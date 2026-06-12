---
title: "IBM Thinkpad wireless no longer working"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by cmulcahy on 2007-02-26
Greetings, all!

I have an IBM Thinkpad A30 running Ubuntu 6.10, though my primary desktop is KDE using Kubuntu-desktop.

I had my wireless set up and working perfectly.  It recognized my home network with WPA, could use other networks as well.  Now, however, it no longer works.

When I go into Networking in Settings, it shows WLAN0 as a wired connection.  It used to properly show it as wireless (hence the WLAN0).  

I'm not sure how to get this back to functioning.  I am uncertain what changed to cause the issue.  I have not messed with my networking settings since getting it up and running.  No need to.  I guess it stopped working about 2 to 3 weeks ago, probably after an update.  

Any advice is greatly appreciated!

Thanks
Chris

---

### Post by Spr0k3t on 2007-02-26
give me the output of "uname -r" when you have the chance.  I'm wondering if you just need to go through the synaptic package manager and include the common-modules for the kernel of the same revision.

---

### Post by cmulcahy on 2007-02-26
2.6.17-11-generic

And just to be thorough:
chris@chris-laptop:~$ ls -l /usr/src
total 16
drwxr-xr-x 19 root root 4096 2006-12-14 08:08 linux-headers-2.6.17-10
drwxr-xr-x  4 root root 4096 2006-12-14 08:08 linux-headers-2.6.17-10-generic
drwxr-xr-x 19 root root 4096 2007-02-11 12:18 linux-headers-2.6.17-11
drwxr-xr-x  4 root root 4096 2007-02-11 12:18 linux-headers-2.6.17-11-generic
chris@chris-laptop:~$


I'll go try the 2.6.17-10-generic kernel to see if it works.

---

### Post by cmulcahy on 2007-02-26
Yep, that seemed to do it.  Now, I have to troll through the modules to see which one is missing in the later kernel version.

I have about 80 modules listed by lsmod.  Anyone have an idea which one is missing from the later kernel for wireless on an IBM Thinkpad A30?

By the way, thanks Spr0k3t for the pointer!

---

