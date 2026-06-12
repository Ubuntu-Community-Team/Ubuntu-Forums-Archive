---
title: "WIFI disconnect issue in ubuntu 13.10"
date: 2015-05-08
forum: Networking &amp; Wireless
---

### Post by chamara2 on 2015-05-08
HI,  


I have been facing regular WIFI disconnect in my Laptop.  Below are the details. Is there any know WIFI disconnecting issues for Ubuntu 13.10.



1) Kernel version ->  3.11.0-18-generic



2) WIFI driver version



description: Wireless interface

       product: Centrino Advanced-N 6205 [Taylor Peak]

       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 84:3a:4b:20:26:26
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.11.0-18-generic firmware=18.168.6.1 ip=10.100.0.44 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
       resources: irq:47 memory:f3000000-f3001fff




3)  Output of **iwconfig** command



eth0      no wireless extensions.


lo        no wireless extensions.


wlan0     IEEE 802.11abgn  ESSID:"WSO2"  
          Mode:Managed  Frequency:5.28 GHz  Access Point: 88:1D:FC:A1:57:EF   
          Bit Rate=65 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0

          Tx excessive retries:4783  Invalid misc:100   Missed beacon:0


Feedback is appreciated.

Regards,
Chamara

---

### Post by ajgreeny on 2015-05-08
13.10 is now out of support, so even if I could help you with suggestions, it would be just about impossible to carry out any actions needed to get you up and running.

I suggest you either upgrade to, or do a clean install of 14.04.

---

### Post by chamara2 on 2015-05-08
agreed. Will do the 14.04 Upgrade and see.

Thank You,

---

