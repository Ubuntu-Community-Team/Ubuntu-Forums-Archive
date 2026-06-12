---
title: "Network settings not sticking"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by danduq on 2008-11-11
Hi,

Since upgrading to Intrepid I'm finding that my network settings (DNS & search domains) won't stick.

I go to System -> Preferences -> Network Configuration and edit "Auto eth0". I change the IPv4 Method to DHCP addresses only and input my two comma separated DNS server IPs, and three comma separated search domains, then click OK.

Looking at my /etc/resolv.conf my DNS servers are still there, but there's only one search domain (my domain) and I'm unable to find machines in the other domains.

With Hardy I ended up editing /etc/dhcp3/dhclient.conf, which I can do again, but didn't know if there might be some other preferred method...?

Here's my very basic /etc/network/interfaces contents;
```
auto lo
iface lo inet loopback
auto wlan0
auto eth0

```

Also, I don't know if this is a symptom of the same problem, but when restarting networking (sudo /etc/init.d/networking restart) I get the message;
```
Ignoring unknown interface wlan0=wlan0.
Ignoring unknown interface eth0=eth0.
```

Any help gratefully received!  :)

---

