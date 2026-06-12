---
title: "Bcm43xx Wireless always changes from Monitor to Managed mode, every 2 Minutes !"
date: 2007-08-31
forum: Networking &amp; Wireless
---

### Post by starfly on 2007-08-31
Hello,

Ive got a Problem whats very strange!

I use Ubuntu Feisty and the Bcm43xx Driver 4 my Wireless Broadcom card . When i manualy change to Monitor mode, the
System randomly changed back to Managed Mode, automaticaly...Always between 1-2 Minutes after changing 2 Monitor mode :-(

Someone an idea to hold the card in Monitor mode, for more than 2 Minutes...

Thanks a LOT :-)

---

### Post by spd106 on 2007-09-01
Have you turned off Network Manager?

If not make sure you in static mode rather than roaming mode in the System -> Admin -> Network capplet.

It might be quicker to just run these commands.
```
sudo ifdown wlan0
```
```
sudo /etc/dbus-1/event.d/25NetworkManager stop
```

---

### Post by starfly on 2007-09-01
That allmost killed all my Connections ;-) Reactivated it, and set my connection to "manually", now it seems 2 work in Monitor mode , so u brougt me on a right way of thinking ;-)

---

