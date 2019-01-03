# Pipelines

In this workshop, we'll cover the basics of setting up a simple delivery pipeline, consisting of git hooks and shell commands.

### Before you start

* [Install opunit and node.js](https://github.com/CSC-DevOps/profile#opunit)
* Clone this repo with: `git clone https://github.com/CSC-DevOps/Pipelines`


### What and why pipelines?

A *delivery pipeline* is a workflow system for building, validating, and deploying changes into a production environment. Pipelines are essential for supporting the paradigm of *continuous deployment*. A pipeline consists of stages, which typically represents a software engineering process, such as testing, static analysis, acceptance testing, or code review. When fully automated, pipelines allow commits to source code to be automatically tested and "seamlessly" deployed into production environments within minutes.

While more complex pipelines can be created with tools like Spinnaker and Jenkins, using *simple tools*—such as git and shell commands—can get the job done.

### Checking progress on workshop

To help you identify if issues exist with the current setup, you can run the following command to check:

```bash
$ cd Pipelines
$ opunit verify local
```
## Hooks

Hooks are.

Types of hooks.

order of hooks...

### Practice

Inside a new directory (`mkdir hook-demo`), create a new git repository with `git init`. Create a post-commit file located in "hook-demo/.git/hooks/post-commit". Finally, you should ensure the post-commit script is exectuable, by running `chmod +x post-commit`.

The script for post-commit might look something like this:

```sh
#!/bin/sh

# In Mac
open https://google.com/
# In Windows
# start https://google.com/
# In Linux
# xdg-open https://google.com/
```

Trigger the commit by create a simple commit in hook-demo. (`touch demo`; `git add demo`; `git commit -m "init"`. You should see the webpage open.)


## A Simple Pipeline

```sh
#!/bin/sh

GIT_WORK_TREE=../production-www/ git checkout -f
SHA1=$(git rev-parse HEAD)
MSG=$(git show -s --format=%B $SHA1)
echo "Received push to production: $MSG"
```

### Something with curl...

* Webhooks?