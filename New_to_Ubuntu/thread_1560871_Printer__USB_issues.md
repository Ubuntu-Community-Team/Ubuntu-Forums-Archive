---
title: "Printer / USB issues"
date: 2010-08-25
forum: New to Ubuntu
---

### Post by Belteshazzar on 2010-08-25
Hello,
I am running Ubuntu 10.04 on a Toshiba Equium which has stopped recognising our HP Photosmart C4580 printer; under the printer properties it says "Printer status - Inactive - /usr/lib/cups/backend/hp failed". I have tried reinstalling cups and other packages relating to hp but nothing has worked.
I am not sure but I suspect this may be related to another issue: the USB ports seem to decide to stop working after the laptop has been left on for a while; upon restarting they work again, but if it has been on for more than an hour it seems to refuse to recognise anything USB (including the mouse). The printer is USB but today it has stopped working no matter how many times I restart. This USB problem has been annoying me for ages and I have searched through forums but haven't found anyone else with the same specific problem. Using lsusb reveals the following: > Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 045e:00d2 Microsoft Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 04f2:b070 Chicony Electronics Co., Ltd 
Bus 001 Device 004: ID 0bda:8197 Realtek Semiconductor Corp. RTL8187B Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
This is with printer and mouse attached. The Chicony thing is the internal web cam (which itself has never worked with ubuntu). I'm wondering if the issue is ubuntu or whether my laptop is just getting too old...
I would be very grateful for any help anyone could give me.

Belteshazzar

---

### Post by Belteshazzar on 2010-08-25
Ok for some unknown reason, the printer has suddenly been recognised and the "failed" message no longer displays in the printer properties - I don't understand it at all, since I have done literally nothing since my last attempt.
This is also why I suspect there's something wrong with the USB ports, since at the moment they are working fine (in other words, there is definitely a correlation between the printer and the USB ports working.)

Belteshazzar

---

