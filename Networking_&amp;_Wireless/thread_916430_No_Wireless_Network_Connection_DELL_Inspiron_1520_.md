---
title: "No Wireless Network Connection: DELL Inspiron 1520 w/ Intel PRO Wireless 3945ABG"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by duffyatkinson on 2008-09-10
Hi all. Brand new to Ubuntu. It's been a challenge to say the least!

Apologies for starting a new thread on an old problem for most of you, but I've been all over the forum trying commands and setups to get a wireless connection but no luck. I installed Wicd, but it didn't provide relief. The UNCLAIMED flag leads me to believe that it is probably just a driver issue, but I'm not sure. I believe I downloaded the correct WinXP driver. I installed the backports-modules. I have a working wired connection.

I installed Hardy in a dual-boot configuration with Vista. I am on a 6mb/s DSL line with a NETGEAR WGR614 v.7 wireless router w/ WPA1 encryption and SSID now being broadcast. At least I managed to get my bluetooth mouse to work!!

Here is the output of 'sudo lspci -nn':

[B]00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a02] (rev 0c)
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller [8086:2a03] (rev 0c)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 02)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 02)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 02)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 02)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 02)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 02)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 02)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 02)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f2)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 02)
00:1f.2 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller [8086:2828] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 02)
03:00.0 Ethernet controller [0200]: Broadcom Corporation BCM4401-B0 100Base-TX [14e4:170c] (rev 02)
03:01.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05)
03:01.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22)
03:01.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12)
03:01.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)
0c:00.0 Network controller [0280]: Intel Corporation PRO/Wireless 3945ABG Network Connection [8086:4222] (rev 02)[/B]

And here is the output of 'sudo lshw -C network':

[B]duffy@duffy-laptop:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0c:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:1c:23:aa:61:02
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=10.0.0.5 latency=64 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s[/B]

Any and all help would be GREATLY appreciated! Thank you.

---

### Post by duffyatkinson on 2008-09-13
Anyone????  Really could use some help!  :(

I purchased the "Official Ubuntu Book, 3rd Ed." and read it cover to cover. It is good as a historical overview but VERY thin on details. 

Can anyone recommend a good, printed reference book that will give me all of the command line syntax, as well as working with the GUI, repositories, etc?  I specifically want to get detail on such things as WPA Supplicant, Network Manager & Wicd, working with drivers, and the linux backports functions.

If I could get wireless networking operational, I'm golden.

Any help would be appreciated.  Thx.

---

### Post by airjaw on 2008-09-14
Hmmm.. i have the same laptop and wireless card and i got mine working..
i don't think reading the ubuntu guide will help.  These things are more like problem solving and research.  Sorry i can't remember what I did to get it working but I think its just a matter of finding (and installing) the **correct** drivers.

---

### Post by duffyatkinson on 2008-09-21
> **airjaw said:**
> Hmmm.. i have the same laptop and wireless card and i got mine working..
i don't think reading the ubuntu guide will help.  These things are more like problem solving and research.  Sorry i can't remember what I did to get it working but I think its just a matter of finding (and installing) the **correct** drivers.

Thanks Airjaw.

I uninstalled, ditched the ISO Live CD version, and reinstalled via the Wubi installer portal and everything is working like a charm! Bluetooth mouse, wireless connection, everything!

---

