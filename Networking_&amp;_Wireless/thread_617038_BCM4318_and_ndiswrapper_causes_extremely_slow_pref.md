---
title: "BCM4318 and ndiswrapper causes extremely slow preformance"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by merinith on 2007-11-18
I have a rather odd problem with my wireless card (a dreaded Broadcom chipset BCM4318) and ndiswrapper on my Gateway MX6455 laptop.  I followed this guide ([http://ubuntuforums.org/showthread.php?t=190177](http://ubuntuforums.org/showthread.php?t=190177)) to install ndiswrapper and get my wireless card working.  It seemed to work fine and I was able to connect to my wireless network without a problem.  On reboot, however, once ndiswrapper loads my laptop goes VERY slow (i.e. takes >20 minutes to boot).

If iIdisable the wireless card using the function keys, everything speeds back up to normal speed.  Once the laptop is booted, if I turn the card back on the fan starts going like crazy and once again everything grinds to a halt.

I have also tried removing ndiswrapper from /etc/modules and loading it after boot with modprobe.  In this case it boots fine but when i try to load ndiswrapper i get the same problem.  If i completely remove ndiswrapper and reinstall it, however, everything works fine again until I reboot.

Anyone have any ideas of how to fix this problem?  Has anyone else had similar problem?

---

### Post by fruehbeck on 2007-11-30
I have the same problem on openSuSE 10.3
    Linux linux 2.6.22.12-0.1-default #1 SMP 2007/11/06 23:05:18 UTC i686 
AFTER upgrading from 10.2
The previous version (I expect it to be a kernel module problem) did not show this misbehaviour.

---

### Post by sudo_t43p on 2007-11-30
Hi,

I thought I was the only one having this problem!

My problem is though a bit more odd. I have a A8N-SLI premium mobo with 512mb 400mhz ram. Yesterday I decided to upgrade my memory to 2gig (Kingston 400mhz ECC memory x 2) and after that my Ubuntu 7.10 wouldn´t boot anymore (recovery didn´t work eighter). I noticed that when Linux tried to load ndiswrapper everything slowed down (took like 5min to mount swap etc).

I decided to install a fresh Ubuntu 7.10 on a clean raptor drive with my new memory installed (I somehow thought at this point it had to do with the memory and swap). Everything worked fine untill I modprobe ndiswrapper -> system forze and I had to hard reset my computer. The same problem occoured at boot, everything superslow after loading ndiswrapper!

Now to the strange part! I removed 1 x Kingston ECC memory from my computer and booted my system. Everythign worked as it should. Re-installing the other memory and I had got the same problem. Well, I removed 1 x 1gb again and booted the system. Once up and running I uninstalled ndiswrapper, and reinstalled my second 1 x 1gb memory. Everything works fine.

Memtest gives no errors and the memory is compatible with my motherboard (at least Kingston's search engine says so..).

I'm so to say clueless.. If there is anyone who is intrested in this problem I'll post my complete hardware setup.

BR,
Chrisse

---

### Post by fruehbeck on 2007-11-30
Hi,
I solved my problem by downloading to ndiswrapper 1.48 and building it for my kernel (see above).
Now everything's fine. WLAN up and running at normal performance.

Hope, that helps,
Thomas

---

### Post by sudo_t43p on 2007-11-30
Ok, thx!

I'll try with the restricted drivers when I get home from work. I cannot though understand why it was working with 1gb of memory but not with 2 x 1gb..?

---

### Post by merinith on 2007-12-01
Sorry for not posting an update, but I was able to solve the problem (upon suggestion of a friend) by adding irqpoll and noirqdebug to my boot string in grub.  Not really sure why this works (anyone know), but my wireless card works without problems now!

---

### Post by SyncMaster on 2008-01-13
> **sudo_t43p said:**
> Ok, thx!

I'll try with the restricted drivers when I get home from work. I cannot though understand why it was working with 1gb of memory but not with 2 x 1gb..?

Hi sudo_t43p!
Did it help? My laptop runs dead slow after memory upgrade, but only Ubuntu, not XP. While the first memory stick (from Kingston) was somehow defective, I got two other, but all show the same effect: Graphics is dead slow, booting takes three times longer with an immense wait after saying "waiting for rootfilesystem" or something. 
I imagine that it could be something with the shared memory of the graphics card and the main memory, and something that XP is doing better... 
But I dont know where to start troubleshooting.

Thanks for a feedback
Rainer

---

