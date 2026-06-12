---
title: "eth0 disappeared from network-admin"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by cclshome on 2007-06-18
How do I add eth0 back into the network-admin list of devices?  

And what config files are read by network-admin?

Details:  Feisty has been working great with a wired ethernet connection.  I started playing with wireless last week.  To get wireless working, I had to un-check eth0 in network-admin.  Device eth0 stayed in the list, but was not checked.  Wireless works great.  Now, when I plug the ethernet cable back in, eth0 is no longer present in network-applet.  Nor can I see options to add it.  Here is what I see: [http://trainweb.org/roc/tmp/pix/network-admin.no.eth0.jpg](http://trainweb.org/roc/tmp/pix/network-admin.no.eth0.jpg)

Thanks much for any suggestions.

---

### Post by tturrisi on 2007-06-18
Post the contents of your /etc/network/interfaces file.

---

### Post by apjone on 2007-06-18
open a terminal
```

sudo gedit /etc/network/interfaces

```

and add the following
```

iface eth0 inet dhcp
auto eth0

```

that should sort ya out

---

### Post by cclshome on 2007-06-21
Folks, thanks for the suggestions, but they did not help yet.  I tried several combinations of lines in /etc/network/interfaces.   It appears my network-admin is ignoring the contents of that file.

Any other suggestions?

Here are two examples.  This did not help (with the lines in any order):
```

auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

```

Nor did this:
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

```

To be clear, eth0 and TCP/IP is working fine.  My only problem is that eth0 does not appear in network-admin.  And I like using network-admin to stop and restart eth0 when I plug in to different wired dhcp networks (rather than doing ifconfig).

PS for future readers:  Do not delete the loopback lines (auto lo and iface lo inet loopback).  When I deleted them, my x desktop would not start.

---

