---
title: "Static wireless ipadress - conection problems"
date: 2008-11-30
forum: Networking &amp; Wireless
---

### Post by greenwom on 2008-11-30
I have recently changed my home wireless desktop to a static IP.  I'm running a dynamic FTP site so I needed a static address to point to.

Prior to the change I never dropped the connection on this desktop.  

when I run iwconfig it still shows an association to the Access Point but when I point my browser to the router I get nothing  

Now to reestablish the connection I end up running: ```
$ sudo ifdown wlan1
$ sudo ifup wlan1
```

How can I figure out why I'm dropping the connection and I'm not much of a script writer, is there a simple script I can write for the ifdown/up commands so my wife and kids can just click on a panel icon to re-establish the connection until I figure the problem out?



I can't figure out why the dropped connection

---

### Post by greenwom on 2008-12-04
shameless bump

---

### Post by IQRules on 2008-12-04
Try this,

sudo apt-get install wifi-radar

Check with "man interfaces", that might help

---

