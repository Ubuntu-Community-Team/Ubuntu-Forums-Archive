---
title: "Wireless Woes"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by brandon moore on 2007-01-04
I'm having some problems getting wireless up with this bcm4318 card on my Gateway MX6424. I feel like I'm really, REALLY close to getting it, but my wireless card doesn't show up in System > Administration > Networking. Here is the output of 'ndiswrapper -l':

> 
brandon@brandon-laptop:~$ ndiswrapper -l
Installed drivers:
bcmwl5 driver installed, hardware present


Here is my /etc/network:
> 
auto lo
iface lo inet loopback

iface eth0 inet dhcp
wireless-essid MooreWireless
wireless-key sxxxxxx

auto eth1
iface eth1 inet dhcp


Here is my 'lspci | grep Broadcom\ Corporation'

> 
brandon@brandon-laptop:~$ lspci | grep Broadcom\ Corporation
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)


Here is my /etc/modprobe.d/ndiswrapper

> 
alias eth0 ndiswrapper


Here is my /etc/modules

> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
rtc
sbp2
ndiswrapper


Is there any other info that would be helpful? I can't get access to my eth0 (which is my wireless card).

> 
brandon@brandon-laptop:~$ sudo ifconfig eth0 up
eth0: ERROR while getting interface flags: No such device


Any help is appreciated!

---

### Post by spd106 on 2007-01-04
Try **lsmod | grep ndis**

If there's no ndiswrapper loaded, do **sudo depmod**, then **sudo modprobe ndiswrapper**.

Also check **dmesg | grep ndis**

---

### Post by brandon moore on 2007-01-04
> **spd106 said:**
> Try **lsmod | grep ndis**

If there's no ndiswrapper loaded, do **sudo depmod**, then **sudo modprobe ndiswrapper**.

Also check **dmesg | grep ndis**

Thanks for the help... here's what I got.

> brandon@brandon-laptop:~$ sudo depmod
Password:
brandon@brandon-laptop:~$ sudo modprobe ndiswrapper
brandon@brandon-laptop:~$ dmesg | grep ndis
[   36.037674] ndiswrapper version 1.22 loaded (preempt=no,smp=yes)
[   36.122453] ndiswrapper (load_pe_images:573): fixing KI_USER_SHARED_DATA address in the driver
[   36.123638] ndiswrapper: driver bcmwl5 (Broadcom,02/11/2005, 3.100.64.0) loaded
[   36.131471] ndiswrapper (NdisWriteErrorLogEntry:241): log: 34ED99B0, count: 1, return_address: ffffffff8830a13e
[   36.131478] ndiswrapper (NdisWriteErrorLogEntry:244): code: 267
[   36.131548] ndiswrapper (miniport_init:264): couldn't initialize device: C0000001
[   36.131556] ndiswrapper (pnp_start_device:428): Windows driver couldn't initialize the device (C0000001)
[   36.131576] ndiswrapper (miniport_halt:327): device ffff810033d44500 is not initialized - not halting
[   36.131588] ndiswrapper: device eth%d removed
[   36.131616] ndiswrapper: probe of 0000:05:02.0 failed with error -22


---

### Post by spd106 on 2007-01-04
Ok, you have two options really.

(1) Find a different, more up to date driver. Perhaps from the device manufacturers website or try the list on the ndiswrapper website. Then install it with ndiswrapper, after removing the old driver.

(2) Try downloading the newest ndiswrapper and building it manually. You will also need to install the build-essential package. There is a guide in the wiki/help docs

Start with (1) first, then report back before starting on (2).

---

