---
title: "/proc/acpi/event Not found"
date: 2009-07-03
forum: New to Ubuntu
---

### Post by Falcon9x5 on 2009-07-03
Reposting this, as it seems to be a separate issue to my ubuntu-desktop problems.

Whenever I try installing acpid (as a dependancy of ubuntu-desktop), it can't start, for some reason (no such file at /proc/acpi/event?):

```
root@dead:~# apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up acpid (1.0.6-9ubuntu4.9.04.3) ...
 * Stopping Hardware abstraction layer hald
   ...done.
 * Starting ACPI services...
acpid: can't open /proc/acpi/event: No such file or directory
invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
```

I've tried various things, like manually stopping the ACPI service, with no luck.
The four packages still to install are:

```
acpid
 acpi-support
 kubuntu-desktop
 ubuntu-desktop
```

Which obviously have a hierarchy of dependancies.

My /proc/acpi directory seems pretty empty too:

```
root@dead:~# ls /proc/acpi/
embedded_controller  power_resource  processor  thermal_zone
```

---

### Post by panaeolus on 2009-12-29
try that ,im facing same problem

sudo aptitude purge acpid  ,mannage to get rid of acpid with that

probably then acpid install ok after

---

