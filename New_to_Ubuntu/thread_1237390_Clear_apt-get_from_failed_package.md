---
title: "Clear apt-get from failed package"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by kradalby on 2009-08-11
Hi

I have tried to install a custom netatalk package on my server. But when i tried to install it, it failed and now i cant get it out from apt-get. 
Whatever apt-get i use it still tryes to install and then it fail so i cant update, remove install this package or any other.

When i try to remove the error:
```
root@server2:~# apt-get remove netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcups2-dev libtasn1-3-dev debhelper libgpg-error-dev libgcrypt11-dev quilt d-shlibs po-debconf dh-buildinfo libavahi-client-dev
  cdbs libmail-sendmail-perl intltool libtool fdupes libgnutls-dev libdbus-1-dev libltdl7-dev libwrap0-dev html2text libpam0g-dev
  libavahi-common-dev libcupsys2-dev libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  netatalk
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 2064kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 102190 files and directories currently installed.)
Removing netatalk ...
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "stop" failed.
dpkg: error processing netatalk (--remove):
 subprocess pre-removal script returned error exit status 1
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netatalk
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


When i try to use for example autoremove:
```
Processing triggers for man-db ...
Setting up netatalk (2.0.3-11ubuntu1) ...
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error processing netatalk (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netatalk
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How can i get the package out of the system! 

Please help me:)

My server is running ubuntu server 8.10!

- Kradalby

---

### Post by XubuRoxMySox on 2009-08-11
**Computer Janitor** does it for me. It's a sweet new feature!

-Robin

---

### Post by colau on 2009-08-11
> **kradalby said:**
> Hi

I have tried to install a custom netatalk package on my server. But when i tried to install it, it failed and now i cant get it out from apt-get. 
Whatever apt-get i use it still tryes to install and then it fail so i cant update, remove install this package or any other.

When i try to remove the error:
```
root@server2:~# apt-get remove netatalk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libcups2-dev libtasn1-3-dev debhelper libgpg-error-dev libgcrypt11-dev quilt d-shlibs po-debconf dh-buildinfo libavahi-client-dev
  cdbs libmail-sendmail-perl intltool libtool fdupes libgnutls-dev libdbus-1-dev libltdl7-dev libwrap0-dev html2text libpam0g-dev
  libavahi-common-dev libcupsys2-dev libsys-hostname-long-perl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  netatalk
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 2064kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 102190 files and directories currently installed.)
Removing netatalk ...
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "stop" failed.
dpkg: error processing netatalk (--remove):
 subprocess pre-removal script returned error exit status 1
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netatalk
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


When i try to use for example autoremove:
```
Processing triggers for man-db ...
Setting up netatalk (2.0.3-11ubuntu1) ...
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error processing netatalk (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netatalk
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

How can i get the package out of the system! 

Please help me:)

My server is running ubuntu server 8.10!

- Kradalby

Hi,
Does this help?
[http://ubuntuforums.org/showthread.php?t=410274](http://ubuntuforums.org/showthread.php?t=410274)

---

### Post by Buuntu on 2009-08-11
If you haven't fixed it yet, try using Synaptic Package Manager.  Not sure if that will be any different, but it's worth a try.

---

### Post by mapes12 on 2009-08-11
```
sudo apt-get --purge remove netatalk
```

---

### Post by kradalby on 2009-08-11
I tried the remove with the purge functions, still nothing

```
root@server2:~# sudo apt-get --purge remove netatalk
sudo: unable to resolve host server2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  netatalk*
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 2064kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 101145 files and directories currently installed.)
Removing netatalk ...
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "stop" failed.
dpkg: error processing netatalk (--purge):
 subprocess pre-removal script returned error exit status 1
hostname: Unknown host
invoke-rc.d: initscript netatalk, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 netatalk
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@server2:~#
``` 

The problem with synaptic and computer janitor is that is a server, and i dont have nor wont a desktop window manager...

Other suggestions?

And the link to the netatalk guide is the one i wanted to try when i got the package away...

---

### Post by kradalby on 2009-08-11
I figured it out...

I whent into all the dir i could think of and deleted all netatalk files, and now its removed and the one that works is installed.


Thank for help!

---

