---
title: "Can't connect Usb modem on Lubuntu 16.04"
date: 2016-04-29
forum: Networking &amp; Wireless
---

### Post by gopi_nath_vajpai on 2016-04-29
My usb modem is detecting in network manager, however on clicking  connect button, it keeps on going for few minutes and disconnects  thereafter.
  Please see output of various queries below-
  [B]
lsusb:[/B]
  Bus 002 Device 011: ID 12d1:1506 Huawei Technologies Co.,Ltd. Modem/Networkcard
  [B]
wvdial:[/B]

  WvDial: Internet dialer version 1.61
Cannot open /dev/ttyUSB0: Device or resource busy
Cannot open /dev/ttyUSB0: Device or resource busy
Cannot open /dev/ttyUSB0: Device or resource busy  
  
I also tried to install drivers as suggested in many forums, and modeswitch but with no joy. Please see output of   
  [B]
sudo usb_modeswitch -v 0x12d1 -p 0x1506 -M "55534243123456780000000000000011062000000100000000000000000000"[/B]  
  Look for default devices ...
   product ID matched
 Found devices in default mode (1)
Access device 003 on bus 002
Current configuration number is 1
Use interface number 0
Use endpoints 0x02 (out) and 0x82 (in)
Error: can't use storage command in MessageContent with interface 0;
       interface class is 255, expected 8. Abort  

  Please suggest what I might be missing here.
  Regards,

---

