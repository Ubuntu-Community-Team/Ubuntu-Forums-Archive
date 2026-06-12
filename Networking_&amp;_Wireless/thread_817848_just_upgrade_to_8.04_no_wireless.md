---
title: "just upgrade to 8.04 no wireless?"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by AznPat on 2008-06-04
hi guys i m new to ubuntu and i just reinstalled my 8.04 i had it before but had some laptop issues so i just reinstalled it,the first time i use it was running fine never had a problem at all,but now i cant get wireless to come up anywhere..can somebody help me i would really appreciate..thanks guys..

---

### Post by EXCiD3 on 2008-06-04
What wireless card do you have?

---

### Post by AznPat on 2008-06-04
how do i check what kind of wireless card i have?i m really new to ubuntu and i dont really know anything about it yet

---

### Post by cudaman73 on 2008-06-04
Need to post the output of lspci from a terminal.

---

### Post by kingair on 2008-06-04
I have the same problem. Rather than starting a new thread..


I am on a sony vaio. My wireless card is a atheros ar242x 802.11 abg.

I can connect just find with a wire, but not at all wirelessly. 


There is no wireless connection showing up at all in network manager.

I am running Ubuntu 8.04



PS, I am a complete ubuntu newbie. I installed this over my vista operating system of my new comp because I hated it so much!


Thanks in advance. Help!

---

### Post by cudaman73 on 2008-06-04
[http://ubuntuforums.org/showthread.php?t=789824&highlight=ar242x](http://ubuntuforums.org/showthread.php?t=789824&highlight=ar242x)

This post apparently works for the ar242x chipset. I don't know that it will for sure, but let me know if you have any more problems.

---

### Post by AznPat on 2008-06-04
> **cudaman73 said:**
> Need to post the output of lspci from a terminal.

here is the result
patrick@patrick-linux:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:04.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by kingair on 2008-06-04
cudaman,

I got to step 2. ha.

It says 

alpha@alpha-laptop:~$ sudo apt-get install build-essential
[sudo] password for alpha: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential
alpha@alpha-laptop:~$

---

### Post by cudaman73 on 2008-06-04
also, lsmod |grep ath_pci

trying to determine if ubuntu has the modules loaded or if it's being detected at all.

---

### Post by cudaman73 on 2008-06-04
> **kingair said:**
> cudaman,

I got to step 2. ha.

that's odd. Make sure you have the proper repositories enabled in synaptic.

---

### Post by kingair on 2008-06-04
> **cudaman73 said:**
> that's odd. Make sure you have the proper repositories enabled in synaptic.

 That sounds like chinese to me.

How do I do that?

---

### Post by AznPat on 2008-06-04
> **cudaman73 said:**
> also, lsmod |grep ath_pci

trying to determine if ubuntu has the modules loaded or if it's being detected at all.

i just did what u ask me to lsmod |grep ath_pci nothing happened

---

### Post by cudaman73 on 2008-06-04
> **kingair said:**
> That sounds like chinese to me.

How do I do that?

augh, it's been ages since i've used ubuntu, and i'm just trying to get back into it.

Unfortunately, I'm in vista, and can't give you direct instructions on how to do it. Either you'll have to wait until I can get back into Ubuntu (I'm at school right now), or perhaps someone else will wander into this thread and be able to help you out further.

I'm sorry :(

---

### Post by kingair on 2008-06-04
I figured it out. Im in synaptic package manager. Everything is clicked on/checked.

---

### Post by cudaman73 on 2008-06-04
> **AznPat said:**
> i just did what u ask me to lsmod |grep ath_pci nothing happened

It seems, then, that ubuntu is not loading drivers for your wireless card.

Is there a message in the system tray about restricted modules? I can't recall at the moment exactly what it looks like (i think it looks like a pci card), but it should tell you something about restricted drivers, and whether or not to enable them) If so, try that first.

If not, this thread looks promising. I don't have time to read all the way through it, but give this thread a look-through and see if that helps you out.

Unfortunately, I have to leave right now, but hopefully that works, but if not, someone else should be able to help you out more.

[http://ubuntuforums.org/showthread.php?t=795984&highlight=modprobe+ath_pci](http://ubuntuforums.org/showthread.php?t=795984&highlight=modprobe+ath_pci)

---

### Post by cudaman73 on 2008-06-04
> **kingair said:**
> I figured it out. Im in synaptic package manager. Everything is clicked on/checked.

Click reload first, then can you find build-essential in synaptic?

---

### Post by kingair on 2008-06-04
reload did it.

ok, working now. standby

(ps. thanks!!!)

---

### Post by kingair on 2008-06-04
ok, the third and forth commands....


alpha@alpha-laptop:~$ tar xfz madwifi-nr-r3366+ar5007.tar.gz
alpha@alpha-laptop:~$ cd madwifi-nr-r3366+ar5007
bash: cd: madwifi-nr-r3366+ar5007: No such file or directory
alpha@alpha-laptop:~$

---

### Post by kingair on 2008-06-04
I followed this...

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)


rebooted, and it still doesnt show any wireless option in the network controller

---

### Post by cudaman73 on 2008-06-04
> **kingair said:**
> I followed this...

[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)


rebooted, and it still doesnt show any wireless option in the network controller

You may want to install WICD, I've heard that it's much better than gnome's network manager.

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

