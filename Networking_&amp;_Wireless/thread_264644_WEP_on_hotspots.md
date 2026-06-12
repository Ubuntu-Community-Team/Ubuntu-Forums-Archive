---
title: "WEP on hotspots?"
date: 2006-09-25
forum: Networking &amp; Wireless
---

### Post by Ripfox on 2006-09-25
Ok, I guess i'm luckier than most in that I have my home network working fine, but when I go to hotspots where I KNOW it's an unsecured network, any tool I use asks for a WEP key. This is true for the built in Gnome tool, NWM, Gtk-Wifi, or any other thing I've dinked with. Anyone know a way around this? Thanks in advance for any help.

---

### Post by wieman01 on 2006-09-25
Depends on what you are referring to as "way around this"... But there are tools around (even in the repositories) that help you assess your own network's security by attempting to crack your wireless (WEP, WPA) network key (if that's what you mean):

[COLOR="Blue"]1. airsnort (graphical interface)
2. aircrack (command line)[/COLOR]

Airsnort in particular is an excellent tool, however, be prudent with its usage!

---

### Post by wieman01 on 2006-09-25
Disclaimer: Any attempt to break into somebody else's secured network is deemed illegal. 

Therefore take my comment very seriously because if a person enables WEP (no matter how bad this sort of the encryption & authentication method is) she/he has got a reason for it.

---

### Post by Ripfox on 2006-09-25
Well, I don't think it's an issue since it says "Free Wireless" on the front of the places that I'm trying to get into...I'm still not sure if this is the reason, since actually the network tool in Gnome says I am connected sometimes, but no google. Page not found. Then I try NWM and it asks for a WEP key, when I know there should be none...confused...

---

### Post by Ripfox on 2006-09-25
This is what I get when I attempt my OWN network with airsnort.


/sbin/wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable > /dev/null
sh: /sbin/wlanctl-ng: No such file or directory
SIOCSIFFLAGS: Permission denied

---

### Post by wieman01 on 2006-09-25
> **ripfox said:**
> This is what I get when I attempt my OWN network with airsnort.


/sbin/wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable > /dev/null
sh: /sbin/wlanctl-ng: No such file or directory
SIOCSIFFLAGS: Permission denied
Try driver type "Host AP/Orinoco" and start Airsnort with sudo:
> sudo airsnort

---

