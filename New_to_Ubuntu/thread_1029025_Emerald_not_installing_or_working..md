---
title: "Emerald not installing or working."
date: 2009-01-03
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-01-03
I cant install emerald, and when I do I cant apply a theme.

This is what I get in the terminal:

[HTML]taylor@taylor-laptop:~$ sudo apt-get install emerald
[sudo] password for taylor: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-wlan-ng-doc linux-headers-2.6.27-7-generic
  linux-wlan-ng
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libemeraldengine0
Recommended packages:
  emerald-themes
The following NEW packages will be installed:
  emerald libemeraldengine0
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B/342kB of archives.
After this operation, 1712kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously deselected package libemeraldengine0.
(Reading database ... 124612 files and directories currently installed.)
Unpacking libemeraldengine0 (from .../libemeraldengine0_0.7.2-0ubuntu2_i386.deb) ...
Selecting previously deselected package emerald.
Unpacking emerald (from .../emerald_0.7.2-0ubuntu2_i386.deb) ...
Processing triggers for man-db ...
Setting up system-tools-backends (2.6.0-1ubuntu1.1) ...
 * Starting System Tools Backends system-tools-backends                         invoke-rc.d: initscript system-tools-backends, action "start" failed.
dpkg: error processing system-tools-backends (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libemeraldengine0 (0.7.2-0ubuntu2) ...

Setting up emerald (0.7.2-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 system-tools-backends
E: Sub-process /usr/bin/dpkg returned an error code (1)
taylor@taylor-laptop:~$ 

[/HTML]

---

### Post by cariboo on 2009-01-03
Have a look at this [bug]("http://bugs.launchpad.net/ubuntu/intrepid/+source/system-tools-backends/+bug/294389"), there is a work around posted that solves the sytem-tools-backend no installing problem.

Jim

---

