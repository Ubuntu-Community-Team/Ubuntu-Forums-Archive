---
title: "Broadcom Netxtreme driver issues"
date: 2006-12-28
forum: Networking &amp; Wireless
---

### Post by JonnyQuest on 2006-12-28
Greetings,

I have been using Linux for quite a while, but am new to Ubuntu, so bear with me...

 I am trying to install 6.06.1 LTS (Dapper?) on a new server and I am having difficulty getting the on-board NICs to work properly. The motherboard is a Tyan Thunder h2000M (S3992), with two on-board BCM5780 GbE ports and an Intel 10/100 port. The Intel port works fine using the e100 driver. By default, the Gb interfaces load the tg3 driver which seems to link up, but won't pass packets.

I have downloaded, built and installed the bcm5700 driver, but I can't seem to get things to work. I've checked the threads here, but no one seems to have made it go. Per the suggestions here I have blacklisted the tg3 module and it does not load (good). I also tried the following:

- edited /etc/network/interfaces to make one of the 5780s the default
- modprobe the bcm5700 (it loads, but won't pass packets)
- putting the bcm5700 into /etc/modules to force it to load at boot
- added entries to /etc/modprobe.d/aliases to link the bcm5700 to eth1 and eth2

](*,)  None of this has gotten me anywhere. 

:confused: Any suggestions?

---

