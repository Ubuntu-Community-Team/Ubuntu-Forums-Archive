---
title: "How do I make a dhcp3 server for only one interface?"
date: 2008-06-03
forum: Networking &amp; Wireless
---

### Post by Cadmus on 2008-06-03
Good day everyone,

I've got a server that I want to try iSCSI on, now here's how I've got things at the moment
[LIST]
[*]Server has two interfaces eth0 and eth1
[*]eth0 is static IP, and connects to the rest of the test LAN (192.168.2.*)
[*]eth1 is also static IP (10.0.0.1), and will be used for the iSCSI targets network (10.0.0.*)
[/LIST]

Now, what I want to do is set up dhcp3 server (assuming that's still the right one to be using) and have it serve addresses, but only on eth1 to prevent any problems on the test lan.

The documentation is a little spartan on this and from a few forum posts I've found for Debian it's not just me, would I be right in assuming I want just a stanza like this in dhcpd.conf?

```
subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.2 10.0.0.0.254}

```

and the 'subnet' part stops it serving IPs on the other interface, right?:confused:

---

### Post by Iowan on 2008-06-03
I think the subnet section only tells where the address will be leased.  Check the **man dhcpd.conf** page for info on local-address.

---

### Post by yingeric on 2009-04-15
> **Cadmus said:**
> Good day everyone,

I've got a server that I want to try iSCSI on, now here's how I've got things at the moment
[LIST]
[*]Server has two interfaces eth0 and eth1
[*]eth0 is static IP, and connects to the rest of the test LAN (192.168.2.*)
[*]eth1 is also static IP (10.0.0.1), and will be used for the iSCSI targets network (10.0.0.*)
[/LIST]

Now, what I want to do is set up dhcp3 server (assuming that's still the right one to be using) and have it serve addresses, but only on eth1 to prevent any problems on the test lan.

The documentation is a little spartan on this and from a few forum posts I've found for Debian it's not just me, would I be right in assuming I want just a stanza like this in dhcpd.conf?

```
subnet 10.0.0.0 netmask 255.255.255.0 {
range 10.0.0.2 10.0.0.0.254}

```

and the 'subnet' part stops it serving IPs on the other interface, right?:confused:

sudo vi /etc/default/dhcp3-server
INTERFACES="eth0"

---

