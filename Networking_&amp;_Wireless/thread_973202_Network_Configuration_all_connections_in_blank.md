---
title: "Network Configuration all connections in blank"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by MorlanXaos on 2008-11-06
I have updated from 8.04 to 8.10. Network Configuration is different. Now there few folders, wlan, wifi, dsl, vpn. etc. No one of them is showing my wifi settings!? They are all in blank. Even though the wifi works. Any clue?:confused:

---

### Post by cariboo on 2008-11-06
What is the output of:

```
cat /etc/network/interfaces
```

This should show your network interfaces

Jim

---

### Post by MorlanXaos on 2008-11-07
Thanks Jim for your interest,

This is what it looks like:

auto lo
iface lo inet loopback


iface wlan0 inet static
address 192.168.1.34
netmask 255.255.255.0
gateway 192.168.1.1
wireless-key s:Z0002CF906XXX
wireless-essid WLAN_60

auto wlan0
root@xavier-casa:/home/xavier# 

The wifi is working, but the network manager does not show the connection

If I look at the connexions in the network manager all the folders are empty?

---

### Post by ijustam on 2009-03-08
Bump.

Same exact thing occurring here.  It didn't bother me but now that I need to change some settings its become a problem :(

---

### Post by Iowan on 2009-03-08
Network Manager is different in Intrepid.  It stores its settings in /etc/NetworkManager - in particular, */etc/NetworkManager/nm-system-settings.conf*.

---

