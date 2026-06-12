---
title: "can't fix my /etc/network/interfaces"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by rossgemuend on 2006-11-18
I am attempting to install my iwp3945 on my latitude d820 with edgy installed so I tried following some tutorials. A few tutorials have me comment out everything in my /etc/network/interfaces file except for:

auto lo
iface lo inet loopback

Anyway, the tutorials didn't do what they were supposed to and I reset my /etc/network/interfaces file back to it's original and rebooted. The problem is that none of my network connections work now. Under System->Administration->Networking, I only see "Wired connection" which used to work but now doesn't. Also, my wireless connection (which has never worked) is now missing from System->Administration->Networking too. Does anyone know how to fix this?

Here is my current /etc/network/interfaces file

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface eth0 inet dhcp

auto eth0

```

---

### Post by K.Mandla on 2006-11-18
Try looking at /etc/iftab.

```
sudo nano /etc/iftab
```
In general, those are the identifiers assigned to your network cards, with their MAC addresses listed too. Those are the identifiers that should appear in your /etc/network/interfaces file.

As an example, here's my /etc/iftab. ...
```
# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

eth0 mac 00:20:e0:68:0a:75 arp 1
eth1 mac 00:06:25:11:29:2b arp 1
```
And here's my /etc/network/interfaces. ...

```
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1

# iface eth1 inet dhcp
iface eth1 inet static
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any
        wireless-key1 xxxxxxxxxx
        address 192.168.1.99
        netmask 255.255.255.0
        gateway 192.168.1.1
```
eth1 is my wireless card. I don't bother with the wired connection (eth0), so there's nothing in my /etc/network/interfaces to configure it. 

In my case, I use a static IP for this laptop's wireless connection. If you just want dhcp, you can keep the default line

```
iface eth1 inet dhcp
```
And throw out the other mess.

I guess my best suggestion is to make sure the identifiers in /etc/iftab match what you're configuring in /etc/network/interfaces.

---

