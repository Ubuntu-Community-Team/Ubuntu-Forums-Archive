---
title: "How to tell what Hardware is working"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by mrpbjnance on 2009-01-25
I am new to ubuntu.  I am one of what looks like many who are having trouble with their wireless card not working.  I got ndiswrapper and installed a driver that I now see.  But I still do not see any wireless networks.  How can i tell if my wireless card is even recognized and working?

Thnaks!

---

### Post by Abu_Dayya on 2009-01-25
lshw should tell you if your wireless card is installed or not. If its there but still not working, you should check how to use ndiswrapper to install the drivers for your specific card. search ndiswrapper guides in these forums and you should find plenty of information

---

### Post by philinux on 2009-01-25
> **mrpbjnance said:**
> I am new to ubuntu.  I am one of what looks like many who are having trouble with their wireless card not working.  I got ndiswrapper and installed a driver that I now see.  But I still do not see any wireless networks.  How can i tell if my wireless card is even recognized and working?

Thnaks!

Which version of ubuntu have you got running?

---

### Post by Kevbert on 2009-01-25
Please enter the following commands in terminal and post back the results:
```
iwconfig
iwlist scanning
```

---

### Post by mrpbjnance on 2009-01-26
I am on unbuntu 8.10

mike@Ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

mike@Ubuntu:~$ iwlist scanning
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

mike@Ubuntu:~$

---

