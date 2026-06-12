---
title: "Can't switch from wired to wireless"
date: 2007-12-11
forum: Networking &amp; Wireless
---

### Post by Ice_cone on 2007-12-11
I normally use wired connection on my IBM X31 notebook
Sometimes I would like to switch to wireless and walk around
But I just can't do so.  After I unplugged, internet is gone.
I tried reconnecting with the nm-applet but still doesn't work
But works after suspend and resume, or restart
Anyway to get it working?
thanks

---

### Post by kevdog on 2007-12-11
An example of how to switch using the command line:

sudo dhclient -r eth0
sudo ifconfig eth0 down
sudo ifconfig wlan0 up
...
...


Fill in the .... lines by consulting my thread on how to connect via the command line.

---

