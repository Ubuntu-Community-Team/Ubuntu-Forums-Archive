---
title: "edgy fails to recognize nvidia 430 network"
date: 2007-01-03
forum: Networking &amp; Wireless
---

### Post by betchern0t on 2007-01-03
I have a ga-m61pm-s2 motherboard with the nvidia 430 chipset that implements a gigabit nic with the rtl8211 PHY chip. The driver should be forcedeth however it fails to see the card. I have attempted to use the driver package from the nvidia website however it fails with a number of syntax errors. My guess is that it is incompatible with the 2.6.17-10 headers used by Edgy. The stuff I am seeing on the internet suggests that it is for 2.6.16 or before. (*,) 

I have no nic that I can put in this box. I have some rtl8193 cards that fail to talk once they are online. Last time I looked at this problem it was another kernel issue with packet recieved interrupts not getting to where they should be. 

There is a suggestion on the internet that support for 430 nic comes in 2.6.18. Can anyone confirm this? I have spent most of a day troubleshooting this and copying packages to get the nvidia package to try to compile. Before doing the same to build a new kernel from the vanilla sources it would be nice to know if a later kernel/version of forcedeth will solve the problem.

Is there a better way to get this chipset going?

Many thanks in advance

Cheers Paul

---

### Post by betchern0t on 2007-01-04
Support was added for the 430 chipset to the 2.6.18 kernel. Current stable kernel is 2.6.19.1 which I am now running on this box. Instructions are here: 

[http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158)

Thankfully I had another pc running edgy and compiled it there. I am still puzzled though as to why a config based on the edgy generic config file fails to build in sata support resulting the infamous "waiting for root file system" message. Took me three goes to get a running kernel which is a record for me. 

For the record the patch that fixed this simply added the ids for the 430 chipset ethernet support to the forcedeth driver. My guess is that the kernel scans the various busses and matches drivers to the device based on ids. This was why  in this case you don't see any ethx created for the card - the kernel doesn't have a clue what it is.

Cheers Paul

---

