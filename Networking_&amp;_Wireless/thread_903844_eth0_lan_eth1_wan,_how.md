---
title: "eth0 lan eth1 wan, how?"
date: 2008-08-28
forum: Networking &amp; Wireless
---

### Post by f8l_0e on 2008-08-28
I have a machine with two NICs running Hardy Server.  I want to have all lan traffic over eth0 and internet traffic over eth1.  I'm doing this strictly for network performance on this machine, so I don't need to set it up as a Firewall or NAT.  Both NICs will be connected to a switch and plugging the NIC I want internet traffic on directly to the gateway is not an option.  I've searching the forum and trying to make sense of the ip route documentation, but I would appreciate an example if anyone can provide it.

---

### Post by Iowan on 2008-08-29
[This]("https://help.ubuntu.com/community/Internet/ConnectionSharing") may help.

---

### Post by f8l_0e on 2008-08-29
Thank you for responding, but this isn't what I'm looking for.  I don't want any NAT or ICS.  The machine that I'm running has asterisk installed on it.  I want one network card dedicated to taking traffic from softphones on the lan and the second nic communicating with the VOIP provider.

---

### Post by f8l_0e on 2008-09-02
Has anyone here done this?

---

