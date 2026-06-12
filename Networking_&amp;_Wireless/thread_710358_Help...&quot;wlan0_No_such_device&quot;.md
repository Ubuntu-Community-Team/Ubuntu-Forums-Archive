---
title: "Help...&quot;wlan0: No such device&quot;"
date: 2008-02-28
forum: Networking &amp; Wireless
---

### Post by burns863 on 2008-02-28
Hi guys,

Started a new thread to try and generate some new faces and fresh minds to help me with my problem :)  I woul really appreciate if you could ready the last couple of posts of my previous thread to get the jist of where I am at now @ [http://ubuntuforums.org/showthread.php?p=4422301#post4422301](http://ubuntuforums.org/showthread.php?p=4422301#post4422301)

However, to sum it up pretty quickly... my Edimax 7728ln WLAN PCI card (with (RT2860) chipset is not being "seen".  The amount of feedback I have got to say the card is there, and atached to the machine is that the green light it on (which I guess means nothing?)

Here are the results of a few commands...

```
daniel@project-host:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: SiS900 PCI Fast Ethernet
       vendor: Silicon Integrated Systems [SiS]
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth0
       version: 02
       serial: 00:06:4f:03:77:bc
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sis900 driverversion=v1.08.10 Apr. 2 2006 duplex=full ip=192.168.2.3 latency=32 link=yes maxlatency=11 mingnt=52 module=sis900 multicast=yes port=MII speed=100MB/s

```

```
daniel@project-host:~$ sudo lspci
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:04.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:04.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:04.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
00:09.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV5 [RIVA TNT2 Ultra] (rev 11)

```

```
daniel@project-host:~$ ifconfig wlan0 up
wlan0: ERROR while getting interface flags: No such device

```

I am completely lost as for what to do next!  Im on a fresh install and guess there is no point continuing installing the RA2860 source code the card is at least seen right?

Thanks in advance

Dan :(

---

### Post by jan quark on 2008-02-28
perhaps your wlan card is just not supported yet by ubuntu

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsEdimax)

---

### Post by rustybronco on 2008-02-28
> **burns863 said:**
>   The amount of feedback I have got to say the card is there, and atached to the machine is that the green light it on (which I guess means nothing?)

I am completely lost as for what to do next!  Im on a fresh install and guess there is no point continuing installing the RA2860 source code the card is at least seen right?

Thanks in advance

Dan :(RT2860?
this is what I would do... fresh install with no card inserted, then after all updates are done (connected to an ethernet cable to router/modem) reboot (cold), insert card, wait a few minutes. does it ask to install the drivers for your card? if not type **lspci -nn** does your card show now? if it does show up then try this [http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419) plus the .inf and .sys off the cd that came with the card.

are you sure of the chipset of your card?

---

### Post by burns863 on 2008-02-28
I was reading some other posts and my card came out to have the RA2860 chipset, but other than that I cannot check as the card doesn't show in terminal (as can be seen in my first post).

On my first install of Ubuntu the card wasn't inserted.  Once inserted Ubuntu didn't prompt me for drivers what so ever :(

If I go for a fresh install for a third time, insert the card (i'll maybe try a different PCI slot) and it doesn't ask me for drivers, where should I go from there?

Also, I'm trying to stay away from the whole ndiswrapper driver install as after reading various posts I get the impression the card may not run in Wireless N? And only support B/G.  I am a little unsure as to why this is, but like I say, its what I took from other posts.  Hence why I am installing from source code.

But I need to conquer the card even being seen first! haha.

Thanks for your help.  And lets keep the help flowing :lolflag:

---

### Post by rustybronco on 2008-02-28
> **burns863 said:**
> I was reading some other posts and my card came out to have the RA2860 chipset, but other than that I cannot check as the card doesn't show in terminal (as can be seen in my first post).

On my first install of Ubuntu the card wasn't inserted.  Once inserted Ubuntu didn't prompt me for drivers what so ever :(

If I go for a fresh install for a third time, insert the card (i'll maybe try a different PCI slot) and it doesn't ask me for drivers, where should I go from there?

Also, I'm trying to stay away from the whole ndiswrapper driver install as after reading various posts I get the impression the card may not run in Wireless N? And only support B/G.  I am a little unsure as to why this is, but like I say, its what I took from other posts.  Hence why I am installing from source code.

But I need to conquer the card even being seen first! haha.

Thanks for your help.  And lets keep the help flowing :lolflag:
some pc's have a hard time with cards in slot 1.
Swap it/the other cards around to a different slot(s) and then try lspci -nn, if it doesn't show up after that ?? we'll cross that bridge...

***edit*** any isa cards in use?

---

### Post by burns863 on 2008-02-28
Yes... its an older machine and has an old ISA sound card in it!  ISA cause conflicts?

---

### Post by rustybronco on 2008-02-28
> **burns863 said:**
> Yes... its an older machine and has an old ISA sound card in it!  ISA cause conflicts?My old memory is failing me, but slot 1 and isa cards (video ?) with certain memory sticks.
don't forget about bad memory sticks.
can't hurt to swap them and/or remove memory.
see if you can get the manual for the motherboard or look at  possible bios updates.

can you get the motherboard part number?

I had a server that wouldn't boot because of a bad memory stick. (pulled my hair out with that one) [http://ubuntuforums.org/showpost.php?p=4248386&postcount=31](http://ubuntuforums.org/showpost.php?p=4248386&postcount=31)

hope the new card isn't bad...

---

### Post by burns863 on 2008-02-28
> **rustybronco said:**
> My old memory is failing me, but slot 1 and isa cards (video ?) with certain memory sticks.
don't forget about bad memory sticks.
can't hurt to swap them and/or remove memory.
see if you can get the manual for the motherboard or look at  possible bios updates.

can you get the motherboard part number?

I had a server that wouldn't boot because of a bad memory stick. (pulled my hair out with that one) [http://ubuntuforums.org/showpost.php?p=4248386&postcount=31](http://ubuntuforums.org/showpost.php?p=4248386&postcount=31)

hope the new card isn't bad...

Good point.  Although I didn't think dodgy RAM could cause a PCI card to not be detected?  Can't hurt to give it a go though!  

With the machine being old, I'm not sure if there will be any BIOS updates, although again it cant hurt to look!  I've got to get this sorted for a higher spec machine too.  Its part of my Uni project looking at media centre setups.  I'm comparing an Apple setup (iMac and Apple TV) to an Open Source OC based setup.  Most likely to be Ubuntu & Myth TV! ....Running out of time though with problem after problem!  Really appreciate the help :)

---

### Post by burns863 on 2008-03-03
Bump :) ....Still stuck!

---

### Post by burns863 on 2008-03-04
Anybody? ....:confused:

---

### Post by eldragon on 2008-03-04
im going to go with the obvious.....

have you tried the wireless card on another machine?

i had a tv capture card that didnt work (lspci didnt show it either), ended up being a dodgy card.

---

### Post by burns863 on 2008-03-04
Good point.  I havent done as my initial thoughts have been "its brand new" but then again I gues that doesn't really mean anything!  Im gong to give it a go in another machine a.s.a.p.

If that fails (ie if it works in anothr machine), have you any more ideas?  I just cant see it being the motherboard as it has been working with no problems at all when previously running a different OS.  Plus, the card isn't working in any of the PCI slots, yet the ethernet card works perfectly.

Thanks for your help :)

Its so frustrating!

Dan

---

### Post by burns863 on 2008-03-04
OK... same card, different machine.  iwconfig still reports no wireless extensions, however the lspci command now see's (in this machine) the wireless card:

```
daniel@Daniel-Project:~$ lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 94c4
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:04.0 Multimedia audio controller: Creative Labs SB Audigy (rev 04)
02:04.1 Input device controller: Creative Labs SB Audigy Game Port (rev 04)
02:04.2 FireWire (IEEE 1394): Creative Labs SB Audigy FireWire Port (rev 04)
02:06.0 Network controller: RaLink Unknown device 0601

```

So... the card is ok, as it can be seen in another machine.  However, I now have two problems:

1)  The card thought to be faulty, AND the card that was already sat in the second machine both show as unknown devices.  How do I get this machine to see one of them as wlan0? Edit:  lshw -C network command shows the wireless card to be UNCLAIMED in this machine.

2) The first machines card doesn't appear to be faulty as it can be seen in the second machine.  What in gods name is wrong with the first machine?  Should I just install the card and hope it is seen after installation?  Or is it a case of the card isn't seen now, so just installing the drivers wont 'make it' be seen?

:confused::(

---

### Post by odiseo77 on 2008-03-04
> **burns863 said:**
> 1)  The card thought to be faulty, AND the card that was already sat in the second machine both show as unknown devices.  How do I get this machine to see one of them as wlan0? Edit:  lshw -C network command shows the wireless card to be UNCLAIMED in this machine.

2) The first machines card doesn't appear to be faulty as it can be seen in the second machine.  What in gods name is wrong with the first machine?  Should I just install the card and hope it is seen after installation?  Or is it a case of the card isn't seen now, so just installing the drivers wont 'make it' be seen?

As for your first question, in order to get this machine (the second one) to show the card as an interface (eg. to show it when you type iwconfig), you need the driver installed. You can find it [here]("http://www.edimax.com/en/produce_detail.php?pl1_id=1&pl2_id=44&pl3_id=126&pd_id=225") (drop down to the bottom of the page and click on "Linux Source Code"). I downloaded the driver and had a look at the README file. I think you need to install the kernel sources before compiling the driver (***sudo apt-get install linux-source***). Also, have a close look at the README file since you must edit the "Makefile" in order to get the driver to compile.

---

### Post by lumiad on 2008-03-04
```
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
```
is your ethernet card


you might try to:
```
modprobe -l | grep 8139
```

when present type:
```
modprobe 8139cp
```



Also see [http://ubuntuforums.org/showthread.php?t=206185]("http://ubuntuforums.org/showthread.php?t=206185")

---

### Post by burns863 on 2008-03-08
Thank you everyone for your help!  I am glad to say that I am now rolling on 802.11!  Im sorry to say that after all this, it was a problem with the seating of the card in the motherboard, despite several re-seats of the device.  It was the case that was causing a miniscule part of the pins to not sit 100% and connect up as they should.

Also... went with ndiswrapper in the end and all is well!

Thanks again guys :D

---

