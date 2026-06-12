---
title: "thin client setup"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by dbclinton on 2007-11-12
I'm trying to set up a thin client network using the Edubuntu Desktop edition 7.1.0 (I'm using that rather than the server edition because I installed via Wubi which, as far as I know, doesn't work with server). I have enabled the thin client manager and set the ip address of my Ethernet card in network manager to:
address 192.168.0.111
netmask 255.255.255.0
gateway 192.168.0.1
Nevertheless, when I boot my client (using a CDRom iso created by rom-o-matic), the client returns "no ip address found" (or something like it) over and over again.
I should add that I'm a bit new to linux terminal (though I have many grim memories of DOS).
Any ideas?
Thanks

---

### Post by veloce on 2007-11-13
> **dbclinton said:**
> I'm trying to set up a thin client network using the Edubuntu Desktop edition 7.1.0 (I'm using that rather than the server edition because I installed via Wubi which, as far as I know, doesn't work with server). I have enabled the thin client manager and set the ip address of my Ethernet card in network manager to:
address 192.168.0.111
netmask 255.255.255.0
gateway 192.168.0.1
Nevertheless, when I boot my client (using a CDRom iso created by rom-o-matic), the client returns "no ip address found" (or something like it) over and over again.
I should add that I'm a bit new to linux terminal (though I have many grim memories of DOS).
Any ideas?
Thanks

Sounds like your client has no ip address.  How is it supposed to get an ip address?  If dhcp, then have you got a dhcp server set up on the server?

---

### Post by dbclinton on 2007-11-13
That is likely an issue: DHCP is installed on the system but, assuming it's not set to do it out of the box,  I'm not sure how to access configuration controls (and how to assign an ip address to a client that won't even "exist" during configuration and will have no way of identifying itself upon bootup).
Thanks

---

