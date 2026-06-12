---
title: "Can't use my wireless"
date: 2011-01-11
forum: New to Ubuntu
---

### Post by jonpon on 2011-01-11
Hi Guys
Ive just installed ubuntu 10.04 on my sons new PC but the wireless won't work, 
I tried to install the driver downed from the Edimax website but nothing seems to be working
Has anyone any ideas?
heres some info:
```
t@fynn-desktop:~# lspci -nn
00:00.0 Host bridge [0600]: Advanced Micro Devices [AMD] RS780 Host Bridge [1022:9600]
00:01.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx) [1022:9602]
00:0a.0 PCI bridge [0604]: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 5) [1022:9609]
00:11.0 SATA controller [0106]: ATI Technologies Inc SB700/SB800 SATA Controller [AHCI mode] [1002:4391]
00:12.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:12.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:12.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:13.0 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller [1002:4397]
00:13.1 USB Controller [0c03]: ATI Technologies Inc SB700 USB OHCI1 Controller [1002:4398]
00:13.2 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB EHCI Controller [1002:4396]
00:14.0 SMBus [0c05]: ATI Technologies Inc SBx00 SMBus Controller [1002:4385] (rev 3c)
00:14.1 IDE interface [0101]: ATI Technologies Inc SB700/SB800 IDE Controller [1002:439c]
00:14.2 Audio device [0403]: ATI Technologies Inc SBx00 Azalia (Intel HDA) [1002:4383]
00:14.3 ISA bridge [0601]: ATI Technologies Inc SB700/SB800 LPC host controller [1002:439d]
00:14.4 PCI bridge [0604]: ATI Technologies Inc SBx00 PCI to PCI Bridge [1002:4384]
00:14.5 USB Controller [0c03]: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller [1002:4399]
00:18.0 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration [1022:1200]
00:18.1 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map [1022:1201]
00:18.2 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller [1022:1202]
00:18.3 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control [1022:1203]
00:18.4 Host bridge [0600]: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control [1022:1204]
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc 760G [Radeon 3000] [1002:9616]
01:05.1 Audio device [0403]: ATI Technologies Inc RS780 Azalia controller [1002:960f]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 03)
03:06.0 Network controller [0280]: RaLink Device [1814:3060]

```

---

### Post by davidmohammed on 2011-01-11
is there a driver to be installed in System - Administration - Hardware drivers?

If not, please reply with the results of the command

sudo lshw -c network

---

### Post by jonpon on 2011-01-11
Thanks for responding,
 Nope, no drivers except my graphics card

```
fynn@fynn-desktop:~$ sudo lshw -c network
[sudo] password for fynn: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 6c:f0:49:99:6c:9c
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.2.34 latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:26 ioport:de00(size=256) memory:fdaff000-fdafffff(prefetchable) memory:fdaf8000-fdafbfff(prefetchable) memory:fda00000-fda1ffff(prefetchable)
  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:03:06.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=32 maxlatency=4 mingnt=2
       resources: memory:fdcf0000-fdcfffff
fynn@fynn-desktop:~$ 

```

---

### Post by davidmohammed on 2011-01-11
I think this is a rt2800 type wireless card.  

I dont think this is in the lucid kernel.

You could try either one of the 2.6.35 maverick [mainline]("https://wiki.ubuntu.com/KernelTeam/MainlineBuilds?action=show&redirect=KernelMainlineBuilds") kernels or try a natty backport from [here]("http://www.ubuntuupdates.org/ppas/37")

---

### Post by jonpon on 2011-01-11
> **davidmohammed said:**
> I think this is a rt2800 type wireless card.  

I dont think this is in the lucid kernel.

You could try either one of the 2.6.35 maverick  kernels or try a natty backport from [here]("http://www.ubuntuupdates.org/ppas/37")

I think it's rt2870STA if that means anything to you.

Whats a "natty backport " and how do I go about it?

---

### Post by Hippytaff on 2011-01-11
Ralink are notorious for being difficult, it might be worth trying the xp driver with Ndiswrapper using ndisgtk

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by jonpon on 2011-01-11
Thats what I've installed 10.04LTS

---

