---
title: "Broadcom BCM4318"
date: 2013-11-09
forum: Networking &amp; Wireless
---

### Post by xfuzzy on 2013-11-09
Hi, I am completely new to linux and I've been struggling with my wifi connection on my old laptop.

I installed lubuntu on my asus a6r and I cannot get my wifi working :/

I tried several ways, even from this very forum, none of them seems to be working. I can't even see a list of wifi's I could connect to. I am positive, that the wifi on my laptop is on.

What should I do, please?

Thank you!

Fuzzy

---

### Post by squakie on 2013-11-09
First, open a terminal window and do the following:

lspci <press enter>

copy and paste that output in a reply back here.

Since this is a laptop, some laptops have the wireless adapter connected to the internal USB buss, so please also:

lsusb <press enter>

and post the output in the same reply.

---

### Post by xfuzzy on 2013-11-10
lspci:

00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC410 Host Bridge (rev 01)
00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 82)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RC410M [Mobility Radeon Xpress 200M]
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
02:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
02:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 08)
02:03.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


lsusb

Bus 001 Device 003: ID 174f:a311 Syntek 1.3MPixel Web Cam - Asus A3A, A6J, A6K, A6M, A6R, A6T, A6V, A7T, A7sv, A7U
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. BT-183 Bluetooth 2.0+EDR adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04b4:0060 Cypress Semiconductor Corp. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

---

### Post by Hadaka on 2013-11-10
Hi,from a wired connetion please do..
```
sudo apt-get update
sudo apt-get upgrde
```
then do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-installer
sudo modprobe b43
```
thanks.

---

### Post by xfuzzy on 2013-11-10
EDIT: It is working after reboot, my bad! Thanks a lot, much appreciated! How do I mark the thread as solved? Just rename the title?


Thanks,

sudo modprobe b43 seems to do nothing.  After executing the console seems to stop functioning. I can execute commands, but nothing happens.

Upon reopening of the console iwconfig is still returning:

lo        no wireless extensions.

eth0      no wireless extensions.

---

### Post by mörgæs on 2013-11-10
> **xfuzzy said:**
> EDIT: It is working after reboot, my bad! Thanks a lot, much appreciated! How do I mark the thread as solved? Just rename the title?



Better to use 'thread tools'.

---

### Post by Hadaka on 2013-11-10
Glad it's working !
you are welcome.

---

