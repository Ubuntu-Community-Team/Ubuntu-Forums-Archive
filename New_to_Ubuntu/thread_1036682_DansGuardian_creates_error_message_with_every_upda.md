---
title: "DansGuardian creates error message with every update"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by fr.theo on 2009-01-11
I installed DansGuardian for web content filtering it works well actually too well however it continually cause problems especially when updating the system or installing any application.


I am unable to uninstall DansGuardian due to the same fault here is the fault in which I receive:

E: dansguardian: subprocess pre-removal script returned error exit status 127

not sure what it means however it is a nuisance although I get this message when removing, when I update, the update goes through but I always receive an error.

Any help would be much appreciated

---

### Post by Partyboi2 on 2009-01-11
Can you open a terminal (Applications>Accessories>Terminal) please  and post the output to
```
sudo apt-get remove dansguardian
```

---

### Post by fr.theo on 2009-01-19
Thankyou for your reply here is the error message I receive when attempting to remove Dans Guardian:

```
theodore@Ubuntu-Desktop:~$ sudo apt-get remove dansguardian

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nspluginwrapper
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  dansguardian
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 1565kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 158235 files and directories currently installed.)
Removing dansguardian ...
Stopping DansGuardian: dansguardian.
[COLOR="Magenta"][COLOR="Lime"][COLOR="Lime"]/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "stop" failed.
dpkg: error processing dansguardian (--remove):
 subprocess pre-removal script returned error exit status 127
Starting DansGuardian: dansguardian.
/etc/init.d/dansguardian: 71: /usr/local/apps/parental-control/./dansguardian_log.pl: not found
invoke-rc.d: initscript dansguardian, action "start" failed.
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 dansguardian
E: Sub-process /usr/bin/dpkg returned an error code (1)
theodore@Ubuntu-Desktop:~$ [/COLOR][/COLOR][/COLOR]


```

---

### Post by Partyboi2 on 2009-01-19
Have a try of some of the things suggested in [[COLOR=Blue]this[/COLOR]]("http://www.backports.ubuntuforums.org/showthread.php?t=882866") thread.

---

