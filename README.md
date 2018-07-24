# gitlab-codecommit-mirror
Mirror GitLab repository to AWS CodeCommit

- Install and configure gitlab-runner
- Generate ssh key for gitlab-runner and add it to an AWS IAM user with right CodeCommit policy
- Define `SOURCE_REPO` and `CODECOMMIT_REPO_URL` variables into .gitlab-ci.yml and add it to your gitlab repo

## Output
```
Running with gitlab-runner 11.1.0 (081978aa)
  on example-repo c443ee6d
Using Shell executor...
Running on gitlab...
Cloning repository...
Cloning into '/home/gitlab-runner/builds/c443ee6d/0/dev/example-repo'...
Checking out ddaa26ee as master...
Skipping Git submodules setup
$ umask 077
$ export TEMP_DIRECTORY=$(cat /dev/urandom | tr -dc 'a-zA-Z0-9' | fold -w 8 | head -n 1)
$ if [[ -z "$TEMP_DIRECTORY" ]]; then exit 1; fi
$ git clone --mirror $SOURCE_REPO $TEMP_DIRECTORY
Cloning into bare repository 'WQwp5Vkn'...
$ cd $TEMP_DIRECTORY
$ git branch -a
* master
$ git push --mirror $CODECOMMIT_REPO_URL
To ssh://git-codecommit.eu-west-1.amazonaws.com/v1/repos/example-repo
 * [new branch]      master -> master
$ cd ..
$ rm -rf $TEMP_DIRECTORY
Job succeeded
```
