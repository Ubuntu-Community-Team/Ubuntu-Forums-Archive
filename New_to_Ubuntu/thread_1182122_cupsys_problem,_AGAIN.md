---
title: "cupsys problem, AGAIN"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by ericeclifford on 2009-06-08
Everytime I do a upgrade or install cupsys fails to upgrade or install and gives me crash reports, I make a live cd customization and every time I upgrade it makes crash reports on my live cd, every time I boot it up.

It must be only the latest version of cupsys, because before it did not do this. 

I tried to reinstall it, and a dpkg --config thing, but it did not work.

Anyone have a fix for this.

---

### Post by mdawg414 on 2009-06-08
Where exactly does it fail to upgrade? What is the change you make on the Live CD to resolve the issue? That will make it easier to figure out what is going wrong.

---

### Post by ericeclifford on 2009-06-08
I get a error when I do the dpkg --config command.
It says: Errors while processing: cupsys

Here is my old thread, its the same thing happening, and the fix that used to work does not anymore.

[http://ubuntuforums.org/showthread.php?t=1148436&highlight=cupsys](http://ubuntuforums.org/showthread.php?t=1148436&highlight=cupsys)

---

### Post by mdawg414 on 2009-06-08
Seems like cupsys may still be looking at the wrong version. Try this:

```

sudo aptitude full-upgrade

```

and see if it upgrades anything. I'm also looking at my system and it appears to have disabled the medibuntu repository on the upgrade to Jaunty. Perhaps you no longer need the cupsys stuff???

---

### Post by ericeclifford on 2009-06-09
This did not work :(

I cant remove it for some reason, it seems to be the version of cupsys that just came out. I am using 8.04, and the live cd Iso image I am using to customize is 8.04.2 as well.

---

### Post by ericeclifford on 2009-06-09
2 hour bump.

---

### Post by ericeclifford on 2009-06-09
BTW I tried to remove cupsys and I get this.

root@eric:~/live# chroot edit apt-get remove --purge cupsys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bluez-cups* cups-pdf* cupsys* cupsys-driver-gutenprint* foomatic-db-hpijs*
  hal-cups-utils* hpijs* hplip* ubuntu-desktop*

---

### Post by ericeclifford on 2009-06-09
root@eric:~/live# chroot edit apt-get remove --purge cupsys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  bluez-cups* cups-pdf* cupsys* cupsys-driver-gutenprint* foomatic-db-hpijs*
  hal-cups-utils* hpijs* hplip* ubuntu-desktop*
0 upgraded, 0 newly installed, 9 to remove and 0 not upgraded.
After this operation, 15.0MB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 98538 files and directories currently installed.)
Removing bluez-cups ...
Removing cups-pdf ...
Purging configuration files for cups-pdf ...
Removing foomatic-db-hpijs ...
Removing hpijs ...
Removing hplip ...
Purging configuration files for hplip ...
Removing ubuntu-desktop ...
Removing cupsys-driver-gutenprint ...
invoke-rc.d: initscript cupsys, action "force-reload" failed.
Purging configuration files for cupsys-driver-gutenprint ...
Removing hal-cups-utils ...
Removing cupsys ...
Ignoring nonregistered document `cupsys'
invoke-rc.d: initscript cupsys, action "stop" failed.
dpkg: error processing cupsys (--purge):
 subprocess pre-removal script returned error exit status 1
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@eric:~/live# chroot edit apt-get remove cupsys
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  cupsys
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 10.1MB disk space will be freed.
Do you want to continue [Y/n]? y
Can not write log, openpty() failed (/dev/pts not mounted?)
(Reading database ... 98381 files and directories currently installed.)
Removing cupsys ...
Ignoring nonregistered document `cupsys'
invoke-rc.d: initscript cupsys, action "stop" failed.
dpkg: error processing cupsys (--remove):
 subprocess pre-removal script returned error exit status 1
invoke-rc.d: initscript cupsys, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 cupsys
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@eric:~/live# 


wont let me remove it :(

---

### Post by ericeclifford on 2009-06-10
still here

---

### Post by ericeclifford on 2009-06-10
I think I got it fixed( kind of) I just deleted the cupsys folder from my repository I mirrored from the ubuntu hardy repositories, and it cant find the upgrade so I am recompiling the iso right now, will post back if it worked, but no broken packages while processing at least or removal script errors.

---

