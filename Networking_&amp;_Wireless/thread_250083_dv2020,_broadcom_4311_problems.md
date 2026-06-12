---
title: "dv2020, broadcom 4311 problems"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by Radarsat-1 on 2006-09-03
Hi,

I (now) know that this wireless chip is apparently a "known" problem in Linux, but still I'm hoping to get some help.

I recently bought a new HP DV2020 Pavillion laptop. It's beautiful!  AMD64 dual-core, with 1GB of RAM, Nvidia graphics, and built-in *everything*.

I can't wait to install Ubuntu on it. However, I wanted to make sure that I could get wireless working before doing anything, so I've been trying things out on the Live CD. To my dismay, I discovered that the built-in wireless chipset, Broadcom 4311, has terrible Linux support. I will be firing off an email to HP and Broadcom to demand help, but since I expect nothing from doing so, I thought I'd take a crack at it.

So far I've tried the Linux built-in bcm43xx drivers using the bcm43xx-fwcutter tool, as well as Ndiswrapper and driverloader. I've tried all three solutions using both 64-bit and 32-bit varieties of Ubuntu Dapper. (Always making sure I was using the correct 32- or 64-bit Windows drivers.)

In the case of bcm43xx, the only indication I get that anything is happening (even after extracting the firmware into /lib/firmware/.../) is a syslog message: "bcm43xx"
One line. That's it.

Next, driverloader ... hm, well it just didn't seem to work, and I didn't feel like using proprietary software anyways.

Ndiswrapper seems to be the best approach for now. I made sure the bcm43xx module was not loaded. I tried downloading and compiling the latest "testing" release, 1.24rc3.

No dice. The wlan0 device just doesn't show up. (ie., not with iwconfig nor  /proc/net/dev)

The following is the relevant syslog output, from 32-bit Dapper:

```

Sep  3 14:21:45 ubuntu kernel: [17181048.348000] ndiswrapper: driver bcmwl5 (Broadcom,12/17/2005, 4.10.40.1) loaded
Sep  3 14:21:45 ubuntu kernel: [17181048.352000] **** SET: Misaligned resource pointer: e5589302 Type 07 Len 0
Sep  3 14:21:45 ubuntu kernel: [17181048.352000] ACPI: PCI Interrupt Link [LK2E] enabled at IRQ 19
Sep  3 14:21:45 ubuntu kernel: [17181048.352000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 233
Sep  3 14:21:45 ubuntu kernel: [17181048.352000] ndiswrapper (NdisWriteErrorLogEntry:237): log: C0001393, count: 1, return_address: f8ccbc91
Sep  3 14:21:45 ubuntu kernel: [17181048.368000] ndiswrapper (NdisWriteErrorLogEntry:240): code: 22
Sep  3 14:21:45 ubuntu kernel: [17181048.376000] ndiswrapper (miniport_init:269): couldn't initialize device: C0000001
Sep  3 14:21:45 ubuntu kernel: [17181048.376000] ndiswrapper (pnp_start_device:426): Windows driver couldn't initialize the device (C0000001)
Sep  3 14:21:45 ubuntu kernel: [17181048.376000] unregister_netdevice: device eth%%d/ccb98000 never was registered
Sep  3 14:21:45 ubuntu kernel: [17181048.380000] ndiswrapper (miniport_halt:326): device ccb98260 is not initialized - not halting
Sep  3 14:21:45 ubuntu kernel: [17181048.380000] ndiswrapper: device eth%%d removed
Sep  3 14:21:45 ubuntu kernel: [17181048.380000] ACPI: PCI interrupt for device 0000:01:00.0 disabled
Sep  3 14:21:45 ubuntu kernel: [17181048.380000] ndiswrapper: probe of 0000:01:00.0 failed with error -22
Sep  3 14:21:45 ubuntu loadndisdriver: loadndisdriver: load_device(448): couldn't load device
Sep  3 14:21:45 ubuntu last message repeated 4 times

```

I think the important line here is "PCI interrupt for device ... disabled."  There is a switch on the front of the machine that allows you to disable the wireless... it seems that it is more of a software-controlled switch, and I have left it switched to "on", but it means I can't be 100% sure that the wireless chipset is "enabled". Anyone have any ideas? Is my chipset disabled, and if so, how can I enable it? Do I need to do something with ACPI? (I checked the BIOS, there seems to be no relevant options.)

