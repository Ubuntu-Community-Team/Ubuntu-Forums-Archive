---
title: "WIFI /w Intrepid"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by pelagic on 2008-11-06
Hello forum,

I got a problem with my PCMCI WIFI card. Actually I got 2 problems:

1) And this happend already with 8.04: booting with my WIFI card in the pcmcia slot did not work. booting always got stuck. I found a work around and only inserted the card *after* booting. Not real fun but working.

2) With 8.10 still the same with booting. But now the card doesnt seem to work even if I put it in the slot after booting.

Anyone has an idea how to solve this?

Environment:
 Laptop Dell Inspiron 8000 (way old)
 500 MB RAM
 Kernel 2.6.27-7
 WIFI: Zyxel ZyAIR B-100

Output from lspci:```

00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:01.0 PCI bridge: Intel Corporation 82815 815 Chipset AGP Bridge (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 02)
00:1f.0 ISA bridge: Intel Corporation 82801BAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801BAM IDE U100 Controller (rev 02)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation NV11 [GeForce2 Go] (rev b2)
02:03.0 Multimedia audio controller: ESS Technology ES1983S Maestro-3i PCI Audio Accelerator (rev 10)
02:06.0 PCI bridge: Actiontec Electronics Inc Mini-PCI bridge (rev 11)
02:0f.0 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.1 CardBus bridge: Texas Instruments PCI4451 PC card Cardbus Controller
02:0f.2 FireWire (IEEE 1394): Texas Instruments PCI4451 IEEE-1394 Controller
08:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)
08:08.0 Communication controller: Agere Systems WinModem 56k (rev 01)

```

output from lshw:```

  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:08:04.0
       logical name: eth0
       version: 08
       serial: 00:20:e0:68:5b:5c
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=half firmware=N/A latency=32 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s
  *-network
       description: 11M WLAN Card v3.0
       vendor: PCMCIA
       physical id: 0
       slot: Socket 0
       resources: irq:3
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 3
       logical name: pan0
       serial: 02:0a:f1:2b:ad:f0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes
  *-network:1
       description: Wireless interface
       physical id: 4
       logical name: wlan0
       serial: 00:a0:c5:40:37:ec
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=hostap firmware=1.4.2 multicast=yes wireless=IEEE 802.11b

```

extract from dmesg as attachment.

Any help is appreaciated!
/pelagic

---

### Post by asamax01 on 2008-11-17
Hi,

Your problem's like mine.
But I have one greater to solve first, and it seems you already solved it, maybe you can help me...

I see you have got Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08) installed on your system.

That's the main way I should get on the internet, but my ethernet card does not work as I installed Ubuntu (xubuntu 8.10 on Dell inspiron 8100).
Which module is running for your ethernet card?
How can I test and fix mine?
I am not yet skilled with linux commands, but I report these 2 (found them in another forum):

banano@NB1:~$ lspci | grep -i ethernet
08:04.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 08)

banano@NB1:~$ uname -a
Linux NB1 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

please help me if you can.
I already posted a specific 3ad, but no answers yet.
thx in advance - m.

---

