---
title: "Having trouble"
date: 2016-04-17
forum: Networking &amp; Wireless
---

### Post by mohammedmuddinx on 2016-04-17
Hi I recently upgraded to ubuntu but am unable to get online. It works perfectly fine on windows 8/10 but not ubuntu. Im using a hp stream mini desktop. Running 14.04 LTS. It sees the connection by refuses to connect via ethernet. I can get online using wifi only and a network card. Works fine on windows. 
```
*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 0c
       serial: 60:02:92:39:e7:76
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:45 ioport:e000(size=256) memory:f7b00000-f7b00fff memory:f0a00000-f0a03fff
  *-network
       description: Network controller
       product: BCM43142 802.11b/g/n
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=bcma-pci-bridge latency=0
       resources: irq:16 memory:f7a00000-f7a07fff
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@1:4
       logical name: wlan1
       serial: 00:02:72:bb:11:85
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8712u ip=192.168.1.108 multicast=yes wireless=IEEE 802.11bgn

```

Any help  will be appreciated.

---

### Post by $yl9pAR%t on 2016-04-17
Similar problem, look here:

[http://ubuntuforums.org/showthread.php?t=2318953](http://ubuntuforums.org/showthread.php?t=2318953)

---

### Post by mohammedmuddinx on 2016-04-17
Hi this didnt solve my issue.

---

### Post by Hadaka on 2016-04-17
Hi from a working wired connection,please do
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe -v wl
```
boot and test wireless..
if it fails..then please open a terminal ctrl/alt/t then Copy and paste the following command and press enter.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
This command writes a file to your home directory.The file name is wireless-info.txt
Next.
From your directory please copy,paste and post the wireless-info.txt
thanks.

---

### Post by Hadaka on 2016-04-17
Hi , I re-read your post and saw this ..
```
 "I can get online using wifi only" 
```
So let's use the offline no internet method to load the correct wifi dirver,
---No Internet Required---  You must have the USB or DVD that you used to install Ubuntu ---

open a terminal..ctrl/alt/t.. and do..
*Ignore any errors or file not found
```
sudo apt-get remove --purge firmware-b43-installer
```
Next..Insert the USB or DVD and do..
```
cp /media/*/pool/main/d/dkms/*.deb dk.deb
cp /media/*/pool/restricted/b/bcmwl/*.deb wl.deb
sudo dpkg -i *.deb
sudo modprobe -v wl
```
This method also here ->> [http://ubuntuforums.org/showthread.php?t=2316986](http://ubuntuforums.org/showthread.php?t=2316986)

---

### Post by mohammedmuddinx on 2016-04-20
Thank you so much that worked.

---

### Post by Hadaka on 2016-04-20
Great ! glad its working, please go to your first post
of this thread, click Thread Tools and choose Solved.
this will mark your thread SOLVED and help other searchers.
thanks.

---

