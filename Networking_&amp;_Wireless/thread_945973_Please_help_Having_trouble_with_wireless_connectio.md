---
title: "Please help: Having trouble with wireless connection"
date: 2008-10-12
forum: Networking &amp; Wireless
---

### Post by pilgrim_sg on 2008-10-12
Dear all

First of all, please pardon me for my noob question; I am very new to Linux in general.


I using Xubuntu 8.04 (love it!) and I am experiencing difficulties when I try connecting to the Internet through a wireless connection. 

In Windows Vista however, I am able to scan for wireless networks; something that I am unable to do in Xubuntu. 


I have read many threads on how to go about sorting this problem out but I very often end up lost. I do not even know how to start actually. 


From what I gather, typing lshw at the terminal results in:

 description: Wireless interface
                product: PRO/Wireless 3945ABG Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:08:00.0
                logical name: wmaster0
                version: 02
                serial: 00:1f:3c:65:da:d6
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

Typing iwconfig results in:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr: off   Fragment thr=2346 B   
          Power Management: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Other than this, I really do not know what I need to do or how to go about sorting this out so that I am able to surf the Internet wirelessly outside.


Please kindly help and advise me. Thank you so much for your time reading this.

---

