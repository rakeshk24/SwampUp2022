# SUP016-Automate everything with the JFrog CLI

### Agenda
- Lab 0 - Configure JFrog CLI
- LAB 1 - Repository Provisioning
- LAB 2 - Role-Based Access Control
- LAB 3 - Build Integration and Properties
  - `jf ci-setup` auto generate `yml` or `jenkins` file with CLI Steps
- LAB 4 - Configure Replication
- LAB 5 - Artifactory Query Language
  - Search, Upload, Download, Cleanup, etc
- LAB 6 - Xray
- LAB 7 - Distribution
- LAB 8 - JFROG CLI Plugin


### Prerequisites

- Generate a Github personnal [access token](https://docs.github.com/en/github/authenticating-to-github/keeping-your-account-and-data-secure/creating-a-personal-access-token). <br/>
  - **NOTE**: if you already have GitHub access token then skip this step else create GitHub account first and then follow above steps.
- Confirm `git` [client](https://git-scm.com/book/en/v2/Getting-Started-First-Time-Git-Setup) has been configured with your user
  - verify with ``git config --list``
- Fork [jfrog/SwampUp2022](https://github.com/jfrog/SwampUp2022) github repository.
  - Reference document to [fork repository](https://docs.github.com/en/get-started/quickstart/fork-a-repo#forking-a-repository).
- `git clone` the forked repo on your workstation
  - Reference document to [clone repository](https://docs.github.com/en/get-started/quickstart/fork-a-repo#cloning-your-forked-repository).
- All content related today's training is under "**SUP016-Automate everything with the JFrog CLI/**".


<br/>

## .env config [Must]
- Our directory `SwampUp2022/SUP016-Automate_everything_with_the_JFrog_CLI` has `.env` file where we need define environment variables.
  - Mandatory - JFROG_EDGE, ADMIN_USER, ADMIN_PASSWORD, JFROG_PLATFORM
  - Optional - ACCESS_TOKEN

<br/>

## Run Labs
### Option 1
- We will be using IDE (any with terminal) or terminal/CMD as part of our labs so please download and install one if you do not have one on your workstation.
- Download [JFrog CLI](https://jfrog.com/getcli/) based on our machine.
- Setup MAVEN or NPM and Docker Client. 
  - so we can run commands like `mvn install`, `npm install` or `docker pull image:tag`

### Option 2
**Using Docker image** :
- Please `cd SwampUp2022` folder and run the following docker command:
```
source SUP016-Automate_everything_with_the_JFrog_CLI/.env

docker run --rm --name my-project -it -v /var/run/docker.sock:/var/run/docker.sock  --env  JFROG_PLATFORM="${JFROG_PLATFORM}" --env ADMIN_USER="${ADMIN_USER}" --env ADMIN_PASSWORD="${ADMIN_PASSWORD}" --env JFROG_EDGE="${JFROG_EDGE}" --env JFROG_CLI_LOG_LEVEL="${JFROG_CLI_LOG_LEVEL}" --env JFROG_CLI_TRANSITIVE_DOWNLOAD_EXPERIMENTAL="${JFROG_CLI_TRANSITIVE_DOWNLOAD_EXPERIMENTAL}" --env JFROG_CLI_TRANSITIVE_DOWNLOAD_EXPERIMENTAL="${JFROG_CLI_TRANSITIVE_DOWNLOAD_EXPERIMENTAL}" -v "$(pwd)":/usr/src/mymaven -w /usr/src/mymaven soleng.jfrog.io/swampup2022-docker-local/docker20.10.16-npm18.1-maven3.8.5-jf2.16.4:11-jdk-alpine /bin/bash
```

