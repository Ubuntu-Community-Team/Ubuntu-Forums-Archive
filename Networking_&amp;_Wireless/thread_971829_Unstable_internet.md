---
title: "Unstable internet"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by lhansen on 2008-11-05
Hi. Like many people, I recently upgraded to intrepid and my internet died. My symptoms don't seem to be consistent, and I need some help troubleshooting. I have tried following several other threads, but none seem to have all of these problems.

At first, wireless on my home network worked perfectly. Now it connects, but there appears to be no data transfer (I ping google.com with no response). At first, I could not get an ethernet connection to work on my home router, but now it works perfectly (how I am able to post this). An internet connection at school has not worked since the upgrade. I can connect to the unprotected network, but again there appears to be no data transfer. I cannot establish an ethernet connection at school.

Here is my ifconfig with ethernet at home
```
br0       Link encap:Ethernet  HWaddr 00:12:f0:41:35:22  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe41:3522/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:5853 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1099494 (1.0 MB)  TX bytes:1061438 (1.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:12:f0:41:35:22  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe41:3522/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:43 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:5815 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1353340 (1.3 MB)  TX bytes:165576 (165.5 KB)
          Interrupt:17 Base address:0x2000 Memory:dfdfd000-dfdfdfff 

eth2      Link encap:Ethernet  HWaddr 00:11:43:72:5f:de  
          inet addr:192.168.1.104  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:43ff:fe72:5fde/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:12409 errors:2 dropped:2 overruns:0 frame:0
          TX packets:8692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13345149 (13.3 MB)  TX bytes:1068505 (1.0 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2420 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:310904 (310.9 KB)  TX bytes:310904 (310.9 KB)

tap0      Link encap:Ethernet  HWaddr 0a:e6:95:8b:e6:00  
          inet addr:192.168.187.1  Bcast:192.168.187.255  Mask:255.255.255.0
          inet6 addr: fe80::8e6:95ff:fe8b:e600/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:9215 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


```

Here is my ifconfig with wireless at home
```
br0       Link encap:Ethernet  HWaddr 00:12:f0:41:35:22  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe41:3522/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:5826 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5999 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1094084 (1.0 MB)  TX bytes:1061438 (1.0 MB)

eth1      Link encap:Ethernet  HWaddr 00:12:f0:41:35:22  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe41:3522/64 Scope:Link
          UP BROADCAST RUNNING PROMISC MULTICAST  MTU:1500  Metric:1
          RX packets:91 errors:0 dropped:0 overruns:0 frame:0
          TX packets:39 errors:0 dropped:5815 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1344833 (1.3 MB)  TX bytes:164856 (164.8 KB)
          Interrupt:17 Base address:0x2000 Memory:dfdfd000-dfdfdfff 

eth2      Link encap:Ethernet  HWaddr 00:11:43:72:5f:de  
          inet6 addr: fe80::211:43ff:fe72:5fde/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12378 errors:1 dropped:1 overruns:0 frame:0
          TX packets:8644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13336539 (13.3 MB)  TX bytes:1060262 (1.0 MB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2407 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2407 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:309627 (309.6 KB)  TX bytes:309627 (309.6 KB)

tap0      Link encap:Ethernet  HWaddr 0a:e6:95:8b:e6:00  
          inet addr:192.168.187.1  Bcast:192.168.187.255  Mask:255.255.255.0
          inet6 addr: fe80::8e6:95ff:fe8b:e600/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:9200 overruns:0 carrier:0
          collisions:0 txqueuelen:500 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

and iwconfig
```
lo        no wireless extensions.

eth2      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"noashark"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:EE:0E:00   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-21 dBm  Noise level=-91 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

tap0      no wireless extensions.

br0       no wireless extensions.

```

Here is the relevant line from lspci
```
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG [Calexico2] Network Connection (rev 05)
```

If anyone has any suggestions, it would be greatly appreciated. Thanks.

---

### Post by lhansen on 2008-11-06
A quick update. I let my computer sit with a wireless connection at home for about an hour. At first there was no data transfer, but after an hour everything worked perfectly. Both ifconfig and iwconfig looked the same.

When my computer initially connects and there is no data transfer, there is one interesting piece of evidence. As I watch a conky graph of download rate, I see three very small spikes. These repeat in packets of three indefinitely. After I let the computer sit for an hour, this behavior stops, and the internet works.

Can anyone tell me what is going on?

---

### Post by lhansen on 2008-11-06
Just in case this helps, here is the output of 

lshw -C network

```
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth2
       version: 02
       serial: 00:11:43:72:5f:de
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 latency=64 module=ssb multicast=yes
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       logical name: eth1
       version: 05
       serial: 00:12:f0:41:35:22
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.1.102 latency=64 maxlatency=24 mingnt=3 module=ipw2200 multicast=yes promiscuous=yes wireless=IEEE 802.11g
  *-network:0 DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: f2:f8:df:fa:e6:fb
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
  *-network:1
       description: Ethernet interface
       physical id: 2
       logical name: tap0
       serial: ee:c9:e7:e1:a5:34
       capabilities: ethernet physical
       configuration: broadcast=yes driver=tun driverversion=1.6 firmware=N/A ip=192.168.187.1 multicast=yes
  *-network:2
       description: Ethernet interface
       physical id: 3
       logical name: br0
       serial: 00:12:f0:41:35:22
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A ip=192.168.1.102 multicast=yes

```

---

### Post by superprash2003 on 2008-11-06
what is br0?? br0 and eth1 have same ip!!!do you use all those interfaces?

---

### Post by lhansen on 2008-11-07
The br0 is a bridged interface that I originally setup while configuring an XP virtual machine. In truth I don't really know how the bridged interface works, and I rather get rid of it to avoid confusion. If you have any thoughts on how to remove it that would be great.

---

### Post by superprash2003 on 2008-11-10
just type sudo ifdown br0  .. that should be enough.. have you sorted out the ipconflict..

---

### Post by lhansen on 2008-11-11
That command takes down br0, but it doesn't seem to fix any symptoms. Currently I'm at school having the same problem. I can connect, there appears to be data being downloaded (according to system monitor), but I can't connect or ping anything. My school does have one of those security setups where you are directed to a login page. However, I am never directed there. Firefox just keeps "Looking up" whatever page I sent it to.

---

### Post by superprash2003 on 2008-11-12
it could be a DNS issue... in your terminal type cat /etc/resolv.conf and post output..

---

### Post by lhansen on 2008-11-13
Thanks for your help. I'm not sure how to interpret this output.

```
lhansen@lars:~$ cat /etc/resolv.conf
# Generated by NetworkManager
domain umn.edu
search umn.edu
nameserver 128.101.101.101
nameserver 134.84.84.84

```

---

