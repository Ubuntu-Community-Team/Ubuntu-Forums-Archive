---
title: "Can not deteced USB Modem?"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by brotin on 2008-04-18
My Modem is Prolink 1456U USB. My ubuntu 7.10 is not deteced this modem. i also tried by modem deteced program. but i did't get any good result.

Please help me for make this problem solve.

---

### Post by Paris Heng on 2008-04-18
> **brotin said:**
> My Modem is Prolink 1456U USB. My ubuntu 7.10 is not deteced this modem. i also tried by modem deteced program. but i did't get any good result.

Please help me for make this problem solve.


How did you actually connect from the Prolink to your Ubuntu? Wireless? LAN?

---

### Post by dstew on 2008-04-18
When you plug in the modem to your USB port, do you see any messages? Open a terminal window (Applications --> Accessories --> Terminal) and on the command line enter```
lsusb
```Post the output to the forum.

---

### Post by whouseswindowsanyway on 2008-04-18
the other thing that u can try -- (my favourite ) -- plug in the modem into ur usb.. then open terminal -- type dmesg
look for anything that says ttyUSB*
if let's say it says device connected to ttyUSB0.. then do the following : 

sudo gedit /etc/wvdial.conf

and enter the following in the file :
 
[Dialer Defaults]

Modem = /dev/ttyUSB0
Init1 = ATZ
Init2 = AT+CGDCONT=1,"IP","internet" ---if using gprs / 3g etc....
Username = (ur usrname)
Password = (ur password)

then save and close file and run :
wvdial



that should connect to internet.... i thinks...

---

