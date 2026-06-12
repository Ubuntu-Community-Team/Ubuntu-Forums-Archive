---
title: "WPA Fails but WEP works- Help with WPA"
date: 2006-09-06
forum: Networking &amp; Wireless
---

### Post by nimbuscott on 2006-09-06
duplicate

---

### Post by nimbuscott on 2006-09-08
I got it to work! The secret was to replace the contents of the interfaces file with the code below.

```
sudo gedit /etc/network/interfaces
```

replace the contents with the following then save the file. You replace the text in red [COLOR="Red"]***[/COLOR] with your own information. Part of the learning process for me with this involved setting my router to WPA2 which is AES algorithm not WPA1 which is TKIP algorithm.On my Linksys router the choice is Pre Shared Key & AES

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
pre-up iwconfig ra0 essid [COLOR="Red"]***[/COLOR]
pre-up iwconfig ra0 mode managed
pre-up iwpriv ra0 set Channel=1
pre-up iwpriv ra0 set AuthMode=WPAPSK
pre-up iwpriv ra0 set EncrypType=AES
pre-up iwpriv ra0 set WPAPSK=[COLOR="Red"]***[/COLOR]
pre-up iwpriv ra0 set TxRate=0




auto ra0

```

---

