---
title: "pppoeconf not detecting my server"
date: 2009-08-30
forum: New to Ubuntu
---

### Post by sksriharsha on 2009-08-30
Hi,
I just installed ubuntu 8.04 on my PC. I also have XP running on it. 
I am not able to connect to internet. My ISP uses DHCP and XP is able to connect to it.
I have tried pppoeconf, but it is not ble to access my server.

---

### Post by halitech on 2009-08-30
do you have a router or is it a direct connection?

---

### Post by sksriharsha on 2009-08-30
It is a direct connection to my LAN Card

---

### Post by halitech on 2009-08-30
on the windows side, do you use ppoe to connect? Does the NIC show up in LSPCI?

---

### Post by sksriharsha on 2009-08-30
On the Windows side I  created a new network connection as pppoe WAN Miniport.
 
I  connect to internet by double clicking on the Icon provided. My username, Password is asked and I am then connected.

---

### Post by halitech on 2009-08-30
ok, open a terminal and run
```
lspci
```and post the results here

---

### Post by sksriharsha on 2009-08-30
How to post the results ?

---

### Post by sksriharsha on 2009-08-30
OK I managed that. Here Goes
 
> 00:00.0 Host bridge: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
01:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

---

### Post by halitech on 2009-08-30
ok, its at least seeing the NIC. what about
```
sudo ifconfig
```

---

### Post by sksriharsha on 2009-08-30
ifconfig says
 
> eth0 Link encap:Ethernet HWaddr 00:21:97:7a:1a:51 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:20 Base address:0xe800 
 
lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:50 errors:0 dropped:0 overruns:0 frame:0
TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:2884 (2.8 KB) TX bytes:2884 (2.8 KB)

---

### Post by halitech on 2009-08-30
what happens when you try to use pppoeconf?

---

### Post by sksriharsha on 2009-08-30
On trying pppoeconf, it goes through the whole process and says at the end that 
"the access concentrator of your server is not responding. Cable connections might be wrong or some other PPPoe client is using the network at the same time".

---

### Post by halitech on 2009-08-30
will the network manager connect to it? Found some saying 9.04 should work out of the box using the Gnome Network manager so might be worth updating to 9.04

---

### Post by sksriharsha on 2009-09-15
I have now loaded UBUNTU 9.04
But same problem exists.

---

