---
title: "karmic koala slow request answer"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by rumca.js on 2009-11-01
Hello.
 

 I am using ubuntu karmic koala (installed through release candidate). After some time spent using this new ubuntu release, updating, downloading programs I developed conviction that something about my wifi connection is not right.
 

 First of all netowrk request answer time was very very long. Even when I wanted to see router setup page I had to wait for 1minute. It is obvious that it should be displayed nearly without any delay.
 

 So I thought to myself that maybe it is a matter of drivers. I configured my own kernel, with Toshiba laptop support drivers in "Processor setup" branch (or something similar).
 I own Toshiba Sattelite A300-1ED.
 After compiling my own kernel network traffic seems to be a little faster. Even though it is not a different kernel (still 2.6.31). Now it is possible to browse the internet.
 

 However the request time speed is not satisfactory. It is faster and if I will once open google or wikipedia page, another page from that domain will open pretty fast.
 

 

 I have static ip. I'm using driver iwl3945
 

 

 **output of ifconfig for wlan0:**
 Link encap:Ethernet  HWaddr 00:1f:3c:8a:45:2a  
           inet addr:192.168.1.13  Bcast:192.168.1.255  Mask:255.255.255.0
           inet6 addr: fe80::21f:3cff:fe8a:452a/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:17965 errors:0 dropped:0 overruns:0 frame:0
           TX packets:16185 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1000
           RX bytes:20072094 (20.0 MB)  TX bytes:2135875 (2.1 MB)
 

 **output of iwconfig**
 wlan0     IEEE 802.11abg  ESSID:"neostrada_97fe"  
           Mode:Managed  Frequency:2.457 GHz  Access Point: 00:16:41:F1:69:87   
           Bit Rate=36 Mb/s   Tx-Power=15 dBm   
           Retry  long limit:7   RTS thr:off   Fragment thr:off
           Power Management:off
           Link Quality=41/70  Signal level=-69 dBm  Noise level=-127 dBm
           Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
           Tx excessive retries:0  Invalid misc:0   Missed beacon:0
 

 

 

 **lshw -html > computer.html**
 id:    
 network
 description:     Wireless interface
 product:     PRO/Wireless 3945ABG [Golan] Network Connection
 vendor:     Intel Corporation
 physical id:     
 0
 bus info:     
 pci@0000:03:00.0
 logical name:     
 wmaster0
 version:     02
 serial:     00:1f:3c:8a:45:2a
 width:     32 bits
 clock:     33MHz
 capabilities:     pm msi pciexpress bus_master cap_list logical ethernet physical wireless
 configuration:    
 broadcast    =    yes
 driver    =    iwl3945
 ip    =    192.168.1.13
 latency    =    0
 multicast    =    yes
 wireless    =    IEEE 802.11abg
 resources:    
 irq    :    30
 memory    :    94200000-94200fff

---

### Post by Rick K on 2009-11-01
Looks to be a [known bug]("https://bugs.launchpad.net/ubuntu/+bug/433972"). The link has a few suggested work arounds.

Hope it helps.

---

