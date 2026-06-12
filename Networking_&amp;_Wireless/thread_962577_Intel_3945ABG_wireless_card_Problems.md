---
title: "Intel 3945ABG wireless card Problems"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by Hekerr on 2008-10-29
Okay, after days and days of installing drivers and following HOWTO's I still am unable to work this wireless card.

It's a FS li2735 laptop with the Intel 3945ABG wireless card, which doesn't have the external switch, rather the FN+F1 switch. 

I installed the compat-wireless-2.6-old drivers from the intellinuxwireless website, but I had to keep reinstalling them whenever I started ubuntu and it enabled to see my wireless card and the driver was listed, but couldn't connect to an unprotected university network.

  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

That's it there even with ndiswrapper XP drivers installed and working.

Complete noob@ubuntu so large explanations may be needed.

HeKerr

---

### Post by Hekerr on 2008-10-29
bump4justice

also

netw5x32 : driver installed
	device (8086:4222) present (alternate driver: iwl3945)
w29n51 : driver installed

---

### Post by Hekerr on 2008-10-29
accident

---

### Post by Hekerr on 2008-10-31
hi

ive progressed ans got the drivers do work through ndiswrapper

my only problem now is getting a connection, any tips?

here's some info.

kerr@kerr-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0a:e4:ce:1e:81
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.80.99 latency=0 module=r8169 multicast=yes
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 02
       serial: 00:1f:3c:6d:1c:df
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+netw4x32 driverversion=1.52+Intel,03/13/2008,11.5.1.15 latency=0 module=ndiswrapper multicast=yes wireless=IEEE 802.11g
kerr@kerr-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          RTS thr=1600 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

kerr@kerr-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0a:e4:ce:1e:81  
          inet addr:192.168.80.99  Bcast:192.168.80.255  Mask:255.255.255.0
          inet6 addr: fe80::20a:e4ff:fece:1e81/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1784 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1177675 (1.1 MB)  TX bytes:270812 (264.4 KB)
          Interrupt:220 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1534 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1534 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78165 (76.3 KB)  TX bytes:78165 (76.3 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1f:3c:6d:1c:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:fa000000-fa001000

---

