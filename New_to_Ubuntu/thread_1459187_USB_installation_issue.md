---
title: "USB installation issue"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by sandeep.e79 on 2010-04-21
Hello all
 
I am new to Ubuntu. I am trying to connect to internet using linktop ct800p model provided by my service provider. Please help me to get driver and installation details.
 
I am unable to get its driver
 
Thanks

---

### Post by dineshs on 2010-04-21
Is it a highspeed CDMA internet dialup modem?
In a terminal type ```
lsusb
```and enter
What is the output?
There are different methods to make dialup connection 
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)

---

### Post by sandeep.e79 on 2010-04-22
Hai
 
 i am also facing same issue. can any one help me in this regards.

---

### Post by sandeep.e79 on 2010-04-22
Sorry for last reply. its not high speed its only 144kbps wireless WLL based land line

---

### Post by dineshs on 2010-04-22
Try any of the dialup methods as in
[http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html](http://www.ubuntugeek.com/setting-up-dial-up-connection-in-ubuntu.html)
Also post the output of lsusb when modem is connected and is ON
I suggest you use pppconfig because gnome-ppp and wvdial need to be installed first

---

