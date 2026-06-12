---
title: "Wireless Signal Monitoring Program that works?"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by dbsoundman on 2007-08-20
Hello all. I've got a Dell E1505 laptop with the Broadcom 1390 wireless card all installed and everything. The wifi works great, but I was looking around trying to find a program that would sit in my system tray and simply show how strong the wifi signal is, kind of like what windows XP has; just the little bar graph thing. I found a program called kwirelessmonitor, and something else, but neither of them work. kwirelessmonitor, when I could actually get it to start up, kept saying there as a "device error", and now, I type the command in and it doesn't even start up at all. The other program, whose  name I forget, was even worse. Are there other programs out there like this that work better, or is there a way to fix kwirelessmonitor so that it actually works?

Thanks,
Dan

---

### Post by moore.bryan on 2007-08-20
*isn't network-manager already installed and in your tray?  you could also check out [wicd]("http://wicd.sourceforge.net").*

---

### Post by dbsoundman on 2007-08-20
A-ha! I hadn't noticed that the network connection thing in the system tray was still looking at my wired ethernet connection. Switched it over to the wireless connection, and it shows everything. The signal graphic is a bit different, but I can probably deal with it. Between that and wifi-radar (which makes it really easy to pick out networks to connect to) I think I'm all set.

-Dan

---

### Post by dbsoundman on 2007-08-20
I take that back; I'm trying wicd, which combines the two programs, and so far, I think it might be more sensible anyway since it does both things in one piece...we'll see how it works out.

-Dan

---

### Post by dbsoundman on 2007-08-20
So far, wicd is all right. The only thing I haven't figured out (and this isn't necessarily connected with the functionality of wicd) is how to connect my laptop to an encrypted wifi signal. I reconfigured my router to do WEP encryption, put in a passcode, it generated a key, and all that, but when I put those settings into wicd and tried to connect, it failed. I'm not sure why that happened...

Also, just for reference, what is the default network management program in ubuntu called? I know there's network manager, but I'm talking about the one that runs in the system tray. I removed it from the tray and now I can't find it anymore.

Thanks,
Dan

---

### Post by rainwalker on 2007-08-20
NetworkManager Applet 0.6.4
[http://www.gnome.org/projects/NetworkManager/](http://www.gnome.org/projects/NetworkManager/)

---

