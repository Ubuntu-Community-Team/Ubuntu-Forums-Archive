---
title: "How do I know if my wireless card was detected?"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by fs_tigre on 2008-11-30
Hi,

I’m trying to connect my laptop to a wireless network and I just cannot figure this out.  It works fine when wired connected.

How can I know if my wireless card was detected?

I’m using a Linksys card Model: WPC11 ver. 4, on a Dell Inspiron 2650.

When I go to Network Connections and click on the Wireless tab it doesn’t show any networks.

Can someone guide me through the steps to accomplish this task? Sorry I’m completely new to linux (Ubuntu)

Thanks,
Fs_tigre

---

### Post by Ayuthia on 2008-11-30
> **fs_tigre said:**
> Hi,

I’m trying to connect my laptop to a wireless network and I just cannot figure this out.  It works fine when wired connected.

How can I know if my wireless card was detected?

I’m using a Linksys card Model: WPC11 ver. 4, on a Dell Inspiron 2650.

When I go to Network Connections and click on the Wireless tab it doesn’t show any networks.

Can someone guide me through the steps to accomplish this task? Sorry I’m completely new to linux (Ubuntu)

Thanks,
Fs_tigre
To see if your wireless card is found:
```
lspci -nn
```and see if the card is there.  You will also want to check:
```
lshw -C network
```and see if there is any info about the wireless card.  If there is, check the configuration line and it should have a driver there.  If there is a driver there, then it does recognize your card.  However, if you see information that it is UNCLAIMED or DISABLED, then the system is missing either the driver or firmware for the device.  If you are stuck, please post the results of the two commands.

---

### Post by fs_tigre on 2008-11-30
Hi,

Can someone tell me what do I need to do next... Please.

This is what I got after inputting the first command (lspci -nn).

[COLOR="RoyalBlue"]lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge [8086:1a30] (rev 05)
00:01.0 PCI bridge [0604]: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge [8086:1a31] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #1 [8086:2482] (rev 02)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801CA/CAM USB Controller #2 [8086:2484] (rev 02)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 42)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801CAM ISA Bridge (LPC) [8086:248c] (rev 02)
00:1f.1 IDE interface [0101]: Intel Corporation 82801CAM IDE U100 Controller [8086:248a] (rev 02)
00:1f.3 SMBus [0c05]: Intel Corporation 82801CA/CAM SMBus Controller [8086:2483] (rev 02)
00:1f.5 Multimedia audio controller [0401]: Intel Corporation 82801CA/CAM AC'97 Audio Controller [8086:2485] (rev 02)
00:1f.6 Modem [0703]: Intel Corporation 82801CA/CAM AC'97 Modem Controller [8086:2486] (rev 02)
01:00.0 VGA compatible controller [0300]: nVidia Corporation NV11 [GeForce2 Go] [10de:0112] (rev b2)
02:01.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
02:04.0 CardBus bridge [0607]: O2 Micro, Inc. OZ601/6912/711E0 CardBus/SmartCardBus Controller [1217:6972]
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)
fily@fily-laptop:~$[/COLOR]


and this is what i got after inputting the second command (lshw -c network).

l[COLOR="Blue"]shw -c network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 78
       serial: 00:08:74:e8:c9:9a
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=3c59x ip=192.168.1.102 latency=80 maxlatency=10 mingnt=10 module=3c59x multicast=yes
  *-network
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wmaster0
       version: 20
       serial: 00:0f:66:a1:75:ce
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:f1:bc:18:f2:12
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
fily@fily-laptop:~$ [/COLOR]


So, as you can imagine I'm completely new and don't know what I'm looking for, can someone help me telling me what do I need to do to make this wireless card work.

Thank you for your help Ayuthia.

---

### Post by fs_tigre on 2008-12-10
Hi,

I really need help to make my wireless work. I know I posted a lot code in my previews post but those are the results I got by doing what “Ayuthia” suggested me to do (not complaining I appreciate it) but honestly I don’t know what to do next.