### Post by Hippytaff on 2011-01-11
Sorry, I was looking at what you had in your profiley bit to the left (Feisty Fawn), then edited my original post because my original advice was rubbish :-)

---

### Post by jonpon on 2011-01-11
I'll see if I can change that now, whilst I wait for a "knight in shining" to sort out the WLAN problem

---

### Post by davidmohammed on 2011-01-11
> **jonpon said:**
> I think it's rt2870STA if that means anything to you.

Whats a "natty backport " and how do I go about it?

Actuall Hippytaff is correct ralink drivers are notorius.

Lucid is using a kernel version 2.6.32.  Natty is the next version of ubuntu (11.04) due in April.

The guys in that link I gave you try to fit the Natty kernel (2.6.37) into Lucid.  

The instructions to install the ppa are at the top of the webpage - the package name is 

linux-lts-backport-natty

---

### Post by jonpon on 2011-01-11
Not n00b proof though ,
Won't let me sudo get-apt linux-lts-backport-natty It's only an umberella file for a whole lot more similarly named files. Can't fathem it at all

---

### Post by davidmohammed on 2011-01-11
yeah you are correct.

try either

linux-image-generic-lts-backport-natty
or

linux-image-generic-lts-backport-maverick

depending if you want the natty or maverick kernel

---

### Post by jonpon on 2011-01-11
I installed the natty-generic and
Something has changed but it still wont connect.
Theres a little LED on the machine which now flashes!!! so some success, I think
Heres the code thing again
```
fynn@fynn-desktop:~$ sudo lshw -c network
[sudo] password for fynn: 
  *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 03
       serial: 6c:f0:49:99:6c:9c
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:40 ioport:de00(size=256) memory:fdaff000-fdafffff memory:fdaf8000-fdafbfff memory:fda00000-fda1ffff
  *-network
       description: Wireless interface
       product: RaLink
       vendor: RaLink
       physical id: 6
       bus info: pci@0000:03:06.0
       logical name: wlan0
       version: 00
       serial: 00:1f:1f:aa:d5:ad
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.37-12-generic firmware=0.11 latency=32 link=no maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:20 memory:fdcf0000-fdcfffff
fynn@fynn-desktop:~$ 

```

---

### Post by jonpon on 2011-01-12
Another problem cropped up after I upgraded with the "linux-image-generic-lts-backport-natty"
 my Graphics card stopped working and it wont let me download the Firmware just says "unknown error"
Can I get it back to pre-"linux-image-generic-lts-backport-natty" situation?

---

### Post by Trandre on 2011-01-12
I had a similar problem on my 10.04 LTS. 

Whay helped me was that I first ran in terminal "nm-tool". There i saw that that my wifi points appeared. 

If they do with you i can try to find the How-to guide I followed and fixed the issue

---

### Post by davidmohammed on 2011-01-12
> **jonpon said:**
> Another problem cropped up after I upgraded with the "linux-image-generic-lts-backport-natty"
 my Graphics card stopped working and it wont let me download the Firmware just says "unknown error"
Can I get it back to pre-"linux-image-generic-lts-backport-natty" situation?

I presume you've got nvidia graphics?

If so, you'll need to install the linux headers as well

i.e.

sudo apt-get install linux-headers-generic-lts-backport-natty

Go back to System - Administrator - Hardware drivers.

Deactivate the nvidia driver and then reactivate it.  This time nvidia should recompile against the headers correct.

Actually the results you gave means that your wireless card is now recognised.

Right click the network manager applet and ensure both "enable networking" and "enable wireless" are ticked.  In 10secs to 1 minute, when you left click on the network manager applet it should show all your possible wireless access points.

... if you want to boot up with the original lucid kernel then when you first start your computer, press and hold the shift key.  This will display your grub kernels - use the up and down keys to select the lucid kernel (2.6.32.x)

---

### Post by jonpon on 2011-01-13
I've worked it out!
I upgraded to UBUNTU 10.10 (although this Probably wasn't necessary)
and found [this]("http://ubuntuforums.org/showthread.php?t=1615304&page=5") thread and followed the instructions. and amazingly it works
----------------

May Root be with you.

---

