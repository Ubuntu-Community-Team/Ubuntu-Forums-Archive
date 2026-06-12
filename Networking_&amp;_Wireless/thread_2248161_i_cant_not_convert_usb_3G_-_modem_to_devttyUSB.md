---
title: "i cant not convert usb 3G - modem to /dev/ttyUSB*"
date: 2014-10-12
forum: Networking &amp; Wireless
---

### Post by quocdatbk on 2014-10-12
i have usb-3G modem, it have id 12d1:14b5 and i want to use it with linux device. 
i use usb_mode switch sucessfull 
lsusb : id usb_3g change to 12d1:14a8 but kernel cannot creat /dev/ttyUSB*
i modify /linux/drivers/usb/serial/option.c and recompile kernel , thi solution cant creat /dev/ttyUSB* but i don't want recompile kernel. 
how to convert device to /dev/ttyUSB* and don't need recompile kernel? please, help me!

---

