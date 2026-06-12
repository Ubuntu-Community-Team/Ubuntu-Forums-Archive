---
title: "Intel Pro Wireless 2200BG detected but cannot connect"
date: 2007-06-02
forum: Networking &amp; Wireless
---

### Post by noneofthem on 2007-06-02
Hello there!

Before I start...
I did check various howtos and threads on this forum and also on various other sites. Still I couldn´t come up with a solution. Any help would be greatly appreciated...

I have got an Intel Pro Wireless 2200GB NIC built in to my laptop. Feisty does detect it and I can see lots of networks in network manager (mine included). However when I try to connect to any of them it takes a while and then either nothing happens or I get a message saying I am connected. When I then try to open a website I don´t get a connection though.

I have tried WEP and WPA-PSK so far and nothing seems to work.

Is there anything you can suggest?

Thanks very much!

none of them

---

### Post by Bredymer on 2007-06-02
Did you upgrade to newest kernel? I've been having the same problem ever since I upgrade to kernel version 2.6.20-16

Running on the old kernel (2.6.20-15) with the "hibernate" module installed, my Sony Vaio VGN-S90S 1.8gHz centrino would hibernate, and connect to WiFi without problems. After the kernel upgrade (I removed the hibernate module after the upgrade, since it seemingly doesn't work with the new kernel) I have no working WiFi and after hibernating I have no network at all.

Does anybody have a solution, or does anybody know if it's safe to remove linux-image-20.6.20-16-generic from adept and thus revert to the last kernel?

---

### Post by noneofthem on 2007-06-04
My system is updated to the most recent kernel and all updates are installed as well. I have had this problem since the beginning. My wifi was working under Windows XP though so it cannot be hardware.

Anyone there who can help?

Thanks

none of them

---

### Post by howardf42 on 2007-06-06
I, too have had post-upgrade problems, but I don't think it's related to the kernel.  I have both the 16 and 15 kernels installed and the same problem with a non-functioning wireless exists with either kernel running.  The problems started after the new kernel and about 80 other updates were installed about a week ago.  From the rather sparse response to this and a few other threads, this doesn't seem to be a universal problem.  Only the lucky few like us, I'm afraid.

HELP!!!

---

### Post by Dasugo on 2007-06-06
Looks like I am in the same boat. my network was working but stopped all of a sudden. Me thinks it was the last few updates I allowed to run. 

I just started using Linux and I dunno  where to go....or do.

---

### Post by honkyusa on 2007-06-11
I'm having the same problems connecting to wireless networks.  I can see all of the SSIDs but when I attempt to connect it usually craps out(timesout).  My 2200bg card was also a little sketchy acting in XPSP2  until I upgraded to 11.1.1.11/9.0.4.36	5/25/07 and my card worked *MUCH* better.  So...   I figure the latest driver for XP worked so damn good I'm going to use [ndiswrapper ]("http://ndiswrapper.sourceforge.net") to use that XP driver in linux.  If it works out good, I'll post how I did it.   It's either that or I might yank the physical card out of my lappy and put in a better quality Atheros based card ;)

-honkyusa

---

### Post by CycleGeek on 2007-06-15
I'm seeing the exact same problem here - but I'm not sure of how to implement ndiswrapper with my WPA network.  Can google it but I'm betting on the next kernel update fixing this problem - am I being too optimistic?  And is it possible to rollback the upgrade?

---

