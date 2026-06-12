---
title: "Network"
date: 2009-10-05
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-10-05
Out of the blue, the Dell D610 that I use for my weather station monitoring and is used for sharing my printer on our home intra net has stopped using wireless. I tried deleting NetworkManager and installing WICD..but still it refuses to talk....I can set up and use a wired connection, but not wireless.

Here are some details

pj@pj-weather:~$ iwconfig 
lo        no wireless extensions. 

eth0      no wireless extensions. 

eth1      unassociated  ESSID:"DLINK"  
          Mode:Managed  Frequency=2.462 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off 
          Power Management:off 
          Link Quality:0  Signal level:0  Noise level:0 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0 

pan0      no wireless extensions. 

pj@pj-weather:~$ ethtool -i eth0 
driver: tg3 
version: 3.94 
firmware-version: 5751-v3.29a 
bus-info: 0000:02:00.0 

Any help would be greatly appreciated.

---

### Post by dunbrokin on 2009-10-06
Wicd will not even detect my wireless network....I am beginning to suspect that my wireless card is cooked......how do I work out if my wireless card is cooked?

---

### Post by mapes12 on 2009-10-06
> **dunbrokin said:**
> Wicd will not even detect my wireless network....I am beginning to suspect that my wireless card is cooked......how do I work out if my wireless card is cooked?Does ```
lspci
``` find it? Or ```
lsusb
``` if it's a USB device.

---

### Post by dunbrokin on 2009-10-06
pj@pj-weather:~$ lspci 
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03) 
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03) 
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) 
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) 
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) 
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) 
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) 
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) 
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3) 
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03) 
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03) 
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03) 
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03) 
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300] 
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express (rev 01) 
03:01.0 CardBus bridge: Texas Instruments PCI6515 Cardbus Controller 
03:01.5 Communication controller: Texas Instruments PCI6515 SmartCard Controller 
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05) 
pj@pj-weather:~$ 

It seems to have found it OK......

---

### Post by dunbrokin on 2009-10-06
Not sure if this helps or not?!?


> Oct  5 09:04:00 pj-weather kernel: [   26.409652] ADDRCONF(NETDEV_UP): eth0: link is not ready 
Oct  5 09:17:34 pj-weather kernel: [  840.946118] ipw2200: Firmware error detected.  Restarting. 
Oct  5 09:19:12 pj-weather kernel: [  938.676504] ipw2200: Firmware error detected.  Restarting. 
Oct  5 09:19:29 pj-weather kernel: [  955.890954] ipw2200: Firmware error detected.  Restarting. 
Oct  5 09:19:52 pj-weather kernel: [  978.637638] ipw2200: Firmware error detected.  Restarting. 
Oct  5 09:20:31 pj-weather kernel: [ 1017.776141] ipw2200: Firmware error detected.  Restarting. 
Oct  5 09:24:32 pj-weather kernel: [ 1258.449989] ipw2200: Firmware error detected.  Restarting. 
Oct  5 09:26:48 pj-weather kernel: [ 1394.911247] ipw2200: Firmware error detected.  Restarting. 
Oct  5 09:28:41 pj-weather kernel: [ 1507.268852] ipw2200: Firmware error detected.  Restarting.

> ct  6 14:44:12 pj-weather kernel: [ 1749.602003] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:44:12 pj-weather kernel: [ 1749.890262] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:44:13 pj-weather kernel: [ 1750.599738] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready 
Oct  6 14:45:00 pj-weather kernel: [ 1798.015534] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:45:00 pj-weather kernel: [ 1798.160223] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:45:02 pj-weather kernel: [ 1799.403426] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready 
Oct  6 14:45:12 pj-weather kernel: [ 1809.625064] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:45:12 pj-weather kernel: [ 1809.888939] ADDRCONF(NETDEV_UP): eth0: link is not ready 
Oct  6 14:46:42 pj-weather kernel: [ 1899.780253] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:46:43 pj-weather kernel: [ 1900.973977] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready 
Oct  6 14:47:28 pj-weather kernel: [ 1945.951250] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:47:28 pj-weather kernel: [ 1946.003490] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:47:29 pj-weather kernel: [ 1947.034279] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready 
Oct  6 14:48:16 pj-weather kernel: [ 1993.657849] ttyS0: 1 input overrun(s) 
Oct  6 14:49:57 pj-weather kernel: [ 2094.573006] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:49:57 pj-weather kernel: [ 2094.644059] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:50:16 pj-weather kernel: [ 2113.488151] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:50:24 pj-weather kernel: [ 2121.614648] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:50:35 pj-weather kernel: [ 2132.666233] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:50:35 pj-weather kernel: [ 2132.718332] ipw2200: Attempt to set invalid wireless mode: 142552000 
Oct  6 14:50:35 pj-weather kernel: [ 2132.718357] ipw2200: Attempt to set invalid wireless mode: 142552000 
Oct  6 14:50:35 pj-weather kernel: [ 2132.718376] ipw2200: Attempt to set invalid wireless mode: 142552000 
Oct  6 14:50:35 pj-weather kernel: [ 2132.718394] ipw2200: Attempt to set invalid wireless mode: 142552000 
Oct  6 14:51:29 pj-weather kernel: [ 2187.047525] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:51:29 pj-weather kernel: [ 2187.110773] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:51:42 pj-weather kernel: [ 2200.296970] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:53:00 pj-weather kernel: [ 2277.967702] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:53:01 pj-weather kernel: [ 2278.799624] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready 
Oct  6 14:53:22 pj-weather kernel: [ 2300.063210] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:53:23 pj-weather kernel: [ 2301.202016] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready 
Oct  6 14:54:24 pj-weather kernel: [ 2362.234994] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:55:07 pj-weather kernel: [ 2405.342206] ADDRCONF(NETDEV_UP): eth1: link is not ready 
Oct  6 14:55:08 pj-weather kernel: [ 2405.557089] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready 
Oct  6 14:56:38 pj-weather kernel: [ 2495.806740] tg3: eth0: Link is up at 100 Mbps, full duplex. 
Oct  6 14:56:38 pj-weather kernel: [ 2495.806747] tg3: eth0: Flow control is on for TX and on for RX. 
Oct  6 14:56:38 pj-weather kernel: [ 2495.809153] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
Oct  6 14:57:02 pj-weather kernel: [ 2520.105562] ADDRCONF(NETDEV_UP): eth0: link is not ready

---

### Post by dunbrokin on 2009-10-07
Bump

---

### Post by Iowan on 2009-10-07
Probably the same information, but try **lshw -C network**.

---

### Post by dunbrokin on 2009-10-07
pj@pj-weather:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:12:3f:10:d2:75
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.94 firmware=5751-v3.29a ip=10.1.1.7 latency=0 module=tg3 multicast=yes
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:95:49:5b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: b6:6d:ee:2b:cc:9e
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by dunbrokin on 2009-10-08
Solve4d - new update

---

### Post by Papa-san on 2009-12-26
So,
How was it solved?

---

### Post by dunbrokin on 2009-12-26
A new update of the Network Manager (I presume) under 9.10 caused the problem to disapear.

---

