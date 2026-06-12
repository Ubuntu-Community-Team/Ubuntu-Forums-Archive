---
title: "wireless internet catastrophe!!"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by earthlovin on 2009-08-14
i posted my problem on the wireless and networking section but got no replies.:confused:

i've been reading and trying suggestions for about a week now.  i think part of the problem is that i know nothing about the directions i'm following because i don't understand the language of computers.  i've bin sudo-ing and modprobing boxcutters and such.also ndis wrapping things (i don't know what any of it really means!) i would like to somehow start fresh.  does this require re-installation?  i hope not.:(

it seems my issue is fairly common (maybe that's why i got no replies, people are prolly tired of seeing and responding to this issue).  i have a broadcom bcm4318. a dlink di-624 router and a compaq presario m2000 laptop with hardy installed.

my problem is that i cannot connect to the net wirelessly.  the strangest part though, is that the first day i got the laptop i did connect wirelesly.  i knew nothing about networking though and had my net provider walk me through the naming of my network, after which point i cannot connect.  also, the network manager does not even list any wireless networks (my neighbor's) like it did before.  i've read posts about network manager issues.

thank you in advance for any advice. :redface:

btw, here's a list of info that seems to be of help to advice givers.

heather@freekbox:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
heather@freekbox:~$

---

### Post by LowSky on 2009-08-14
the newer verios 9.04 will work with your wifi chipset
you can download it here, or use the upgrade feature of your current version

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

once installed you go to system>admin> drivers> and turn it on... siple as that.

---

### Post by Ric_NYC on 2009-08-14
> **LowSky said:**
> the newer verios 9.04 will work with your wifi chipset
you can download it here, or use the upgrade feature of your current version

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
[https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes)

once installed you go to system>admin> drivers> and turn it on... siple as that.


I did that. I could not connect to the internet using Hardy Heron. Then I installed Jaunty and I got my wireless internet working very well.

---

### Post by earthlovin on 2009-08-14
wow! thank you SOOOO much!  i had no idea it could be that easy!  :lolflag:
so at the the risk of sounding like even more of a dunce...do i following the first set of instructions for the network upgrade or the network upgrade for ubuntu servers...

they seem to be two different options...

---

### Post by earthlovin on 2009-08-14
> **Ric_NYC said:**
> I did that. I could not connect to the internet using Hardy Heron. Then I installed Jaunty and I got my wireless internet working very well.

oh. maybe not so easy then?  so to get jaunty instead of hardy, do i have to uninstall and reinstall?  of is it possible to upgrade a couple times to jaunty?  does it work that way?

---

### Post by Ric_NYC on 2009-08-14
> **earthlovin said:**
> oh. maybe not so easy then?  so to get jaunty instead of hardy, do i have to uninstall and reinstall?  of is it possible to upgrade a couple times to jaunty?  does it work that way?

I don't know if it was fixed in Hardy. I just upgrade to Jaunty and the internet started working without tweaks!

---

### Post by earthlovin on 2009-08-14
mkay.  it looks like i have to do it in steps though.  i have to upgrade from 8.04 hardy to 8.10 intrepid THEN to 9.04 jaunty.

i'll give it a try.

---

### Post by earthlovin on 2009-08-14
:P YAY!!  5 hours and two upgrades later and i'm online wirelessly!!!!  thank you folks fer helpin!!  yay 9.0!!

---

