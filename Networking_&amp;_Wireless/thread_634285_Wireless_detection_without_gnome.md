---
title: "Wireless detection without gnome"
date: 2007-12-07
forum: Networking &amp; Wireless
---

### Post by mrblondeisback on 2007-12-07
I just got e17 and I will be removing my gnome from my system to get rid of all that bloat.  How can I get my wireless card to detect without network manager?  I have another box running archlinux and that was in the rc.conf file, I can't seem to find anything like that in my ubuntu distro.  I don't need roaming, just the one internet connection.  where can I configure my networks?  I did a sudo iwconfig essid "network name" but it still won't ping.  any help?

---

### Post by mpokrywka on 2007-12-07
Configuration of your network cards is in /etc/network/interfaces config file.
You did not told what is your connection type, but I assume it is very popular WPA with dhcp.
First type in terminal:
iwconfig
This will give you linux interface name of your wireless card, for example there will be "eth1" with something like "IEEE 802.11g".
Now edit /etc/network/interfaces file:
```
# make eth1 connection when system boots
auto eth1
# configuration of eth1 interface
iface eth1 inet dhcp
    wpa-ssid YOUR_NETWORK_NAME
    wpa-passphrase YOUR_NETWORK_KEY
```

after saving changes you can test if config works:
sudo ifdown eth1
sudo ifup eth1
ifconfig eth1
iwconfig eth1

For mode information see:
# /etc/network/interfaces syntax, how to configure static ip address, etc
man interfaces

# how to configure wireless wpa
zless /usr/share/doc/wpasupplicant/README.modes.gz

# how to configure open or wep encrypted wireless
less /usr/share/doc/wireless-tools/README.Debian

---

### Post by mrblondeisback on 2007-12-15
I'm not completely sure what my connection type is, but that leads me to believe that it's wpa as it's more common, right?  Anyway, I made the changes to my interfaces to no avail.  However, when i do```
 iwlist ath0 scan
``` it shows me my connection right there.  I tried manually setting the ssid with ```
iwconfig ath0 essid NETWORK_NAME
``` and brought it up and down again but still nothing.  I'll keep digging through those readmes but any more insight would be awesome, thanks.

---

### Post by mrblondeisback on 2007-12-15
Nevermind,  got it.  had to change it to wireless rather than wpa.  must not be wpa, lol.

---

