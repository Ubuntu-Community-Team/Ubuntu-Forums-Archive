---
title: "wifi card not detected"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by U-Johannes on 2009-11-15
I just installed Ubuntu 9.10 and I have a Sitecom WL-608 USB Wifi card (the driver is - I guess - rt2870). When I put the card in the USB slot, nothing happens. 
From iwconfig I get:

johannes@johannes-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

Can anybody tell me what I can do that the system at least recognizes the card?

And sorry for any dumb question. I am an Absolute Beginner with capital A.:D

---

### Post by kapi on 2009-11-15
Hi I had a similar problem this morning and got it sorted.

Try going to system>administration>hardware drivers

then select one of the standard wireless driver, it may be that it's just not installed.

Select the driver and then click 'activate'

hope it helps, you may have to re boot after the installation

---

