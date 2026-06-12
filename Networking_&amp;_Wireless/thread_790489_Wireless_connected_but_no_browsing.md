---
title: "Wireless connected but no browsing"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by Madmagnum on 2008-05-11
Alright first time Ubuntu user, but long time Linux user.

I have the default 8.04 install and am working on my wireless card.  I can get it up and connected but cannot get my browser to work.

My ifconfig shows an address.
I can ping servers.
I can browse to my router and a few sites (unbuntu, google), however general browsing loads maybe the title and then stalls. After a minute or 2 I get network timeouts.  I can still ping sites through when this happens.
I've tried changing DNS servers to no avail.  Any hints on this topic?

---

### Post by Madmagnum on 2008-05-11
bump with additional info (got wired working, still same probs with wireless).

Card: Intel 2200G

ifconfig:
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:76:61:c5  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::2c0:9fff:fe76:61c5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2615 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2226193 (2.1 MB)  TX bytes:360285 (351.8 KB)
          Interrupt:18 Base address:0x3000 

eth1      Link encap:Ethernet  HWaddr 00:0e:35:c6:fa:ac  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Base address:0x6000 Memory:e0206000-e0206fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1572 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1572 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:78600 (76.7 KB)  TX bytes:78600 (76.7 KB)

robert@robert-laptop:~$ netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 eth1
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth1
0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 eth0

robert@robert-laptop:~$ dmesg | grep 2200
[   34.544850] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.2.2kmprq
[   34.544855] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[   34.879995] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[   37.677300] ipw2200: Radio Frequency Kill Switch is On:
[   37.746776] ipw2200: Detected geography ZZM (11 802.11bg channels, 0 802.11a

---

### Post by superprash2003 on 2008-05-11
have you tried opendns servers?

---

### Post by Madmagnum on 2008-05-12
yes I have.  

turns out its not the kill switch.....

---

### Post by superprash2003 on 2008-05-12
can you post your iwconfig output

---

### Post by Madmagnum on 2008-05-12
eth1      IEEE 802.11g  ESSID:"groffmynet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:94:60:CB   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=100/100  Signal level=-20 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:2

Also it is not the kill switch I think, it acutally works, I can turn the power on and off iff nessecary.  COnfirmed it with iwconfig, but still having network issues.

Here's my nameservers:
208.67.220.220
208.67.222.222
68.238.96.12
68.238.138.12

---

### Post by kindofabuzz on 2008-05-12
> **Madmagnum said:**
> yes I have.  

I think after so0me searching it has to do with the kill switch.  Unofrtunatly it appears my switch is not functioning under Ubuntu.  Now the problem is how to turn on wireless from the laptop.  I have a single key that does it, but its not functional at all in Ubuntu.

like a switch on the wireless card itself?  i heard that only works if you use ndiswrapper and the manufacture drivers.

---

### Post by Madmagnum on 2008-05-12
No the killswitch is definitly working.  I can see the change with iwconfig.  I've read a couple of other posts with the same problem (connected but no web) and no resolution  yet.

As a check i disabled security and tried to connect.  That was no improvement.  I can connect to my router fine with encryption on and off.  I am really confused as to what is happening.

---

### Post by Madmagnum on 2008-05-12
ANother (hopefully) helpful info:
 *-network:0             
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:76:61:c5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 6
       bus info: pci@0000:02:06.0
       logical name: eth1
       version: 05
       serial: 00:0e:35:c6:fa:ac
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.101 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=IEEE 802.11g

---

### Post by Madmagnum on 2008-05-13
*bump*
anyone out there got any suggestions?

---

