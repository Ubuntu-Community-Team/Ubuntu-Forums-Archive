---
title: "Wireless adapter quits working when idle"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by jbeauchamp on 2008-06-03
Ubuntu Server Hardy 2.6.24-16
Linksys Wireless USB adapter (WUSB54GC)

Works great as long as I'm continuously pinging something.  I'm sure there's a config somewhere that will resolve this but I'm not well-versed enough in *nix to figure it out.  Your help is greatly appreciated.

-James

---

### Post by jbeauchamp on 2008-06-03
FIXED

Added this to /etc/rc.local and rebooted.

ifconfig wlan0 down
ifconfig eth0 down
dhclient -r wlan0
ifconfig wlan0 up
ifconfig eth0 up
iwconfig wlan0 essid "MYSSID"
iwconfig wlan0 mode Managed
dhclient wlan0

Connection is staying up now so I guess it does work out of the box! :)

---

### Post by jbeauchamp on 2008-06-04
Looks like I spoke too soon...

last line from dmesg:
wlan0: No ProbeResp from current AP xx:xx:xx:xx:xx:xx - assume out of range

Any ideas?

---

