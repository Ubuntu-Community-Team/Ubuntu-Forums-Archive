---
title: "Need some help setting up a DWL-G510 wireless card."
date: 2005-11-16
forum: Networking &amp; Wireless
---

### Post by haliski on 2005-11-16
Howdy fellers, I'm a totaly n00b when it comes to linux so don't try to get to frustrated with me:) 

I've got a Dlink DWL-G510 wireless card, ubuntu didn't recognise it in the initial installation, and I can't seem to get it to work on ubuntu through any software. I don't even know where to look? 

Any help?

---

### Post by dbott67 on 2005-11-16
You may need to use NDISWrapper.  This program allows most "windows only" network devices to work in Linux.

Read how to set it up here:
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)

Additionally, you can check my signature below for a link to "supported hardware" and look up your network card.

EDIT: after a brief look, it appears as though the [DWL-510 is supported]("https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards").

-Dave

---

### Post by dbott67 on 2005-11-16
I just searched the forums and it appears that there are a number of people that have resorted to using NDISWrapper in order to get their cards working, so this is probably the route to take.

Could also post the output of the following commands:
```
sudo lshw -C network
```
```
dbott@breezy:~$ sudo lshw -C network
Password:
  *-network
       description: Wireless interface
       product: ACX 100 22Mbps Wireless Interface
       vendor: Texas Instruments
       physical id: 0
       bus info: pci@01:00.0
       logical name: wlan0
       version: 00
       serial: 00:40:05:b8:eb:74
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=acx_pci ip=192.168.1.100 multicast=yes wireless=IEEE 802.11b+
       resources: ioport:4000-401f iomemory:10810000-10810fff iomemory:10800000-1080ffff irq:11
dbott@breezy:~$
```
Next, post the output of lspci:
```
dbott@breezy:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (AGP disabled) (rev 02)
0000:00:04.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 12)
0000:00:05.0 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:05.1 IDE interface: Intel Corp. 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:05.2 USB Controller: Intel Corp. 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:05.3 Bridge: Intel Corp. 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:00:09.0 Communication controller: Toshiba America Info Systems FIR Port (rev 23)
0000:00:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)
0000:00:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 (rev 07)
0000:00:0d.0 Multimedia controller: C-Cube Microsystems Cinemaster C 3.0 DVD Decoder (rev 02)
0000:01:00.0 Network controller: Texas Instruments ACX 100 22Mbps Wireless Interface
dbott@breezy:~$
```
And finally, ifconfig:
```
dbott@breezy:~$ ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:56008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:56008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:4383386 (4.1 MiB)  TX bytes:4383386 (4.1 MiB)

wlan0     Link encap:Ethernet  HWaddr 00:40:05:B8:EB:74
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::240:5ff:feb8:eb74/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11055 errors:350 dropped:0 overruns:0 frame:0
          TX packets:11327 errors:8 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:9147582 (8.7 MiB)  TX bytes:1598594 (1.5 MiB)
          Interrupt:11 Base address:0x4000

dbott@breezy:~$
```

-Dave

---

### Post by haliski on 2005-11-17
Thanks a bundle, I'm going to get right on it!:D :D

---

### Post by haliski on 2005-11-23
Bagh. I tried the commands you gave me, and I also tried ndiswrapper. It all worked until i had to get the windows driver.

ndiswrapper -i ~/windows_driver/###

### should be the name of my driver, but I don't know where to get it off of windows.

i think the equivalent with linux is prism54, but I couldn't seem to get it to work with that either.

Note: My card is a DWL-G510.

Thanks in advance.

---

### Post by aaarg on 2005-11-23
[QUOTE=haliski]Howdy fellers, I'm a totaly n00b when it comes to linux so don't try to get to frustrated with me:) 

I've got a Dlink DWL-G510 wireless card, ubuntu didn't recognise it in the initial installation, and I can't seem to get it to work on ubuntu through any software. I don't even know where to look? 

Any help?[/QUOTE]

haliski, i just tested that card on my gf's box with the 5.10 live disk and it worked fine.

all i did was go to: system/administration/networking....it was listed as ath0(i think) but all you have to do is hit properties enter all your info (be sure to enter your DNS as well) then activate it.

i guess there could be different versions of the card, but i *think* it will work for you

---

### Post by haliski on 2005-11-23
My card isn't an atheros chip (I don't think). But I'll try it, thanks.

---

### Post by aaarg on 2005-11-23
ya, i have another d-link card (g520...i think) that one version works and the other doesnt....good luck

---

### Post by haliski on 2005-11-23
I went into the networking thing through system, administration, networking...

The two things there were eth0 and modem. I went into properties, and checked it out. I have DSL (not a static ip), and so my only viable choice was DCHP. I also tried it with my DNS name in there, and without it in there. No luck.

Shouldn't I have another choice like wlan0 instead of eth0?

---

### Post by Linux_Houftie on 2005-11-25
I'm having troubles with a DWL-650. Here's some info to hopefully help...

  *-network
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@02:08.0
       logical name: eth0
       version: 42
       serial: 00:08:0d:49:69:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.4.8-k2-NAPI duplex=full firmware=N/A ip=10.0.122.124 link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:fceff000-fcefffff ioport:df40-df7f irq:11
  *-network
       description: DWL-650 Wireless PC Card RevP
       product: ISL37101P-10
       vendor: D-Link
       physical id: 0
       version: A3
       slot: Socket 1



0000:00:00.0 Host bridge: Intel Corp. 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
0000:00:01.0 PCI bridge: Intel Corp. 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 02)
0000:00:1d.1 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #2) (rev 02)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 42)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 02)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 02)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 02)
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 420 Go] (rev a3)
0000:02:08.0 Ethernet controller: Intel Corp. 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller (rev 42)
0000:02:0b.0 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0b.1 CardBus bridge: Toshiba America Info Systems ToPIC95 PCI to Cardbus Bridge with ZV Support (rev 32)
0000:02:0d.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 03)



eth0      Link encap:Ethernet  HWaddr 00:08:0D:49:69:02
          inet addr:10.0.122.124  Bcast:10.0.122.255  Mask:255.255.255.0
          inet6 addr: fe80::208:dff:fe49:6902/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5636 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4075 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:7242160 (6.9 MiB)  TX bytes:487083 (475.6 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:10167 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10167 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:925432 (903.7 KiB)  TX bytes:925432 (903.7 KiB)




Ive been running around in circles all day and can't find anything that's helped on way or the other. :???:

---

### Post by Manveru913 on 2005-11-26
I have the same card (DWL-G510) and im almost positive it has a marvell W8300 chipset. Ive tried NDISWrapper but it wont work on my box either. My problem was with the modprobe step, but if youre just looking for the driver, [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#M](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List#M) this is a pretty good site, not ubuntu specific though... Can also skip right over to the D-Link site, thats what i did. Unless thats my mine wont work....

---

