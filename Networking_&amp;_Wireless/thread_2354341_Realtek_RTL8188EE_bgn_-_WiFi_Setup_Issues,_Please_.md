---
title: "Realtek RTL8188EE b/g/n - WiFi Setup Issues, Please Help!"
date: 2017-03-01
forum: Networking &amp; Wireless
---

### Post by cyberf0rk on 2017-03-01
Hello Linux pros.

First I would like to say I am using Linux for the first time and it has been challenging. I installed Ubuntu 16.04 LTS on Feb 27 2017 and have been productively trouble shooting up until this point.

For the past 2 days now I have been trying to set up WiFi. My laptop has a Realtek RTL8188EE b/g/n Wireless Adapter built in. This adapter seems to have a lot of known issues with Linux. I have been all over Google, Youtube, and Ask Ubuntu/Forums. I have followed thread directions to the best of my abilities downloading files, using links, and command lines with no luck. Most of the threads have been idle for a while so I like I would ask for help to get the topic circulating.

Any answers or references that can be provided will be greatly appreciated.

Thanks[INDENT]
lspci -
[/INDENT]
[INDENT=2]02:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188EE Wireless Network Adapter (rev 01)
[/INDENT]
[INDENT]
lsusb -[/INDENT]
[INDENT=2]Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0c45:651b Microdia 
Bus 001 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

[/INDENT]
[INDENT]
iwconfig -
[/INDENT]
[INDENT=2]lo        no wireless extensions.

enp1s0    no wireless extensions.

wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off

[/INDENT]

---

