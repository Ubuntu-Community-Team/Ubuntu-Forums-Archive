---
title: "Parameters save place"
date: 2007-10-17
forum: Networking &amp; Wireless
---

### Post by ennoreys on 2007-10-17
Hello

I'd like to know where (in which file) are saved the following parameters :

Settings for network in menu admin - network

NTP servers list

Thanks

---

### Post by chili555 on 2007-10-17
> Settings for network in menu admin - network
Please look in /etc/network/interfaces.

> NTP servers listPlease look in /etc/ntp.conf

If you intend to modify or fine-tune these to your liking, which I recommend, please be sure to make a backup of your known working file, for example:```
sudo cp /etc/ntp.conf /etc/ntp.conf.bak
```Then if you need to to recover from a failed experiment, you can reverse the process and get a working file back in place.

---

### Post by spd106 on 2007-10-17
Locations are stored under /root/.gnome2/network-admin-locations

Current network settings like DHCP or static addresses are in the /etc/network/interfaces file.

Hostname is in the /etc/hostname file. Don't just edit this because things will break,  use the hostname utility or network-admin.

Service discovery is set in the /etc/default/avahi-daemon file.

DNS settings are configured in the /etc/resolv.conf file.

and Hosts settings are in the /etc/hosts file.

If you have roaming mode enabled on any interface then Network Manager will assume control over the resolv.conf, which can make routing troublesome unless you work with/around it.

The default NTP settings are in /etc/default/ntpdate.

---

### Post by ennoreys on 2007-10-17
Thanks for your answers, I was not looking for /etc/network/interfaces but location for network profiles (which contains network settings). I'll take a look when I'll be home.

---

### Post by ennoreys on 2007-10-17
I'd a look on my computer, and :

The /home/.gnome2 does not contains any locations (profiles) file !

The /etc/ntp.conf contains the actual NTP settings (servers that are selected), not the list of servers which I'm looking for.

---

