---
title: "Ubuntu server doesn't remember static ip address...?"
date: 2007-11-01
forum: Networking &amp; Wireless
---

### Post by growse on 2007-11-01
I've got a strange problem with trying to set a static ip on an ubuntu gutsy server running as a vmware guest on a gentoo host.

My /etc/interfaces is:

```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.0.4
netmask 255.255.255.0
gateway 192.168.0.1

```

If I issue a /etc/init.d/networking restart it uses this address correctly. However, after a certain amount of time (I think it's about a day or two) I find that the server's randomly changed it's address, usually to 192.168.0.30. I'm guessing it's picking it up from dhcp. The only thing in /var/log/messages when this happens is:

```

Nov  1 09:17:20 ticklemail kernel: [296508.320865] eth0: link up
Nov  1 09:21:04 ticklemail kernel: [296749.733844] UDF-fs: No VRS found

```

As I'm trying to run this box as a mail server, this is rather annoying, and the two debian stable boxes I have also running as vmware guests don't have this problem. Any ideas what it could be?

---

### Post by bapoumba on 2007-11-01
Same problem here, with just a regular install. Please try:
```
sudo pkill dhclient

```
/me looks for the bug report.
Edit : I get timeouts from Launchpad..

---

### Post by Gutti on 2007-11-01
Have you tried to set the static ipaddress outside of the field of the router? You are using ip 192.168.0.4 as your static ip, have you tried to set it @ 192.168.0.104 or 192.168.0.134?

---

### Post by growse on 2007-11-01
Yeah, dhclient3 was running. I've killed it - will see if that works.

> **Gutti said:**
> Have you tried to set the static ipaddress outside of the field of the router? You are using ip 192.168.0.4 as your static ip, have you tried to set it @ 192.168.0.104 or 192.168.0.134?

Not quite sure what you mean outside the "field of the router". There's only one network I've got, 192.168.0.0/24 and the router is being the gateway and sitting at 192.168.0.1. Why would setting the static to .104 help?

---

