---
title: "wicd interupts full-upgrade and autoremove"
date: 2018-11-19
forum: Networking &amp; Wireless
---

### Post by Sherman_Willden on 2018-11-19
WICD works well but everytime I try full-upgrade or autoremove I get the following:

Reading package lists...
Building dependency tree...
Reading state information...
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up wicd-daemon (1.7.4+tb2-6) ...
Job for wicd.service failed because the control process exited with error code.
See "systemctl status wicd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript wicd, action "start" failed.
&#9679; wicd.service - Wicd a wireless and wired network manager for Linux
   Loaded: loaded (/lib/systemd/system/wicd.service; disabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Mon 2018-11-19 03:48:59 EST; 11ms ago
     Docs: man:wicd(8)
  Process: 8782 ExecStart=/usr/sbin/wicd --no-daemon --keep-connection (code=exited, status=1/FAILURE)
 Main PID: 8782 (code=exited, status=1/FAILURE)

Nov 19 03:48:59 sql-dev systemd[1]: Starting Wicd a wireless and wired network manager for Linux...
Nov 19 03:48:59 sql-dev wicd[8782]: It seems like the daemon is already running.
Nov 19 03:48:59 sql-dev wicd[8782]: If it is not, please remove /var/run/wicd/wicd.pid and try again. wicd depends on wicd-daemon (= 1.7.4+tb2-6); however:
  Package wicd-daemon is not configured yet.

dpkg: error processing package wicd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wicd-gtk:
 wicd-gtk depends on wicd-daemon (= 1.7.4+tb2-6); however:
  Package wicd-daemon is not configured yet.

dpkg: error processing package wicd-gtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 wicd-daemon
 wicd
 wicd-gtk
Nov 19 03:48:59 sql-dev systemd[1]: wicd.service: Main process exited, code=exited, status=1/FAILURE
Nov 19 03:48:59 sql-dev systemd[1]: wicd.service: Failed with result 'exit-code'.
Nov 19 03:48:59 sql-dev systemd[1]: Failed to start Wicd a wireless and wired network manager for Linux.
dpkg: error processing package wicd-daemon (--configure):
 installed wicd-daemon package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of wicd:

---

### Post by mitesh.agrwl on 2018-11-19
> dpkg: error processing package wicd (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of wicd-gtk:
 wicd-gtk depends on wicd-daemon (= 1.7.4+tb2-6); however:
  Package wicd-daemon is not configured yet.

The problem seems that the wicd-daemon package is not-configured (properly). Use the code 

```
 ~$ sudo dpkg --configure wicd-daemon 
```

check if this solves your problem.

---

