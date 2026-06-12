---
title: "Speedtouch USB 330/120"
date: 2007-03-30
forum: Networking &amp; Wireless
---

### Post by FRuMMaGe on 2007-03-30
Hello, I am new to Ubuntu and this is my first post on the forums.  My windows installation recently got destroyed so I decided to revert to Ubuntu (which I had a live CD for in my desk).  Everything installed fine and it boots perfectly.

However, no matter how many tutorials I follow, I cannot get my speedtouch to work!

I have a choice of two to use: Speedtouch 120 or Speedtouch 330 (version 4)

With windows XP, I used to connect to the internet with my SpeedTouch 120 via a router in my Dad's office.  The router is a Thompson Speedtouch 570/570i if that matters.

Any help would be greatly appreciated.  I've been trying for days to get online and i'm considering giving up and getting Windows again.

EDIT: I'm using Ubuntu 6.06 Dapper Drake

---

### Post by teaker1s on 2007-03-30
[http://www.linux-usb.org/SpeedTouch/]("http://www.linux-usb.org/SpeedTouch/")
there is also an arp issue, which if you can get connected,but not surf net -then I'd have to look for the link-It will take time as I'm subscribed to hundreds of threads.

or buy an asdl router

---

### Post by FRuMMaGe on 2007-03-30
> **teaker1s said:**
> [http://www.linux-usb.org/SpeedTouch/]("http://www.linux-usb.org/SpeedTouch/")
there is also an arp issue, which if you can get connected,but not surf net -then I'd have to look for the link-It will take time as I'm subscribed to hundreds of threads.

or buy an asdl router

I've tried this tutorial, and it didn't work. :(

---

### Post by teaker1s on 2007-03-30
okay but didn't work how, have you looked at your logs, did firmware load, did it try to connect? It's very difficult to suggest solutions to "it doesn't work" without an idea of whats going wrong

---

### Post by FRuMMaGe on 2007-03-31
> **teaker1s said:**
> okay but didn't work how, have you looked at your logs, did firmware load, did it try to connect? It's very difficult to suggest solutions to "it doesn't work" without an idea of whats going wrong

I've looked at my device manager and that detects it.  However, it just will not interface with it :(

---

### Post by teaker1s on 2007-03-31
so you have tried the various firmwares and they won't load?
```
lsusb 
``` should give you the revision number as well

also worth knowing that sometimes the colour of the modem and the firmware required on guide-not always correct, well worth trying the other firmwares

welcome to the forums:popcorn:

---

