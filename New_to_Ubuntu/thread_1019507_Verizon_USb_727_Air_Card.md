---
title: "Verizon USb 727 Air Card"
date: 2008-12-23
forum: New to Ubuntu
---

### Post by motor409 on 2008-12-23
Can anyone tell me if there are available drivers for the Verizon USb 727 aircard? I am new to Ubuntu 8.04 and I did get the software to install but the application can not find the device. The light on the device turns green but still can not find the correct drivers. If anyone could help I need the drivers and a good set of directions to install. Thanks

---

### Post by halitech on 2008-12-23
with the device not plugged in, open a terminal and post the output of
```
sudo lsusb
```
then plug it in, wait a minute and issue the same command.

what software did you install?

---

### Post by motor409 on 2008-12-23
I installed the verizon software that comes on the disk. I will run those commands later when I get back home and post the results.

---

### Post by halitech on 2008-12-23
do they include a linux version?

---

### Post by motor409 on 2008-12-23
No there was not a Linex version. I used Wine to install the exe. It worked well.

---

### Post by halitech on 2008-12-23
using wine to install software of this sort does not always work. Let's see if the system is seeing the card and then we'll go from there

---

### Post by motor409 on 2008-12-23
Not plugged in:

Bus 005 Device 005: ID 058f:6335 Alcor Micro Corp. 
Bus 005 Device 003: ID 18e8:6229  
Bus 005 Device 002: ID eb1a:2771 eMPIA Technology, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 062a:0000 Creative Labs Optical Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000 

Plugged in:

Bus 005 Device 005: ID 058f:6335 Alcor Micro Corp. 
Bus 005 Device 003: ID 18e8:6229  
Bus 005 Device 002: ID eb1a:2771 eMPIA Technology, Inc. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 004: ID 062a:0000 Creative Labs Optical Mouse
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 002: ID 1410:4100  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


Same Results...

---

### Post by motor409 on 2008-12-23
sorry I missed the  

Bus 003 Device 002: ID 1410:4100 

That must be the device.

---

### Post by ieee488 on 2008-12-23
[http://www.evdoforums.com/thread7379.html](http://www.evdoforums.com/thread7379.html)
scroll down

---

### Post by motor409 on 2008-12-23
These directions do not work for me. I get this error half way through the directions 

KPPP cannot be installed on your computer type (lpia). Either the application requires special hardware features or the vendor decided to not support your computer type.

Does anyone have any suggestions?

---

### Post by halitech on 2008-12-23
ok, I thought this card sounded familar and it was :) Just helped someone a few weeks back with the same issue. are you running 8.04 or 8.10?

check this thread for more ideas but basically it should work in 8.10 using GnomePPP to connect

[http://ubuntuforums.org/showthread.php?t=996421](http://ubuntuforums.org/showthread.php?t=996421)

---

### Post by ieee488 on 2008-12-23
Kppp is for Kubuntu
gnome-ppp is for Ubuntu

---

### Post by MrKlean on 2008-12-23
If you right click on the connection icon, go to edit connections and go to wireless broadband... you can set it up there real easy ; )

---

