---
title: "Bluez and RSSI"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by acubino on 2007-03-20
HI. 
I am making some detection test of my devices and their distances.  
I have coded a bash script to retrieve the RSSI, TPL and LQ information, but the values shown are almost random. Sometimes i receive a 0 value, other times a negative or positive. 
 
The hardware i am using: 
- Bluetooth Dongle Conceptronic USB 200 mts 
- Nokia N73 
- Nokia N-Gage QD 
 
The script : 
#!/bin/bash  
sudo hcitool dc $1  
sudo hcitool cc $1  
  
  
sleep 5  
  
sudo hcitool tpl $1  
sudo hcitool lq $1  
sudo hcitool rssi $1  
  
Bluetooth device:  
Bus 001 Device 009: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode) 
 
Thanks.

---

