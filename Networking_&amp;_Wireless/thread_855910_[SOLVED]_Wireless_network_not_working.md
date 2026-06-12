---
title: "[SOLVED] Wireless network not working"
date: 2008-07-10
forum: Networking &amp; Wireless
---

### Post by acreech on 2008-07-10
Like many others, my wireless network is not working and the suggestions I've tried from other posts have not worked yet.
System is: Acer Aspire 7520-5185
AMD Athlon 64 X 2 Dual-Core processor
NVIDIA GeForce 7000M

First network card was Antheros AR5BXB63
  The restricted drivers were automatically loaded for it and I enabled them, but under the nm-applet there were never any networks available to try and connect to even though my home network was up and available on my Windows Vista laptop.  Also under System/Administration/Network there is not a wireless selection.

Since several posts indicated that Intel based wireless cards work out of the box I replaced my network card with:

2nd network card: Intel 3945ABG
This card was not detected at all.  After running: sudo modprobe iwl3945
The card now shows up in dmesg, but under System/Administration/Network there is not a wireless selection. and under the nm-applet there still is not any networks detected to try and connect to.

Unlike some of the other posts: wireless has never worked on the 3 separate installs of Hardy Heron Ubuntu 8.04 on two different hard drives using this laptop.

```
dmesg | grep iw
lsmod | grep 3945
sudo modprobe iwl3945
lsmod | grep 3945
```
iwl3945               100468  0 
iwlwifi_mac80211      251876  1 iwl3945
```
dmesg | grep iw
```
[  150.965161] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.0
[  150.965168] iwl3945: Copyright(c) 2003-2007 Intel Corporation

```
lspci
```
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7000M (rev a2) (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:04.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:04.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:04.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:04.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:04.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)


```
iwlist scan
```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.


```
modinfo iwl3945
```
filename:       /lib/modules/2.6.24-19-generic/ubuntu/wireless/iwlwifi/iwlwifi/compatible/iwl3945.ko
license:        GPL
author:         Copyright(c) 2003-2007 Intel Corporation
version:        1.2.0
description:    Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux
srcversion:     8E95C617988943846696F97
alias:          pci:v00008086d00004227sv*sd*bc*sc*i*
alias:          pci:v00008086d00004222sv*sd*bc*sc*i*
depends:        iwlwifi_mac80211
vermagic:       2.6.24-19-generic SMP mod_unload 
parm:           antenna:select antenna (1=Main, 2=Aux, default 0 [both]) (int)
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           hwcrypto:using hardware crypto engine (default 0 [software])
 (int)
parm:           debug:debug output mask (int)
parm:           disable_hw_scan:disable hardware scanning (default 0) (int)
parm:           queues_num:number of hw queues. (int)
parm:           qos_enable:enable all QoS functionality (int)


```
iwconfig
```
lo        no wireless extensions.

eth0      no wireless extensions.


```
lshw -C network
```
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:c8:1c:d2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.1.106 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes

---

### Post by chili555 on 2008-07-11
The fact that the card doesn't show up at all in either *lspci* or *lshw* suggests the card is either defective or not installed correctly. Even if the wireless switch or key combination was switched 'off' the card would still appear. The listings in *dmesg* and *lsmod* simply reflect that the modules inserted without error; not that any device associated with the modules. Compare to my *dmesg | grep iw*:```
chili@LAPTOP60:~$ dmesg | grep iw
[   28.480605] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, 1.2.25
[   28.480611] iwl3945: Copyright(c) 2003-2007 Intel Corporation
[   28.480801] iwl3945: Detected Intel PRO/Wireless 3945ABG Network Connection
[   28.542673] wmaster0: Selected rate control algorithm 'iwl-3945-rs'
[   34.774192] iwl3945: Tunable channels: 11 802.11bg, 13 802.11a channels
[   34.777289] Registered led device: iwl-phy0:RX
[   34.777321] Registered led device: iwl-phy0:TX
```Mine detects the device, however yours simply reports the module was inserted.

---

### Post by mybeat on 2008-07-11
Have you installed iwlwifi-firmware for Intel 3945ABG?

---

### Post by Heartless kid on 2008-07-11
i got the same problem but mine vanished after download from update manager so i need help

---

### Post by acreech on 2008-07-11
> **mybeat said:**
> Have you installed iwlwifi-firmware for Intel 3945ABG?

Can you give the steps to install the iwlwifi-firmware. I have installed drivers, but not firmware. 

Thanks

---

### Post by mybeat on 2008-07-12
> **acreech said:**
> Can you give the steps to install the iwlwifi-firmware. I have installed drivers, but not firmware. 

Thanks

sudo apt-get install iwlwifi-firmware

---

### Post by Marouf on 2008-07-19
same problem here. I have an Acer Aspire 7520-5185.  I could have sworn that the wireless card showed up when I had the Live CD in. Now. I get nothing.. only the wired network works. This might be more then a hardware malfunction on the laptop? Was anyone able to get it to work yet? 

Thanks

---

### Post by acreech on 2008-07-27
I have not gotten my wireless card to work yet. I have tried the command 

to get the firmware and that did not work.

---

### Post by acreech on 2008-08-06
> **acreech said:**
> I have not gotten my wireless card to work yet. I have tried the command 

to get the firmware and that did not work.

I have re-installed my Atheros Card which works fine on Windows Vista. I ran

> 
lshw -C network


and got the following

> 
  *-network               
       description: Ethernet interface
       product: MCP67 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: a2
       serial: 00:1b:38:c8:1c:d2
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=forcedeth driverversion=0.61 ip=192.168.0.64 latency=0 maxlatency=20 mingnt=1 module=forcedeth multicast=yes
  *-network UNCLAIMED
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0


Under network settings my wireless does not show up. How do I get my computer to connect to this wireless network card?

---

### Post by acreech on 2008-08-19
I finally got my Atheros ar5007eg card to work by installing the 32 bit system. and then running the following commands:

> 
sudo -s
echo 'blacklist ath_pci' >> /etc/modprobe.d/blacklist
apt-get install ndiswrapper*
wget [ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip](ftp://ftp.work.acer-euro.com/notebook/aspire_4710/driver/Wireless_Atheros.zip)
unzip Wireless*
cd Atheros
unzip HR*
ndiswrapper -i net5211.inf
echo 'ndiswrapper' >> /etc/modules



Then reboot and it should work. 

check this forum to see the history:    
> []("http://ubuntuforums.org/showthread.php?p=5617842#post5617842")

[http://ubuntuforums.org/showthread.php?p=5617842#post5617842]("http://ubuntuforums.org/showthread.php?p=5617842#post5617842")

---

