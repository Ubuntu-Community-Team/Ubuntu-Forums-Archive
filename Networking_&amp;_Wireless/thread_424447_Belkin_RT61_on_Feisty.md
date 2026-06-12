---
title: "Belkin RT61 on Feisty"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by super.rad on 2007-04-26
I installed feisty the other day, and after reading a few things on here the first thing i did was to disable network manager, i did that this way 
```
sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop
```

and then creating 2 files containing "exit" in 
/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

then i edited the /etc/network/interfaces and added the following at the bottom

```
auto ra1
iface ra1 inet static
address 192.168.123.176
netmask 255.255.255.0
gateway 192.168.123.254
pre-up iwconfig ra1 essid NETGEAR
```

but it will not connect to the internet or ping the router or anything.

is their anything i have missed out or done wrong?
the wireless network has no security
if you need any more information just ask. Thanks

---

### Post by super.rad on 2007-04-26
i just logged back onto ubuntu to see if i could find anything wrong and i can now access my router but no other websites.

---

