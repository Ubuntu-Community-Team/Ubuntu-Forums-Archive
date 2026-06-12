---
title: "usb_modeswitch and Netgear AC327U 3G USB dongle"
date: 2014-10-27
forum: Networking &amp; Wireless
---

### Post by debraj.dutta on 2014-10-27
usb_modeswitch detects Netgear AC327U USB stick as 2077:f000 , but does not switch to modem mode . 

My laptop is running Ubuntu 14.04 9 Kylin .

Output of lsusb :

===
raja@raja-Lenovo-G510:~$ lsusb
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 003 Device 003: ID 105b:e065  
Bus 003 Device 009: ID 2077:f000  
Bus 003 Device 002: ID 174f:114f Syntek 
Bus 003 Device 006: ID 12d1:1436 Huawei Technologies Co., Ltd. E173 3G Modem (modem-mode)
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
===

Content of /usr/share/usb_modeswitch/2077:f000
===
# Netgear AC327U


DefaultVendor=0x2077
DefaultProduct=0xf000
TargetVendor=0x2077
TargetProduct= 0xa003
#TargetClass=    not set
#TargetProductList=""


#MessageEndpoint=0x03
MessageContent="55534243204C55890000000000000600000000000000000000000000000000"

===

Manual switching attempt outputs :
===
raja@raja-Lenovo-G510:~$ sudo usb_modeswitch -c  /usr/share/usb_modeswitch/2077:f000Look for target devices ...
 No devices in target mode or class found
Look for default devices ...
   product ID matched
 Found devices in default mode (1)
Access device 009 on bus 003
Current configuration number is 1
Use interface number 0
Use endpoints 0x01 (out) and 0x81 (in)


USB description data (for identification)
-------------------------
Manufacturer:   
     Product: Netgear Aircard 3G USB Modem
  Serial No.: 1234567890ABCDEF
-------------------------
Looking for active driver ...
 No active driver found. Detached before or never attached
Set up interface 0
Use endpoint 0x01 for message sending ...
Trying to send message 1 to endpoint 0x01 ...
 OK, message successfully sent
Reset response endpoint 0x81
Reset message endpoint 0x01
-> Run lsusb to note any changes. Bye!
===

After all this , no change in lsusb output , and device does not appear in network manager for new connection .



Any help appreciated .

---

