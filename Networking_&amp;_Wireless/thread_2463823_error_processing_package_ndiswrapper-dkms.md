---
title: "error processing package ndiswrapper-dkms"
date: 2021-06-18
forum: Networking &amp; Wireless
---

### Post by kennedya27 on 2021-06-18
I seem to be stuck on an issue with ndiswrapper. I can't seem to install ***any*** packages, I always end up getting the following error (error replicated below with "sudo dpkg --configure -a"). I believe completely uninstalling ndiswrapper is a viable option, but I can't seem to do that successfully either, it doesn't even appear to be a recognized command. Any guidance on what to do next would be greatly appreciated, all other posts I've looked at haven't led my anywhere yet. I am rather new to Linux so if I am missing something obvious, please let me know and thank you in advance. 

Post below:

user@user:~$ sudo dpkg --configure -a
Setting up ndiswrapper-dkms (1.60-6ubuntu0.2) ...
Removing old ndiswrapper-1.60 DKMS files...

------------------------------
Deleting module version: 1.60
completely from the DKMS tree.
------------------------------
Done.
Loading new ndiswrapper-1.60 DKMS files...
It is likely that 4.9.140-tegra belongs to a chroot's host
Building for 4.15.0-122-generic and 4.9.140-tegra
Building initial module for 4.15.0-122-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/ndiswrapper-dkms.0.crash'
Error! Bad return status for module build on kernel: 4.15.0-122-generic (aarch64)
Consult /var/lib/dkms/ndiswrapper/1.60/build/make.log for more information.
dpkg: error processing package ndiswrapper-dkms (--configure):
 installed ndiswrapper-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 ndiswrapper-dkms
user@user:~$ ndiswrapper -l
bash: ndiswrapper: command not found

---

### Post by coffeecat on 2021-06-19
I've moved your thread from the Installation & Upgrades sub-forum, whose strapline reads, "For questions about upgrading and installation of your new Ubuntu OS," (operating system, **not** packages) to the Networking & Wireless sub-forum since you seemingly have a wireless problem that you are trying to fix by installing ndiswrapper.

Ndiswrapper is obsolete and almost certainly a lost cause. One of our members, chili55, who is very knowledgeable about wireless problems, said this [in a recent thread]("https://ubuntuforums.org/showthread.php?t=2458385&p=14022611&viewfull=1#post14022611"):

> **chili555 said:**
> I have not seen a single case of ndiswrapper working correctly either here or at askubuntu in many years.

I suggest you take a step back from ndiswrapper, describe whatever wireless problem it is that you are experiencing, and post the output from the wireless info script that is described in the sticky here: [https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108) . Hopefully someone will be able to come up with a better solution for you.

---

### Post by QIII on 2021-06-19
It also looks like you are on an ARM device.  It would be helpful if you would tell us what it is.

---

### Post by chili555 on 2021-06-19
Subscribed and watching.

---