Thanks.
If all else fails I may just have to go buy a USB dongle, but ... I'd really prefer not to.

---

### Post by reedatschool on 2006-09-05
I managed to get the 4311 to work with the 32 bit and 64 bit installs on my Compaq Presario V3000 (V3018CL).  

To get the Wireless to work I used a freshly compiled version of the new ndiswrapper util at

[http://sourceforge.net/project/showf...ckage_id=99148](http://sourceforge.net/project/showf...ckage_id=99148)

I followed most of the walkthrough here

[http://www.ubuntuforums.org/showthre...highlight=4311](http://www.ubuntuforums.org/showthre...highlight=4311)

I think I may have even copied the files on the above link over the top of my Windows drivers which came with the computer to get the 32 bit to work.  The 64 bit was easier as I just used the Windows drivers (If you can't find them I will mail them to you).

I have also had some issues with the other kernels like the K7 for the 32 bit, but the 386 kernel works just fine (Albiet with only one processor).

Goodluck with the Wireless,

Reed Harding

---

### Post by haiku99 on 2006-09-06
FWCutter will NOT work w/ a BCM4311 AKAIK,  but I was able to get mine working w/ ndiswrapper (also in a new HP FWIW)....however only w/ the latest version (1.23 a/o a few weeks ago)...there is a good writeup on how to download and install the latest version at [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

also, I used windows drivers copied from my XP partition and that worked OK...

---

### Post by Radarsat-1 on 2006-09-11
It's so strange, I keep reading that people have been able to get this Broadcom 4311 working by using the latest Ndiswrapper.

But no matter what I try, I *always* get:

[FONT="Courier New"]Windows driver couldn't initialize the device (C0000001)[/FONT]


I've tried using Ndiswrapper from CVS, even after downloading and compiling the very latest kernel release (2.6.17-7) from kernel.org. No luck.

I've even compiled ndiswrapper with DEBUG=3 to try and get some more insight, but as far as I can tell it dies when calling the Windows "init" function.  :frown: 

Unrelated, but I'm also having problems with the hda-intel ALSA driver on this laptop.

---

### Post by mmaki on 2006-09-15
I had to install and compile ndiswrapper 1.23 to get my Dell Latitude D620 Broadcom 4311 to work as described here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I used the drivers from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Card: Dell Wireless 1390 WLAN MiniCard (Dell Inspiron E1505, Dell Latitude D620, Dell Inspiron 640m, Dell Inspiron E1405)

    * Chipset: Broadcom BCM4311
    * pciid: 14e4:4311 (rev 01, subsys 1028:0007)
    * Driver: [http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE)
    * Other: Use the bcmwl5.inf and bcmwl5.sys in DRIVERS folder.

---

### Post by Radarsat-1 on 2006-09-30
Fixed!  I got it working by compiling the latest wireless-2.6 kernel (domesday branch), patching for PCI-E support, manually patching bcm43xx to recognize 4311, and installing the correct firmware (wl_apsta.o).  No problem! :)

(who said linux wasn't user friendly??  ;-)  )

More information here:
[http://bcm43xx.spugna.org/index.php?topic=137.0](http://bcm43xx.spugna.org/index.php?topic=137.0)

I'll probably create a DV2020 howto at some point and post the link here.

---

### Post by boz on 2006-10-02
> **mmaki said:**
> I had to install and compile ndiswrapper 1.23 to get my Dell Latitude D620 Broadcom 4311 to work as described here: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

I used the drivers from [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

Card: Dell Wireless 1390 WLAN MiniCard (Dell Inspiron E1505, Dell Latitude D620, Dell Inspiron 640m, Dell Inspiron E1405)

    * Chipset: Broadcom BCM4311
    * pciid: 14e4:4311 (rev 01, subsys 1028:0007)
    * Driver: [http://ftp.us.dell.com/network/R115321.EXE](http://ftp.us.dell.com/network/R115321.EXE)
    * Other: Use the bcmwl5.inf and bcmwl5.sys in DRIVERS folder.

How did you get the files from the .exe file?  I tried using cabextract and unshield and neither work for me.  I'm a dummy with both of those so I may be doing something wrong.

---

### Post by w b on 2006-10-04
from the dell .exe its just to open with ark and use ZIP format :)

---

### Post by discord on 2006-10-09
Radarsat, is it possible to create a module with the kernel sources from the ubuntu repos or do I have to create a custom kernel using the tools you described above? I'm running the 2.6.17 kernel under edgy right now and would like to make a module that works with the edgy kernel.

---

### Post by jrz on 2006-10-15
> **reedatschool said:**
> I managed to get the 4311 to work with the 32 bit and 64 bit installs on my Compaq Presario V3000 (V3018CL).  

To get the Wireless to work I used a freshly compiled version of the new ndiswrapper util at

[http://sourceforge.net/project/showf...ckage_id=99148](http://sourceforge.net/project/showf...ckage_id=99148)

I followed most of the walkthrough here

[http://www.ubuntuforums.org/showthre...highlight=4311](http://www.ubuntuforums.org/showthre...highlight=4311)

I think I may have even copied the files on the above link over the top of my Windows drivers which came with the computer to get the 32 bit to work.  The 64 bit was easier as I just used the Windows drivers (If you can't find them I will mail them to you).

I have also had some issues with the other kernels like the K7 for the 32 bit, but the 386 kernel works just fine (Albiet with only one processor).

Goodluck with the Wireless,

Reed Harding

------------------
I'm trying to help a friend get his new computer working satisfactorly, and now we are working on the wireless part. It is a Compaq V3042AU, AMD64 X2, probably similar to what you have and  I was hoping that you might be able to tell me where to find the 32bit Windows drivers necessary, we have the 32 bit version of Ubuntu 6.06 LTS installed. I have an IBM ThinkPad R40 notebook loaded with Windows XP-Pro and an install CD, but don't know what file(s) pertain to the drivers necessary or where they would be located, Hard Disk or CD, and how to extract them if in a .cab file or something else. Any help would be greatly appreciated. Other than this we are more than pleased with Ubuntu, and I am seriously thinking of dumping Windows off my IBM once we get this new computer running smoothly. Thanks.
Joe (Thailand)

---

### Post by shasto on 2007-02-16
Ok using HP dv2104eu Pavilion Laptop Broadcom 4311 device, using bcm43xx-fwcutter006 (from Berlios, compiled and installed) - BTW: Edgy 64-Bit (Kernel# 2.6.17-11). Plenty of tutorials on this but after about two days I discovered some minor things I had missed - using the fwcutter and the HP sp34512.exe (Broadcom Drivers from HP) you must -w to /lib/firmware/<kernel> and you also must be using the bcmwl564.sys not the bcmwl5.sys (which is 32-Bit).

Now on to NDISWRAPPER:
remove all NDISWRAPPER installations
download 1.37 source and make

NOTE: before installing please comment out the eth1 line in /etc/iftab
also add the *blacklist bcm43xx* to /etc/modprobe.d/blacklist **BEFORE PROCEEDING**

ok now ndiswrapper -i bcmwl5.inf
ndiswrapper -l
ndiswrapper -m
depmod -a
modprobe ndiswrapper

and then test using
iwlist wlan0 scanning
(You should also be seeing your little blue light) BTW: sliding the switch slider right is the on position!

in /etc/interfaces you should have/enter the following:
auto wlan0
iface wlan0 inet dhcp
wireless-essid <wirelessnamegoeshere>
wireless-key <128BitHexKeygoeshere>

Now restart and viola you should have it.
Note this isn't meant as a complete guide, just a couple of gotcha's I got caught out by.

PS: I am also using the 64Bit Automatix Nvidia Drivers perfectly with this

This post was written from a rocking :guitar: and now complete (besides a webcam I don't use and SD Card I haven't tested) installation of Edgy 64-Bit on a HP dv2104eu connected through the my in built Broadcom 4311 wireless card, took two days but a good experience / education ... now I am going to have a beer and watch Episode 12 of Heroes (yes on the same laptop):popcorn:

---

