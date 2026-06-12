---
title: "Random boot error: &quot;Gave up waiting for root device&quot;"
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Purkinje on 2009-08-12
I just installed Ubuntu 9.04 yesterday.  It booted fine the first time I powered on.  After a few reboots, I have noticed that I am getting a completely random error that temporarily halts the boot process; sometimes I get the error, and other times it boots just fine (from the Ubuntu splash screen, without dropping to shell).  

I've seen other threads on this, and I've (to the best of my knowledge) tried all the solutions to no avail.  Here's the error message:

```
Boot from (hd0, 4) ext3 682bc0ce-b500-488e-b36e-4bc7ad043776
Starting up...
Loading, please wait...
Gave up waiting for root device.  Common problems:
 -Boot args (cat /proc/cmdline)
   -Check root delay = (did the system wait long enough?)
   -Check root=(did the system wait for the right device?)
 -Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/682bc0ce-b500-488e-b36e-4bc7ad043776 does not exist. Dropping to shell!

Busybox v1.10.2 (Ubuntu 1:1.10.2-2ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands.
```

I have tried the following solutions:
1. I ran the command:
```
sudo vi /etc/fstab
```
and compared the UUID stated there with the UUID in the /boot/grub/menu.lst file.  They were both the same, so I kept it that way. This was suggested in another thread.

2. I added a 'rootdelay=10' to my menu.lst file in the following way:
```
title		Ubuntu 9.04, kernel 2.6.28-14-generic
uuid		682bc0ce-b500-488e-b36e-4bc7ad043776
kernel		/boot/vmlinuz-2.6.28-14-generic root=UUID=682bc0ce-b500-488e-b36e-4bc7ad043776 ro quiet splash **rootdelay=10**
initrd		/boot/initrd.img-2.6.28-14-generic
quiet
```

This didn't work.  I then tried making the rootdelay a larger number, like 20.  Still didn't fix it.


My method for getting past this error message is simply by typing 'exit' after waiting a few seconds.  This will almost always work as a solution, but I'd like to get this fixed so I don't have to do that.

Any and all help will be greatly appreciated!

Thanks,
Purkinje

---

### Post by LarsW_Tierp on 2009-08-12
Maybe you need a new harddrive. I'll only seen this when drives have been broken.

---

### Post by Purkinje on 2009-08-12
> **LarsW_Tierp said:**
> Maybe you need a new harddrive. I'll only seen this when drives have been broken.

Oh, I hope not. It might be starting to break, but once I boot into Ubuntu, everything runs smoothly.

---

### Post by zfranciscus on 2009-11-01
Hi,

I encountered the same issue. A work around to solve this problem is to modify the menu.lst to use the absolute path to my Ubuntu drive instead of the UUID. I summarises the steps that I do to solve this problem in my blog and ubuntu community documentation:

1. My Blog - [Upgrading to Karmic Koala]("http://zfranciscus.wordpress.com/2009/11/01/ubuntu-karmic-upgrade-series-1-upgrading-jaunty-to-karmic-koala/")
[2. Ubuntu Community Documentation]("https://help.ubuntu.com/community/KarmicUpgrades#Troubleshooting")

---

