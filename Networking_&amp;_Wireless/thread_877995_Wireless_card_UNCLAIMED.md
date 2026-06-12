---
title: "Wireless card UNCLAIMED"
date: 2008-08-02
forum: Networking &amp; Wireless
---

### Post by littlestar19 on 2008-08-02
I'm a newbie to Ubuntu, I only installed it today (dual boot with Vista). 

I have a wireless card that after a bit of messing around with I got to work and access the web.  Then I installed system updates and rebooted with no wireless. 

running lshw returns 

*-network UNCLAIMED
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: latency=0

What does it mean by UNCLAIMED, and how do I fix this?  The driver is installed, I have ndiswrapper and wpasupplicant. 

Thanks!

---

### Post by jmmorrow on 2008-08-02
Hi, sorry to see no answers to your problem yet.  Like you I was happily running a wireless card until I installed some updates today.  Now my system shows no wireless extensions and "network: 1 UNCLAIMED"
I have looked at a large number of posts but none seem to adress this problem.  So I hope someone picks it up and offers some help soon.

---

### Post by raja_genius on 2008-10-23
I am facing the exact same problem, moreover my usb ports also seem to get disabled. Has anyone found a solution to this yet?

---

### Post by ravenwyn on 2008-10-24
I too have a "network UNCLAIMED" issue with my wireless.  It was working about 2 weeks ago, but now, the wireless connection does not appear in the Network Settings.

The "network UNCLAIMED" is seen when I run:

sudo lshw -C network

I am on a MacBook (2,1?).

---

### Post by barrel_master on 2008-10-24
It looks like we have the same problem.  It was working fine for me on 7.10 until I updated to 8.04 yesterday.  

[http://ubuntuforums.org/showthread.php?t=957164](http://ubuntuforums.org/showthread.php?t=957164)

When it says it's unclaimed I belive that means the drivers aren't working for some reason.

---

