---
title: "[SOLVED] Broadcom works fine but doesn't after reboot"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by be4truth on 2007-12-01
I am running a presario C500 with Gutsy32bit .
The Restricted driver module finds and installs the wireless network without problems. The blue light on the toggle switch goes on and with the help of 'wlassitance' I got online in 1 min. Super!

But as soon as I reboot everything is lost.
here some data. If I type ifconfig -a
I get this. Where is my wlan0? Not listed here but it works.

eth0      Link encap:Ethernet  HWaddr 00:1A:73:0B:C9:BB  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:3 errors:0 dropped:0 overruns:0 frame:0
          TX packets:78 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:180 (180.0 b)  TX bytes:3510 (3.4 KB)
          Interrupt:17 Base address:0x8000 

eth1      Link encap:Ethernet  HWaddr 00:16:D4:A6:83:6C  
          inet addr:192.168.1.10  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fea6:836c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:503 errors:0 dropped:0 overruns:0 frame:0
          TX packets:456 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:751485 (733.8 KB)  TX bytes:36315 (35.4 KB)
          Interrupt:19 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

The lspci command gives this output:

.....
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:08.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

It's there.
I haven't installed niswrapper. 
How do I get this thing to be active after boot? Why is there no wlan0 in the ifconfig output?
Any idea and help highly appreciated.

---

### Post by kevdog on 2007-12-01
Remove the statement:
blacklist bcm43xx
inside the /etc/modprobe.d/blacklist file.

---

### Post by be4truth on 2007-12-01
> **kevdog said:**
> Remove the statement:
blacklist bcm43xx
inside the /etc/modprobe.d/blacklist file.

Did that but after the restart the wireless card there with lspci but its somehow not switched on. 

After adding 'bcm43xx' to /etc/modules it loads it after start-up. 

Thx again for all help received, in this forum and via goodle. Computing is fun with a supportive community.

---

