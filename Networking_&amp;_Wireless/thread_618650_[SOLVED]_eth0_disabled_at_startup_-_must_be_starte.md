---
title: "[SOLVED] eth0 disabled at startup - must be started manually"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by kooldino on 2007-11-20
A co-worker is running kubuntu 7.10 and has a networking issue.

Yesterday, he installed the OS off of the CD, and the machine was not connected to a network.

Today, he got network access, and he obtains his IP via DHCP.

However, his network card will be disabled upon booting and logging into KDE.  He has to manually go into the system settings every time he reboots, and he has to manually enable the interface (eth0).  Once he does, all is well.

Two questions

1-Why is this happening?

2-How can it be fixed?

Thanks in advance.

---

### Post by cmnorton on 2007-11-20
Is this system a laptop?

Is the NIC built-in, USB, or Cardbus?

There may be a bunch of reasons for this, but possible it could be that your NIC does not support carrier detection. 

Look at the output of lspci, and also look at /var/log messages and /var/log/syslog.

---

### Post by elctb on 2007-11-20
Also, make sure the file "/etc/network/interfaces" has the "auto" keyword for the interfaces you want to come up at boot time.

This is what my interfaces file looks like:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

---

### Post by kooldino on 2007-11-21
> **cmnorton said:**
> Is this system a laptop?

Nope, it's a desktop.

> Is the NIC built-in, USB, or Cardbus?

I'm pretty sure it's a PCI card.

> There may be a bunch of reasons for this, but possible it could be that your NIC does not support carrier detection. 

IIRC, it's a 3com 309-TX, which should support just about anything.

> Look at the output of lspci, and also look at /var/log messages and /var/log/syslog.

will do.

---

### Post by kooldino on 2007-11-21
> **elctb said:**
> Also, make sure the file "/etc/network/interfaces" has the "auto" keyword for the interfaces you want to come up at boot time.

This is what my interfaces file looks like:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

Roger that.  I'll check this first thing in the morning.

---

### Post by kooldino on 2007-11-21
"auto" did the trick.  Gracias!

---

