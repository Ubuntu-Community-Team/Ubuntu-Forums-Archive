---
title: "Cannot connect to wireless"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by Spccowboy on 2007-06-20
I'll start by saying that I've only been using Ubuntu for about a week, so I'm pretty green. 

My problem is that I can see wireless networks (both my own and others in the building) but the bars next to them are blank in Network Manager. Using Wireless Assistant I can see a strong signal but still can't connect. 

I am running Fiesty 64bit with a Linksys WMP54g adapter and a WRT54G router. 

Thoughts?

---

### Post by dbaile10 on 2007-06-23
i'm having the same problem, i cant quite figure it out

---

### Post by Spccowboy on 2007-06-23
I'll let you know if I figure anything out.

---

### Post by SwannyJ on 2007-06-23
Same problem here.  Inspiron 2500 and DLink DWL-650+ adapter.  AK!

---

### Post by sqadeer on 2007-06-23
Same problem. SOme details are:

I just upgraded my system to 7.04 and lost the functionality of wireless card. My sytem is a Dell Latitude D800 and the system was working with 6.04 without any problem. The /etc/network/interfaces fiel is (after upgrade):

auto lo
iface lo inet loopback


auto eth0
iface eth0 inet dhcp


auto eth1
iface eth1 inet dhcp
        wpa-driver wext
        wpa-ssid dlink
The output of the command wpa_supplicant -W -c/etc/network/interfaces -ieth1 -dd
is:

Reading configuration file '/etc/network/interfaces'
Line 1: Invalid configuration line 'auto lo'.
Line 2: Invalid configuration line 'iface lo inet loopback'.
Line 5: Invalid configuration line 'auto eth0'.
Line 6: Invalid configuration line 'iface eth0 inet dhcp'.
Line 9: Invalid configuration line 'auto eth1'.
Line 10: Invalid configuration line 'iface eth1 inet dhcp'.
Line 11: Invalid configuration line 'wpa-driver wext'.
Line 12: Invalid configuration line 'wpa-ssid dlink'.

Please help.

---

### Post by SwannyJ on 2007-06-28
I feel like an idiot.  All I had to do was manually configure the network (system>administration>network) and WEP, restart, and it worked.

Any other noobs out there who haven't tried that yet might want to give it a shot...I myself need to read more about Ubuntu.

---

