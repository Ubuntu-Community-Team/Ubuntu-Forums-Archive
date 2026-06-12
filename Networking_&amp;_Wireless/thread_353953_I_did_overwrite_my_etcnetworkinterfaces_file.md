---
title: "I did overwrite my /etc/network/interfaces file"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by kjuvik on 2007-02-05
As a quite new user of Ubuntu I tried to modify the /etc/network/interfaces - file on my Thinkpad X60s, Ubuntu 6.10 computer. I ended up overwriting the file with an emty file. How do I get it back? Or how could I write a new file?

Kjuvik

---

### Post by tturrisi on 2007-02-05
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface uncomment if use wired ethernet
# allow-hotplug eth0
# iface eth0 inet dhcp
# auto eth0

# wifi without WEP where ath0 = your interface
# auto ath0
# iface ath0 inet dhcp

# wifi with WEP where ath0 = your interface
# auto ath0
# iface ath0 inet dhcp
# wireless-essid 8724
# wireless-key xxxx-xxxx-xx

```

---

### Post by kjuvik on 2007-02-05
Thanks! But I still dont understand it all. I use both wired network (eth0) and wireless network (eth1). Should I just copy and paste? Or do I have to make some adjustments?

---

### Post by jtc on 2007-02-05
Since it's a laptop I assume you run it as a desktop-system and not a headless server? If you run GNOME or KDE both of them have controlpanels where you can add your networksettings without having to modify /etc/network/interfaces

---

### Post by tturrisi on 2007-02-05
> **kjuvik said:**
> Thanks! But I still dont understand it all. I use both wired network (eth0) and wireless network (eth1). Should I just copy and paste? Or do I have to make some adjustments?

If you do not use WEP security then copy+paste this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface uncomment if use wired ethernet
allow-hotplug eth0
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid YOUR-SSID

auto eth0
auto eth1

```

if use WEP then copy & paste this:
```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface uncomment if use wired ethernet
allow-hotplug eth0
iface eth0 inet dhcp

iface eth1 inet dhcp
wireless-essid YOUR-SSID
wireless-key xxxx-xxxx-xx 
#REPLACE x-s WITH YOUR WEP KEY

auto eth0
auto eth1

```

---

