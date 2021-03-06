# okd-demo-storage

Demo of various storage backend used into OKD.

Present various use case running an apache web-server using :
- Ephemeral storage backend example
- Volatile storage backend example
- Persistent storage backend example
- Distributed storage backend example

## Install startx-demo script

You must run this demo in a all-in-one installation of openshift (origin or enterprise). You must also have
a nfs external server connected to this node with multiple (at least 3) mountpoints exported and mounted to 
your openshift installation. For more information see [demo requirements](REQUIREMENTS.md).

```bash
## switch to root user
sudo su -
## Download startx-demo script
curl -Ls https://goo.gl/a1UakD > /usr/local/bin/startx-demo
## Allow script execution
chmod ugo+x /usr/local/bin/startx-demo
## Setup demo parameters (if not default)
#startx-demo setup cluster <cluster-api-url>
#startx-demo setup project demo-storage
## Start demo installation
startx-demo install
```

When demo is installed, auto-completion is enabled for `startx-demo` script and help you using this demo
do not hesitate to execute `startx-demo --help` for information on command and sub-commands availables 


## Setup demo environment

When you are ready to start a demo, you can follow this sequence to install mandatory resources

```bash
## Login using a new developer user (interactive). Could be skipped if install was your previous action.
startx-demo login
## setup and create the openshift project to use (interactive)
startx-demo project demo-storage
## Load images streams and templates in the current project
startx-demo load
## List generic ressources in project
startx-demo get
```

After you environment setup, you can run one or all demo type according to your demo scenario


## Excute ephemeral demo

This demo will show how emptydir storage is handled by openshift infrastructure and how data if preserved and released
with as single Pod deployement and no PV storage associated to Pod volume (emptydir).

```bash
## Start the ephemeral demo
startx-demo ephemeral start
## Watch openshift ressources and storage content for the ephemeral demo (dynamic)
startx-demo ephemeral watch
## Show openshift ressources for the ephemeral demo
startx-demo ephemeral ps
## Show storage content for the ephemeral demo
startx-demo ephemeral ls
## Delete openshift ressources and storage content for the ephemeral demo (asynchronous)
startx-demo ephemeral delete


## Excute hostpath demo

This demo will show how hostpath storage is handled by openshift infrastructure and how data if preserved and released
with as single Pod deployement and no PV storage associated to Pod volume (hostpath).

```bash
## Start the hostpath demo
startx-demo hostpath start
## Watch openshift ressources and storage content for the hostpath demo (dynamic)
startx-demo hostpath watch
## Show openshift ressources for the hostpath demo
startx-demo hostpath ps
## Show storage content for the hostpath demo
startx-demo hostpath ls
## Delete openshift ressources and storage content for the hostpath demo (asynchronous)
startx-demo hostpath delete
```

## Excute volatile demo

This demo will show how PV storage is handled by openshift infrastructure and how data if preserved and released
with a single Pod lifecycle using a persistent storage defined as a `Recycle` reclaim policy and a `ReadWriteOnce` 
access mode.

```bash
## Start the volatile demo
startx-demo volatile start
## Watch openshift ressources and storage content for the volatile demo (dynamic)
startx-demo volatile watch
## Show openshift ressources for the volatile demo
startx-demo volatile ps
## Show storage content for the volatile demo
startx-demo volatile ls
## Delete openshift ressources and storage content for the volatile demo (asynchronous)
startx-demo volatile delete
```

## Excute resilient demo

This demo will show how PV storage is handled by openshift infrastructure and how data if preserved and released
with a single Pod lifecycle using a persistent storage defined as a `Retain` reclaim policy and a `ReadWriteOnce` 
access mode.

```bash
## Start the resilient demo
startx-demo resilient start
## Watch openshift ressources and storage content for the resilient demo (dynamic)
startx-demo resilient watch
## Show openshift ressources for the resilient demo
startx-demo resilient ps
## Show storage content for the resilient demo
startx-demo resilient ls
## Delete openshift ressources and storage content for the resilient demo (asynchronous)
startx-demo resilient delete
```

## Excute distributed demo

This demo will show how PV storage is handled by openshift infrastructure and how data if preserved and released
with a multiple Pod lifecycle using a persistent storage defined as a `Retain` reclaim policy and a `ReadWriteMany` 
access mode.

```bash
## Start the distributed demo
startx-demo distributed start
## Watch openshift ressources and storage content for the distributed demo (dynamic)
startx-demo distributed watch
## Show openshift ressources for the distributed demo
startx-demo distributed ps
## Show storage content for the distributed demo
startx-demo distributed ls
## Delete openshift ressources and storage content for the distributed demo (asynchronous)
startx-demo distributed delete
```


## close this demo

```bash
## Remove all resource and project
startx-demo delete
# Remove all resource, project and demo script
#startx-demo delete all
```

