---
title: "lucid 10.04"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by jrev on 2011-05-10
Hi, 
By which command do I know if my wifi driver is active ? 

I have a laptop that connects immediately to my Freebox wifi after the boot

The other laptop doesn't connect also the network manager has the same configuration 

Help !

Thanks :p

---

### Post by BrandonC19 on 2011-05-10
If you're looking to check whether your wifi is actually working, try the command ```
ifconfig wlan0
```):P

---

### Post by jrev on 2011-05-11
Here is the answer :
[B]
jean@debian:~$ ifconfig wlan0[/B]
wlan0     Link encap:Ethernet  HWaddr 00:00:00:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          Packets reçus:0 erreurs:0 :0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 lg file transmission:1000 
          Octets reçus:0 (0.0 B) Octets transmis:0 (0.0 B)
          Interruption:17

the wifi  doesnt work.

Why ?

---

### Post by Redblade20XX on 2011-05-11
Post output: 
lspci | grep Network

---

### Post by jrev on 2011-05-11
The output is :

jean@debian:~$ lspci|grep network
jean@debian:~$ 
jean@debian:~$ lspci | grep network
jean@debian:~$ sudo su
[sudo] password for jean: 
root@debian:/home/jean# lspci | grep network
root@debian:/home/jean#

---

### Post by jramshu on 2011-05-11
Try

```
lspci -k
``` That will list the drivers too.

EDIT: My output for my wifi looks like this;

```
02:00.0 Network controller: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Hewlett-Packard Company Device 1381
    **Kernel driver in use: ath9k**
    Kernel modules: ath9k
```

---

### Post by jrev on 2011-05-11
jean@debian:~$ lspci -k
00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge
	Kernel driver in use: agpgart-intel
	Kernel modules: intel-agp
00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller
	Kernel driver in use: i915
	Kernel modules: i915
00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
	Kernel driver in use: uhci_hcd
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02)
	Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02)
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
	Kernel modules: i2c-i801
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 04)
	Kernel driver in use: r8169
	Kernel modules: r8169
01:00.1 Class ff00: Realtek Semiconductor Co., Ltd. Device 5288 (rev 01)
02:00.0 [B]Network controller: RaLink RT3090 Wireless 802.11n 1T/1R PCIe
	Kernel driver in use: rt3090
	Kernel modules: rt3090sta[/B]

So we know now which module is concerned ...

---

### Post by jramshu on 2011-05-11
Dang, I just did something really stupid. I was looking back at this thread and saw that his hardware didn't show a mac address. So I decide to see if I get the same results and I reach down and hit ctrl+alt+t, nothing happened. So I do it a couple more times, nothing. Then I realize I have windows booted up. 

Had to laugh at myself. :lolflag:           =D>

---

### Post by jrev on 2011-05-12
Ifound the driver at the following address :
[http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/pool/main/r/rt3090/](http://ppa.launchpad.net/markus-tisoft/rt3090/ubuntu/pool/main/r/rt3090/)
on the fourth line

The wifi runs fine !

---

