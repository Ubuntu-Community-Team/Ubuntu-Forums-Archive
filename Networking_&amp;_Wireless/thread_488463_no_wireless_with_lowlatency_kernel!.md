---
title: "no wireless with lowlatency kernel!"
date: 2007-06-30
forum: Networking &amp; Wireless
---

### Post by Zannax on 2007-06-30
Hi, I've installed the ubuntustudio packages, but after rebooting there was no wlan connection anymore!

I suspected that the new lowlatency kernel was the problem: in fact, if I select the former generic kernel, wireless works fine!

With lowlatency-kernel, network manager doesn't see any network, manual configuration doesn't show the wlan connection at all.

Hardware Information correctly shows my Dlink card ACX 111 chipset, but there's no "wlan interface" under it...

I tried running "depmod", but that doesn't fix it...

What else can I try?
any suggestion is welcome... :-)

---

### Post by Zannax on 2007-06-30
Solved!
**solution:**
I only had to install the **linux-restricted-modules-lowlatency ** package...

Looking at dmesg output I've seen it didn't find the acx111 firmware (my wireless card has acx111 chipset), in fact I had the firmware in:

 /lib/firmware/2.6.20-16-generic/acx

but there was no such folder in:

 /lib/firmware/2.6.20-16-lowlatency

A little search an I found that the relevant firmware modules are provided by the package:
linux-restricted-modules-lowlatency

which was not installed...

---

### Post by mrbugspray on 2007-06-30
Great job. that is a good contribution to the ubuntu studio ppc. ;)

http://ubuntuforums.org/showthread.php?t=447403

---

### Post by Jeff Seager on 2007-09-29
Zannax, I had installed Ubuntu Studio over 7.04 a while back, but had not added the repositories until yesterday. Upgrading last night knocked out my wireless card, as it did yours. Thanks for posting your solution ... you've saved me a lot of work this morning!

---

### Post by telehack on 2007-10-16
Another word of thanks Xannan for posting this. I installed Ununtu Studio over a standard Feisty install and had the same problem with no wireless in lowlatency mode. I booted using the standard kernel, found your post and presto, fixed. Now that I've got everything working I have to decide whether to take the plunge with the realtime kernel.

-Telehack

---

### Post by sebastjanp on 2007-11-22
I belive that the name of the package on my sistem is linux-restricted-modules-rt.
 It definetly works for me :)

Thanks Zannax

---

