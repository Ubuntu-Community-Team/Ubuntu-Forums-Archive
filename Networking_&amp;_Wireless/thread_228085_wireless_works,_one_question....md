---
title: "wireless works, one question..."
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by ncappel1 on 2006-08-02
Most of my wireless woes were solved a bit ago, but there is one small problem: 
when I boot, I can't connect until I click into System-->Administration-->Networking, then click on the device "ra0", and click "activate"

How can I make it activate automatically at startup?

---

### Post by stormblue on 2006-08-02
In /etc/network/interfaces put

```
auto ra0
```

---

### Post by ncappel1 on 2006-08-02
To my surprize, that line was already in the end of mt /etc/network/interfaces this is what the whole file looks like, if this is any help:

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
script grep
map eth0

iface ra0 inet dhcp
pre-up iwconfig ra0 essid NETGEAR
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=*
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwpriv ra0 set WPAPSK="***********"
pre-up iwpriv ra0 set TxRate=0
wireless-essid NETGEAR




auto ra0
```

any more ideas?

---

