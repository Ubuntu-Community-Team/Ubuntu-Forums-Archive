---
title: "atheros"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Snappo on 2008-05-24
Ok, I have had ubuntu for about a month now but i'm still stuck on windows. The reason is i'm not able to use the internet on ubuntu. Mbarak has helped me a lot and we have gone all the way around back to square one. I have an atheros chipset and i have came to find out madwifi is already installed on ubuntu and it does show support under restricted drivers. However the i'm not able to use the wifi when i try to scan via terminal it just tells me that l0 & eth0 do not support scanning it says nothing about my wireless card. I have tried thee following commands in the terminal to get the wireless running

sudo modprobe ath_pci (no problems running)
sudo ifconfig ath0 up (device error)

Some more information
I have a easynote r1005

lspci
> snappo@snappo-linux:~$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.1 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.2 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.3 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.4 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:00.7 Host bridge: VIA Technologies, Inc. CN400/PM880 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:06.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: VIA Technologies, Inc. S3 Unichrome Pro VGA Adapter (rev 02)
snappo@snappo-linux:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)
*-network:0 UNCLAIMED
description: Ethernet controller
product: AR5212/AR5213 Multiprotocol MAC/baseband processor
vendor: Atheros Communications Inc.
physical id: 6
bus info: pci@0000:00:06.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: cap_list
configuration: latency=0 maxlatency=28 mingnt=10
*-network:1
description: Ethernet interface
product: VT6102 [Rhine-II]
vendor: VIA Technologies, Inc.
physical id: 12
bus info: pci@0000:00:12.0
logical name: eth0
version: 74
serial: 00:40:d0:89:90:b0
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical
configuration: broadcast=yes driver=via-rhine driverversion=1.4.3 latency=128 maxlatency=8 mingnt=3 module=via_rhine multicast=yes


So if anyone has any ideas please shoot :)

---

### Post by DVANDERM on 2008-05-24
> **Snappo said:**
> Ok, I have had ubuntu for about a month now but i'm still stuck on windows. The reason is i'm not able to use the internet on ubuntu. Mbarak has helped me a lot and we have gone all the way around back to square one. I have an atheros chipset and i have came to find out madwifi is already installed on ubuntu and it does show support under restricted drivers. However the i'm not able to use the wifi when i try to scan via terminal it just tells me that l0 & eth0 do not support scanning it says nothing about my wireless card. I have tried thee following commands in the terminal to get the wireless running

sudo modprobe ath_pci (no problems running)
sudo ifconfig ath0 up (device error)

Some more information
I have a easynote r1005

lspci



So if anyone has any ideas please shoot :)

It looks like you are in the same boat that I am in with my wireless card for my laptop. I can't get power to the card or nothing.

 Ubuntu 8.04 works great on my desktop. Wish it would on my laptop. 

Did you try ndiswrapper with the XP driver?

---

### Post by Snappo on 2008-05-24
> **DVANDERM said:**
> It looks like you are in the same boat that I am in with my wireless card for my laptop. I can't get power to the card or nothing.

 Ubuntu 8.04 works great on my desktop. Wish it would on my laptop. 

Did you try ndiswrapper with the XP driver?

Yeh i did no results there

---

### Post by Snappo on 2008-05-25
bump

---

### Post by floreal on 2008-05-25
i have an atheros wireless card too. I think you should use madwifi. I managed to get wireless working after installing madwifi. After a "modprobe ath_pci" on terminal, you will see it is working. But madwifi on the repository does not make its job. I compiled from source code.

---

