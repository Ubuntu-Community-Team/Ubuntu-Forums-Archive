---
title: "Netgear RangeMax Next (wn311b)"
date: 2006-09-17
forum: Networking &amp; Wireless
---

### Post by mixmaster on 2006-09-17
I was hoping I could get this to work with ndiswrapper.  It is a pci card with a broadcom chip (marked unknown when I tried to find more info).

I extracted the .sys, .inf and a .bin file from the .cabs, as instructed, but when I attempt the ndiswrapper -i the directory it creates contains only the .inf file and a couple of files created by the process - the .sys & bin files are not copied.  ndiswrapper -l then reports "invalid driver".

Any suggestions would be appreciated.  Driverloader fails in a similar way.

I know - my fault for being bleeding edge/pre-standard but the geometry is such that I really need more penetrating power than a standard 802.11b/g setup could give me.

---

### Post by alzamabar on 2007-10-27
Hi, I want to get started with Ubuntu and have already got a WN311B. Have you got the WN311B card working with Ubuntu? 

If so could you post the instructions to get it installed? 

Please be kind (I'm a newbie to Ubuntu and Linux-like OS).

Thanks.

M.

---

### Post by jon_williams on 2007-11-06
I'm also wanting to get two Linux machines linked up using WN311B wireless cards - has anyone worked out how to get them working in 64bit Ubuntu 7.10 ??

[IMG]http://serve.dynasig.net/4087.gif[/IMG]

---

### Post by c1981 on 2008-03-10
Assuming your all running 64-bit versions of Linux --->
The problem is the fact that the Netgear driver-pack can't be extracted (not that i know of anyway) they have to be installed on a windows machine first and then copied to an accessible linux directory. As few people actually run 64-bit versions of windows; the 32-bit drivers are installed by default; which aren't compatible with a 64-bit linux kernel.

Solution: get the wn311b.sys and wn311b.inf file from a windows XP pro 64-bit or vista 64-bit installation; afterwards the ndiswrapper solution should work fine.

---

