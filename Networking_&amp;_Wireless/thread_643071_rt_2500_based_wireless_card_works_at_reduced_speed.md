---
title: "rt 2500 based wireless card works at reduced speed"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by goofybert on 2007-12-17
hello,i installed 7.10 a couple of weeks ago and from the start i had trouble getting my wireless card to work it just didn't wont to connect evantualy i found out that network manager was the problem so i installed wicd and from then off i always have a connection but there is a drawback the card seems to work at a reduced speed normaly i download at an average of 600-700 kB/s but now i'm glad if i get 67kB/s does anyone have an idea how this can be fixed?here is some more info over the card ```
 lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Wireless interface
       product: RT2500 802.11g Cardbus/mini-PCI
       vendor: RaLink
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: wmaster0
       version: 01
       serial: 00:50:fc:8c:5d:75
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=rt2500pci ip=192.168.62.50 latency=32
```
```
iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"WLAN"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:10:A7:2C:4F:46   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Signal level=-66 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
```
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0D:61:ED:78:FC  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:19 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

wlan0     Link encap:Ethernet  HWaddr 00:50:FC:8C:5D:75  
          inet addr:192.168.62.50  Bcast:192.168.62.255  Mask:255.255.255.0
          inet6 addr: fe80::250:fcff:fe8c:5d75/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5470 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5254 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4583623 (4.3 MB)  TX bytes:857091 (837.0 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-50-FC-8C-5D-75-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```i hope someone can help me
ps.: sorry for the spelling mistakes but english is my thirth language

---

### Post by Feenix3k on 2008-07-09
Change the driver to the one that came with your card. The rt2500pci driver only does 802.11b. Blacklist it and install the rt2500.inf from the cd that came with your card. This will give you full use of the card in a/b/g.

---

