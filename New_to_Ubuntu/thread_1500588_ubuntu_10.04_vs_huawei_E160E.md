---
title: "ubuntu 10.04 vs huawei E160E"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by markus.dnd on 2010-06-03
Hello, i am having an odd problem with huawei 3G modem. 

My ubuntu is able  to find it out as mass storage if i have no usb-modeswitch installed and if i do i can not even see it as storage

When modeswitch is installed i can do lsusb and for the part where i should see some long identification i see only : 
Bus 001 Device 050: ID 1e0e:f000  

I have no idea  of what i should do to get this thing to work and my 7h of google have shown only problems with making it work with connection manager, i can not even get that far since i do not get all of the info i should be getting

---

### Post by juanJosepablos on 2010-07-28
Download new data from  the usb_modeswitch project and copied them under /etc/usb_modeswitch.d directory.
see
[http://www.draisberghof.de/usb_modeswitch/](http://www.draisberghof.de/usb_modeswitch/)

---

