---
title: "How to find IP's of other computers on netowork?"
date: 2007-04-29
forum: Networking &amp; Wireless
---

### Post by 3rods on 2007-04-29
Is there a way to find the IP's of other computers/devices on the network in ubuntu? Command line or gui.

---

### Post by mdjohnson on 2007-04-29
A few  ways, none guaranteed to list everything:

If you have a proper dns server set up, then you can use the host utility to pull a list of entries from the DNS server:

host -l <domain>

If not, you can send pings out to a broadcast address and see what responds.  Assuming the hosts are not set to ignore pings.

If you're on a local network, your IP will likely be something like 192.168.0.10.  If this is the case, try broadcast address 192.168.0.255.

ping -b 192.168.0.255

Failing that, nmap's quite handy, run as root:

nmap -sP 192.168.0.* (alter according to what range you want to scan)(also can't remember the exact syntax, so check the man page, you want a ping sweep)

---

### Post by 3rods on 2007-04-29
Good stuff. Thanks!

---

