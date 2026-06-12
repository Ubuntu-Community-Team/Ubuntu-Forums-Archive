---
title: "Wireless not working, button shows wifi (off)"
date: 2016-05-31
forum: Networking &amp; Wireless
---

### Post by Wan_Muhamad_Asyraf on 2016-05-31
Hi

Noob here, As per title this is actually my 2nd installation on the same Laptop,  after I reshuffle my OS, but sadly this time my wireless button is on  the red indicator which means it is off, and I can't turn it on.

Have been on google for a few hours already here is a few details that might be needed :

rfkill list all

> 0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no



Sadly it does not say that my wifi is there :sad:

sudo lshw -C network
>  *-network               
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:39 memory:a0c00000-a0c07fff
  *-network
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: enp4s0
       version: 07
       serial: ec:b1:d7:c1:d8:0a
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list  ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169  driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-1_0.0.1 06/29/12  latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:35 ioport:2000(size=256) memory:a0b00000-a0b00fff memory:a0800000-a0803fff
  *-network
       description: Ethernet interface
       physical id: 1
       logical name: enx3258ca4420cf
       serial: 32:58:ca:44:20:cf
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host  driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.64  link=yes multicast=yes



lspci -nn

> 00:00.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1566]
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc.  [AMD/ATI] Mullins [Radeon R4/R5 Graphics] [1002:9851] (rev 05)
00:01.1 Audio device [0403]: Advanced Micro Devices, Inc. [AMD/ATI] Kabini HDMI/DP Audio [1002:9840]
00:02.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:156b]
00:02.1 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 [1022:1439]
00:02.3 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 [1022:1439]
00:02.4 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 [1022:1439]
00:02.5 PCI bridge [0604]: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 [1022:1439]
00:08.0 Encryption controller [1080]: Advanced Micro Devices, Inc. [AMD] Device [1022:1537]
00:10.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller [1022:7814] (rev 11)
00:11.0 SATA controller [0106]: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] [1022:7804]
00:12.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 39)
00:13.0 USB controller [0c03]: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller [1022:7808] (rev 39)
00:14.0 SMBus [0c05]: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller [1022:780b] (rev 42)
00:14.2 Audio device [0403]: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller [1022:780d] (rev 02)
00:14.3 ISA bridge [0601]: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge [1022:780e] (rev 11)
00:14.7 SD Host controller [0805]: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller [1022:7813] (rev 01)
00:18.0 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1580]
00:18.1 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1581]
00:18.2 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1582]
00:18.3 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1583]
00:18.4 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1584]
00:18.5 Host bridge [0600]: Advanced Micro Devices, Inc. [AMD] Device [1022:1585]
01:00.0 Display controller [0380]: Advanced Micro Devices, Inc.  [AMD/ATI] Sun LE [Radeon HD 8550M / R5 M230] [1002:666f] (rev ff)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136]  (rev 07)
wan632@wan632-HP-15-Notebook-PC:~$ 



---

### Post by chili555 on 2016-05-31
> *-network
description: Network controller
product: BCM43142 802.11b/g/n
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
version: 01
width: 64 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=bcma-pci-bridge latency=0
resources: irq:39 memory:a0c00000-a0c07fffI suggest that you consult the sticky at the top of the forum and install the correct driver for this Broadcom. Post back and tell us if it is then operating correctly.

[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Wan_Muhamad_Asyraf on 2016-06-06
I encountered this error while installing:
probably my hardware is not ditacted??

modprobe: ERROR: could not insert 'wl': Required key not available

---

### Post by wildmanne39 on 2016-06-06
Please look at post 81 at the following link.
[http://ubuntuforums.org/showthread.php?t=2304607&page=9&p=13498349#post13498349](http://ubuntuforums.org/showthread.php?t=2304607&page=9&p=13498349#post13498349)
I have followed the exact same directions with a different driver and it worked perfectly.

---

### Post by chili555 on 2016-06-06
Please see: [http://askubuntu.com/questions/780069/ubuntu-16-04-only-connecting-to-ethernet-no-wifi-option/780095#780095](http://askubuntu.com/questions/780069/ubuntu-16-04-only-connecting-to-ethernet-no-wifi-option/780095#780095)

If you don't want to turn off Secure Boot, you can create a key as described here: [http://ubuntuforums.org/showthread.php?t=2304607&page=9&p=13498349#post13498349](http://ubuntuforums.org/showthread.php?t=2304607&page=9&p=13498349#post13498349) Please note that the post refers to rtl8723be. Your key should reference your driver: wl.

---

### Post by Wan_Muhamad_Asyraf on 2016-06-07
Thanks brother, the solution is turn off secure boot, well it seems like my ubuntu bootmenu suddenly gone, but I can access my wifi, so no issue there.. can access via manual... :)

---

### Post by jeremy31 on 2016-06-07
If you are happy with the results, then use "Thread tools" menu at the top of the page to Mark as solved

---