Could some please guide me though the steps to make this work? Otherwise I will have to go back to XP and I don’t really want to do that.

Thanks

---

### Post by Ayuthia on 2008-12-10
This is your wireless card:
> 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)
This shows that your card has been detected and it is trying to use one of the kernel modules to make it work:
```
*-network
description: Wireless interface
product: RTL8180L 802.11b MAC
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:03:00.0
logical name: wmaster0
version: 20
serial: 00:0f:66:a1:75:ce
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list logical ethernet physical wireless
configuration: broadcast=yes driver=**rtl8180** latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11b
```

Are you able to see any wireless sites when you type:
```
sudo iwlist scan
```
in the Terminal?

---

### Post by fs_tigre on 2008-12-11
Hi,

First of all thank you all for your help. I think I will switch back to Windows Xp (my nightmare).  Last night when I turned my computer on it said that I had 160 updates and asked me if wanted to download and install the them I clicked yes and it started downloading than installing them, in the middle of the process an error occurred then I tried to cancel the installation but it was not responding so I hold the power button for a few seconds to turn it off manually, when I pressed this button again to turn it back on a blue message pop up warning me about an error clicked ok and after that the computer doesn’t come on it just sits there showing just text with an error, anyways I think this is too advanced for me so I will go back to XP.

Thanks,
Fs_tigre

---

### Post by ghayden on 2009-05-20
I am having a similar problem with a Gateway Solo 3350 laptop & WPC11 v.4.0.  I am communicating current via wired ethernet, but the wireless card is not responding.  From the previous posts, here is my terminal info:

root@shelby:~# lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge [8086:7190] (rev 03)
00:01.0 PCI bridge [0604]: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge [8086:7191] (rev 03)
00:07.0 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ISA [8086:7110] (rev 02)
00:07.1 IDE interface [0101]: Intel Corporation 82371AB/EB/MB PIIX4 IDE [8086:7111] (rev 01)
00:07.2 USB Controller [0c03]: Intel Corporation 82371AB/EB/MB PIIX4 USB [8086:7112] (rev 01)
00:07.3 Bridge [0680]: Intel Corporation 82371AB/EB/MB PIIX4 ACPI [8086:7113] (rev 03)
00:09.0 Multimedia audio controller [0401]: ESS Technology ES1988 Allegro-1 [125d:1988] (rev 12)
00:09.1 Communication controller [0780]: ESS Technology ESS Modem [125d:1989] (rev 12)
00:0a.0 CardBus bridge [0607]: Texas Instruments PCI1410 PC card Cardbus Controller [104c:ac50] (rev 01)
00:0d.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Rage Mobility P/M AGP 2x [1002:4c4d] (rev 64)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC [10ec:8180] (rev 20)
root@shelby:~# lshw -c network
  *-network               
       description: Realtek
       physical id: 0
       version: Rtl8139
       slot: Socket 0
       resources: irq:10
  *-network
       description: Ethernet interface
       product: 3c905C-TX/TX-M [Tornado]
       vendor: 3Com Corporation
       physical id: d
       bus info: pci@0000:00:0d.0
       logical name: eth0
       version: 78
       serial: 00:c0:9f:03:d7:58
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=3c59x duplex=full ip=192.168.1.25 latency=80 link=yes maxlatency=10 mingnt=10 module=3c59x multicast=yes port=MII speed=100MB/s
  *-network DISABLED
       description: Wireless interface
       product: RTL8180L 802.11b MAC
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 1
       bus info: pci@0000:02:00.0
       logical name: wmaster0
       version: 20
       serial: 00:0f:66:b2:fc:02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 latency=64 maxlatency=64 mingnt=32 module=rtl8180 multicast=yes wireless=IEEE 802.11b
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 7e:60:cd:8e:1a:5a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

How do you ENABLE the wireless card?  Thanks

---

