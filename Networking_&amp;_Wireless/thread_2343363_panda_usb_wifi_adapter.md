---
title: "panda usb wifi adapter"
date: 2016-11-15
forum: Networking &amp; Wireless
---

### Post by garyed on 2016-11-15
I'm wondering if anyone has any info on this wifi adapter for my laptop with Ubuntu 14.04.  It says its supported by Ubuntu. One is model Panda PAU03  & the other is PAU05 so i plan on getting one of them.
I went through a lot of trouble getting the original broadcom internal wireless working in Ubuntu but it has never been reliable. I finally decided there is something wrong with the internal wireless card because it has the same problems when I dual boot into Windows.
Any info appreciated

---

### Post by garyed on 2016-11-19
Well I haven't gotten any replies but just wanted to post that I got the PAU05 &  I think it works without any drivers at all. I'm not sure how to tell what's going on because now both internal & external wireless show up in ifconfig & iwconfig but my wifi seems to be working better.

---

### Post by jeremy31 on 2016-11-19
Post results for ```
lspci -nnk | grep -iA2 net; lsusb
```
Then we can figure out how to disable the internal card

---

### Post by garyed on 2016-11-20
~$ lspci -nnk|grep -iA2 net; lsusb
07:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lite-On Communications Inc BCM43142 802.11b/g/n [11ad:6655]
	Kernel driver in use: wl
--
08:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 07)
	Subsystem: Toshiba America Info Systems RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [1179:f840]
	Kernel driver in use: r8169
	Kernel modules: r8169
Bus 001 Device 002: ID 8087:8001 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 002 Device 004: ID 04f2:b446 Chicony Electronics Co., Ltd 
Bus 002 Device 003: ID 0930:0225 Toshiba Corp. 
Bus 002 Device 002: ID 04f3:20d8 Elan Microelectronics Corp. 
Bus 002 Device 005: ID 148f:5372 Ralink Technology, Corp. RT5372 Wireless Adapter
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by jeremy31 on 2016-11-20
This should work ```
 sudo apt-get remove bcmwl-kernel-source
echo "blacklist b43" | sudo tee /etc/modprobe.d/b43.conf
```
Reboot

---

### Post by garyed on 2016-11-20
I appreciate the help but I'm a little nervous about getting rid of the bcmwl-kernel-source since it took me so long to get the internal wireless to even work.
At least if I forget or lose the usb I'll still have the internal wireless though not very dependable. 
Could I just do the blacklist thing without deleting the internal drivers? Would that still keep the internal wireless from being used? That way it would be easy to reverse if needed.
Right now without doing anything except plugging in the usb wireless adapter things seem to be working well & whatever conflicts there might be don't seem bad. I think the usb is taking over because I can see the little light flashing whenever anything is being downloaded or even accessing a site.

---

### Post by jeremy31 on 2016-11-20
You may find that this will work
```
echo "blacklist wl" | sudo tee /etc/modprobe.d/wl.conf
```
Reboot
And if you do happen to need it
```
sudo modprobe wl
```

---

### Post by garyed on 2016-11-20
Thanks, that's exactly what I needed.

---

