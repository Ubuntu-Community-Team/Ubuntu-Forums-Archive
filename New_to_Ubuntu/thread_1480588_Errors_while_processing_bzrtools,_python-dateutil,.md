---
title: "Errors while processing bzrtools, python-dateutil, python-gnomedesktop, etc."
date: 2010-05-11
forum: New to Ubuntu
---

### Post by ndstate on 2010-05-11
Hello,

I would appreciate any help with this.

When installing a package I get the following errors:

```
Errors were encountered while processing:
 bzrtools
 python-dateutil
 python-gnomedesktop
 python-gweather
 python-paramiko
 python-vobject
E: Sub-process /usr/bin/dpkg returned an error code 

```

When running a system update, I get the following errors:

```
E: python-dateutil: subprocess installed post-installation script returned error exit status 2
E: python-gnomedesktop: subprocess installed post-installation script returned error exit status 2
E: python-gweather: subprocess installed post-installation script returned error exit status 2
E: python-paramiko: subprocess installed post-installation script returned error exit status 2
E: python-vobject: dependency problems - leaving unconfigured
E: bzrtools: subprocess installed post-installation script returned error exit status 2
```

Thanks for your help!

---

### Post by ndstate on 2010-05-12
On apt-get dist-upgrade I get:

```
Setting up bzrtools (2.1.0-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing bzrtools (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up libmysqlclient16 (5.1.41-3ubuntu12) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmysqlclient16 (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of libdbd-mysql-perl:
libdbd-mysql-perl depends on libmysqlclient16 (>= 5.1.21-1); however:
Package libmysqlclient16 is not configured yet.

dpkg: error processing libdbd-mysql-perl (--configure):
dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mysql-client-core-5.1:
mysql-client-core-5.1 depends on libmysqlclient16 (>= 5.1.41-3ubuntu12); however:
Package libmysqlclient16 is not configured yet.

dpkg: error processing mysql-client-core-5.1 (--configure):
dependency problems - leaving unconfigured
Setting up python-dateutil (1.4.1-3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error

dpkg: error processing python-dateutil (--configure):
subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
Setting up python-gnomedesktop (2.30.0-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error

dpkg: error processing python-gnomedesktop (--configure):
subprocess installed post-installation script returned error exit status 2
Setting up python-gweather (2.30.0-0ubuntu1) ...
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error

dpkg: error processing python-gweather (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-mysqldb:
python-mysqldb depends on libmysqlclient16 (>= 5.1.21-1); however:
Package libmysqlclient16 is not configured yet.

dpkg: error processing python-mysqldb (--configure): dependency problems - leaving unconfigured
Setting up python-paramiko (1.7.6-2) ...
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
dpkg (subprocess): unable to execute installed post-installation script: Exec format error

dpkg: error processing python-paramiko (--configure):
subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python-vobject:
python-vobject depends on python-dateutil (>= 1.1); however:
Package python-dateutil is not configured yet.

dpkg: error processing python-vobject (--configure):
dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already

Errors were encountered while processing:
bzrtools
libmysqlclient16
libdbd-mysql-perl
mysql-client-core-5.1
python-dateutil
python-gnomedesktop
python-gweather
python-mysqldb
python-paramiko
python-vobject
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Looks like I need to configure libmysqlclient16 ???  How do I go about doing this?  Thanks

---

### Post by ndstate on 2010-05-18
sudo apt-get autoremove -f results in:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bzr bzrtools python-dateutil python-gnomedesktop python-gweather python-paramiko python-vobject
0 upgraded, 0 newly installed, 7 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 24.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 178711 files and directories currently installed.)
Removing bzrtools ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing bzrtools (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Removing python-vobject ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing python-vobject (--remove):
 subprocess installed pre-removal script returned error exit status 2
Removing python-dateutil ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing python-dateutil (--remove):
 subprocess installed pre-removal script returned error exit status 2
Removing python-gnomedesktop ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing python-gnomedesktop (--remove):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Removing python-gweather ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing python-gweather (--remove):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Removing python-paramiko ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing python-paramiko (--remove):
 subprocess installed pre-removal script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Removing bzr ...
Processing triggers for man-db ...
Errors were encountered while processing:
 bzrtools
 python-vobject
 python-dateutil
 python-gnomedesktop
 python-gweather
 python-paramiko
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
```

---

### Post by ndstate on 2010-05-18
sudo dpkg --purge bzr :

```
(Reading database ... 177870 files and directories currently installed.)
Removing bzr ...
Purging configuration files for bzr ...
dpkg: warning: while removing bzr, directory '/usr/lib/python2.6/dist-packages/bzrlib' not empty so not removed.
```


sudo dpkg -r bzrtools:

```
(Reading database ... 177867 files and directories currently installed.)
Removing bzrtools ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing bzrtools (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bzrtools
```

error exit status 2????
exec format error???

How come nothing works right?

---

### Post by ndstate on 2010-05-18
sudo dpkg --remove --force-remove-reinstreq bzrtools results in:

```
Removing bzrtools ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing bzrtools (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bzrtools
```

---

### Post by ndstate on 2010-05-18
I was finally able to get this solved!!!!!!!!!!!!!!!!!!!!!!!!!!

\\:D/

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/512096)

Workaround A: Remove the package and reinstall

sudo rm /var/lib/dpkg/info/PACKAGE_VERSION.p*
sudo apt-get remove --purge PACKAGE
sudo apt-get clean
sudo apt-get update

---

