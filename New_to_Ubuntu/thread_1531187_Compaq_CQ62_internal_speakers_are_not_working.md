---
title: "Compaq CQ62 internal speakers are not working"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by stroyeror on 2010-07-14
Sound does not work from the internal speakers with my Cq62 laptop using Ubuntu 10.04.  but when i run this command and reboot ```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```the speakers work i was wondering if someone could explain why its works with and what  this command is exactly doing.

thanks

---

### Post by cariboo on 2010-07-15
Do you have the output of System->Preferences->Sound set to internal speakers?

---

### Post by sushilksk on 2010-07-25
yeah this command works, this updates alsa drivers to newer versions

---

### Post by ambarox on 2010-08-03
**[SIZE=3]linux-backports-modules-alsa-lucid-generic[/SIZE]**

This empty package allows people to keep their alsa-driver snapshot up-to-date when upgrading their Linux kernel.

---

### Post by nanonils on 2010-08-05
> **stroyeror said:**
> Sound does not work from the internal speakers with my Cq62 laptop using Ubuntu 10.04.  but when i run this command and reboot ```
sudo apt-get install linux-backports-modules-alsa-lucid-generic
```the speakers work i was wondering if someone could explain why its works with and what  this command is exactly doing.

thanks

Very nice! Fixed my identical sound problem. 
You do not have any issues with WiFi or brightness?

Thanks!

---

### Post by stroyeror on 2011-01-29
when i run the above command it the the following

```
paul@Laptop-CQ62-01:~$ sudo apt-get install linux-backports-modules-alsa-lucid-generic
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-backports-modules-alsa-lucid-generic: Depends: linux-backports-modules-alsa-2.6.32-28-generic but it is not installable
E: Broken packages

```

---

