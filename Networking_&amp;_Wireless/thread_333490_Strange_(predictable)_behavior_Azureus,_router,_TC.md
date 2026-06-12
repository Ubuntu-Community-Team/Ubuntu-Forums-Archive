---
title: "Strange (predictable) behavior: Azureus, router, TCP/DHT"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by djgrandmarquis on 2007-01-07
Occasionally, Azureus won't play nice. I get a "Firewall/NAT (TCP) reachability problem" and "DHT Firewalled." I have experienced this with multiple machines (Kubuntu Breezy, Kubuntu Edgy, XP) and multiple routers (Netgear, Linksys). In every case, I did not enable any port forwarding, firewalls, etc. This problem has a simple solution: reset the router by unplugging it, then plugging it back in.

It's somewhat irritating, so I'm curious: why does this happen? My settings never change, and rebooting the router solves the problem every time. I searched the Forums and Google to no avail.

Any thoughts?

---

### Post by wilsonag on 2007-01-07
> **djgrandmarquis said:**
> Occasionally, Azureus won't play nice. I get a "Firewall/NAT (TCP) reachability problem" and "DHT Firewalled." I have experienced this with multiple machines (Kubuntu Breezy, Kubuntu Edgy, XP) and multiple routers (Netgear, Linksys). In every case, I did not enable any port forwarding, firewalls, etc. This problem has a simple solution: reset the router by unplugging it, then plugging it back in.

It's somewhat irritating, so I'm curious: why does this happen? My settings never change, and rebooting the router solves the problem every time. I searched the Forums and Google to no avail.

Any thoughts?

It is very likely the router has problems with the number of connections created by Azureus.  I have used multiple routers and have the same trouble.  You could try going into the settings in Azureus and limit the number of global connections it creates.  Many routers made today have problems with to many connections being created.  I know the documentation in Azureus lists a few routers that are known to have troubles with the number of connections.

---

### Post by lothar_m on 2007-01-07
i agree with wilsonag.

talking from my own experience: i have a dlink 624+ router and can't get decent speeds from p2p  networks (especially bittorrent and emule protocols) despite having tried everything i couls think of (from port forwarding to dmz). in top of that if i bypass the router and connect directly to the cable modem i get great download speeds.

---

### Post by djgrandmarquis on 2007-01-08
Great insight, thanks. It makes a lot of sense, since this problem never happens at school (big industrial strength router) and only at home (cheap desktop routers).

I limited my connections to 99 via Tools->Options->Transfer as per the Azureus Wiki:
[http://www.azureuswiki.com/index.php/Good_settings#Good_settings_based_upload_speed](http://www.azureuswiki.com/index.php/Good_settings#Good_settings_based_upload_speed)

This also leads me to believe it could be related to my limited upload bandwidth, but it's most likely an overburdened router.

---

### Post by lothar_m on 2007-01-19
yeap .. that probably the case.... i've also heard that usally this kind of problem may arise due to heavy use of the router's NAT table.

---

