---
title: "Need to remove BandwidthD - bandwidth monitoring software"
date: 2010-07-30
forum: New to Ubuntu
---

### Post by halovivek on 2010-07-30
Hi
I tried to install bandwidthd monitoring software for ubuntu.
It got failed. i tried following steps to remove. 
Since it is not installed properly in ubuntu, it is not allowing other files to install.
Could you please help me.

Steps which I followed and results as below

**halovivek@halovivek-laptop:~$ sudo apt-get remove bandwidthd**
[sudo] password for halovivek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bandwidthd
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing bandwidthd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)

[B]halovivek@halovivek-laptop:~$ sudo dpkg --configure -a

halovivek@halovivek-laptop:~$ sudo apt-get install bandwidthd
[/B]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  bandwidthd
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/74.8kB of archives.
After this operation, 73.7kB of additional disk space will be used.
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
Selecting previously deselected package bandwidthd.
(Reading database ... 244395 files and directories currently installed.)
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20090917-3_i386.deb) ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by mac9416 on 2010-07-30
Have you tried deleting /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb and trying again? The download may be corrupted.

---

### Post by halovivek on 2010-07-31
Hi I have removed as you said. after that i tried to reinstall and remove it is not working. I even tried in removing from synaptic also.
could you help me more.
thanks

[B]halovivek@halovivek-laptop:~$ sudo apt-get remove bandwidthd
[/B][sudo] password for halovivek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bandwidthd
0 upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? Y
dpkg: error processing bandwidthd (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 bandwidthd
E: Sub-process /usr/bin/dpkg returned an error code (1)


**halovivek@halovivek-laptop:~$ sudo apt-get install bandwidthd**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  bandwidthd
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 74.8kB of archives.
After this operation, 73.7kB of additional disk space will be used.
Get:1 [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe bandwidthd 2.0.1+cvs20090917-3 [74.8kB]
Fetched 74.8kB in 2s (36.1kB/s)                        
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
Selecting previously deselected package bandwidthd.
(Reading database ... 244395 files and directories currently installed.)
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20090917-3_i386.deb) ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
halovivek@halovivek-laptop:~$ sudo apt-get install bandwidthd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  bandwidthd
1 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/74.8kB of archives.
After this operation, 73.7kB of additional disk space will be used.
Preconfiguring packages ...
cp: cannot stat `/usr/share/doc/bandwidthd/bandwidthd.conf': No such file or directory
bandwidthd failed to preconfigure, with exit status 1
Selecting previously deselected package bandwidthd.
(Reading database ... 244395 files and directories currently installed.)
Preparing to replace bandwidthd 2.0.1 (using .../bandwidthd_2.0.1+cvs20090917-3_i386.deb) ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: warning: old pre-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by halovivek on 2010-07-31
I could not able to install other softwares also

i am getting error message 

E:I wasn't able to locate file for the bandwidthd package. This might mean you need to manually fix this package.: dpkg: error processing bandwidthd (--configure):

 Package is in a very bad inconsistent state - you should

 reinstall it before attempting configuration.

---

### Post by Elfy on 2010-07-31
Try 

```
sudo dpkg --remove --force-remove-reinstreq bandwidthd
```

---

### Post by halovivek on 2010-07-31
I tried and got this result.


**halovivek@halovivek-laptop:~$ sudo dpkg --remove --force-remove-reinstreq bandwidthd**
[sudo] password for halovivek: 
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 244929 files and directories currently installed.)
Removing bandwidthd ...
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "stop" failed.
dpkg: error processing bandwidthd (--remove):
 subprocess installed pre-removal script returned error exit status 2
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bandwidthd

---

### Post by mac9416 on 2010-07-31
> E:I wasn't able to locate file for the bandwidthd package. This might mean you need to manually fix this package.: dpkg: error processing bandwidthd (--configure):

I've seen this problem before with flashplugin-installer. That problem was fixed by enabling the Canonical partner repo. Do you know what repo that software came from, and can you (re)enable it?

---

### Post by halovivek on 2010-07-31
i tried to remove from synaptic and i am getting this error message

E: /var/cache/apt/archives/bandwidthd_2.0.1+cvs20090917-3_i386.deb: subprocess new pre-removal script returned error exit status 2

what to do?

---

### Post by halovivek on 2010-07-31
i got one more error while trying to select other bandwithd software
E: bandwidthd: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal.

---

### Post by halovivek on 2010-07-31
i tried to re-install and i got this error

**installArchives() failed**

could not install all dependencies

---

### Post by mac9416 on 2010-07-31
Could you post your /etc/apt/sources.list?

---

### Post by halovivek on 2010-07-31
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ lucid main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid multiverse
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-security multiverse
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) lucid main

---

### Post by mac9416 on 2010-07-31
Looks like we can safely scrap the notion that the correct source is not enable.

When dealing with the similar issue with adobe-flashplugin, this was the solution:

```
$ sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm  # deletes a troublesome config file
$ sudo dpkg-reconfigure adobe-flashplugin --force  # force-reconfigures adobe-flashplugin
$ sudo dpkg --purge --force-all adobe-flashplugin  # force-removes adobe-flashplugin
$ sudo apt-get install flashplugin-nonfree  # installs flashplayer the easy way
```

So, a modified version of that might work for you.

```
$ sudo mv /var/lib/dpkg/info/bandwidthd.prerm ~/bandwidthd.prerm
$ sudo dpkg-reconfigure bandwidthd --force
$ sudo dpkg --purge --force-all bandwidthd
```

---

### Post by halovivek on 2010-07-31
i followed and this is the result.
whether it got fixed?

**halovivek@halovivek-laptop:~$ sudo mv /var/lib/dpkg/info/bandwidthd.prerm ~/bandwidthd.prerm**
[B]
halovivek@halovivek-laptop:~$ sudo dpkg-reconfigure bandwidthd --forc[/B]
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.

**halovivek@halovivek-laptop:~$ sudo dpkg-reconfigure bandwidthd --force**
update-rc.d: warning: /etc/init.d/bandwidthd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
/etc/init.d/bandwidthd: 19: Syntax error: "(" unexpected
invoke-rc.d: initscript bandwidthd, action "start" failed.
**halovivek@halovivek-laptop:~$ sudo dpkg --purge --force-all bandwidthd**
dpkg: warning: overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 244976 files and directories currently installed.)
Removing bandwidthd ...
Purging configuration files for bandwidthd ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...

---

### Post by mac9416 on 2010-07-31
I'm not sure, but it looks hopeful. Try installing something else and see if it works. If it does, you're good to go!

---

### Post by halovivek on 2010-08-01
> **mac9416 said:**
> I'm not sure, but it looks hopeful. Try installing something else and see if it works. If it does, you're good to go!

Thank you all for your support :). Problem got solved. Now i can able to install other files.

**God Bless all.**

---

### Post by ashwindatye on 2011-04-20
"sudo dpkg --purge --force-all bandwidthd" worked for me looks like. thanks a million!!

---

### Post by fmoyota on 2012-02-24
$ sudo dpkg-reconfigure bandwidthd --force
$ sudo dpkg --purge --force-all bandwidthd

was helpful!

---

### Post by wesaus35 on 2012-05-04
A bit of a necro but i just tried to install this software as well and ended up following this thread down to the letter. It worked!! Is there anyway to get the information out about this program causing problems for other Ubuntu users?

---

### Post by iShiva on 2012-10-04
Thanks to all, It was helpful for me too  ;)


:guitar:

---

