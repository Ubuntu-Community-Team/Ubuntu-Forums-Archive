---
title: "Can't get online w/ Ubuntu Maverick"
date: 2011-02-11
forum: New to Ubuntu
---

### Post by kbrownk on 2011-02-11
I'm using a Toshiba A25-S207 laptop. I have a dual-boot partition w/  Windows XP which has no problem using my wireless card WPC54G ver 3.1. I  gather the drivers for this card don't work w/ Linux unless I  apparently use something called ndiswrapper.

It seems the 1st step commonly asked for in forum troubleshooting is to provide the chipset type by typing lspci..., but this provides a whole bunch of info none of which explicitly says anything about chipsets. All I know is that the processor is intel pentium 2.66GHz.

I was very pleased with how easy it was to install Ubuntu 10.10 Maverick. Beyond installation though I've gotten nowhere in 2 days of effort.

I can't get online wired or wireless. I tried to follow instructions from related posts such as getting the latest ndiswrapper and the drivers for my wireless card (WPC54G ver 3.1), but each step suggested leads to further confusion on how to do that step, I feel like I'm digging myself a hole rather than making any progress.

I can't install this ndiswrapper. After trying to follow broken links, I came across 3 files I guess could be the ndiswrapper file I'm supposed to install (ndiswrapper_1.56.orig.tzr.gz, ndiswrapper_1.56-3.debian.tar.gz, and one called ndiswrapper-1.56). I extracted all of them, but then I'm at a loss for how to install anoy one of them. There's a readme  and an Install doc with ridiculous instructions I can't follow. One says I need an include directory and a .config file in /lib/modules/'uname -r'/build, but I don't see either. Skipping to the next command in the instructions doesn't work.

Isn't there anything I can just click on and install like I can do for Windows? If not, can someone please guide a complete beginner like me to get internet access so I can actually start learning Linux?

Thanks,
kbrownk

---

### Post by cariboo on 2011-02-11
From the looks of it, your device uses a broadcom chipset, Have you gone to System->Administration->Hardware Drivers/Additional Drivers to see if there is a closed source driver for your device?

If you open a terminal and run the following command:

```
sudo lshw -C network > network.txt
```

The above command will create a text file called network.txt, that you can transfer to a system with an internet connection, and paste the results in your next post.

---

### Post by kbrownk on 2011-02-11
Well I only found System->Administration->Additional Drivers, which 1st gets an error saying to '...please check network', then 'searches for available drivers' which results in a window saying 'No proprietary drivers are in use on this system.'

Here is the network.txt file:

*-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: 10
       serial: 00:08:0d:5d:1f:60
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:11 ioport:ed00(size=256) memory:f7efff00-f7efffff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:02:2d:b3:40:f9
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=orinoco_cs driverversion=2.6.35-22-generic firmware=Lucent/Agere 9.48 link=no multicast=yes wireless=IEEE 802.11b

Thanks,
kbrownk

---

### Post by kbrownk on 2011-02-12
I'm sure this is obvious, but I assume this network log isn't going to say anything about the linksys I want to install drivers for, but instead the integrated internet devices.

Should I maybe try a different Linux OS? I'm dying to get this going to try out a program developed for Linux only, and I don't want to keep reverting to Cygwin.

Thanks,
kbrownk

---

### Post by davidmohammed on 2011-02-12
have a read of this [thread]("http://ubuntuforums.org/showthread.php?t=1602482") - hopefully it fixes your issue.

---

### Post by kbrownk on 2011-02-12
thanks, my power cord broke on me today so I'll give the efforts in this thread a shot once the new one gets here in hopefully less than a week.

kbrownk

---

