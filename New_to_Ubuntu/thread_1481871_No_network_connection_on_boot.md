---
title: "No network connection on boot"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by Ashmadia on 2010-05-13
Hi,

I'm sure it's something I haven't configured properly... but I have no network connection when ubuntu first starts. I have to disable networking, then re-enable it, and the network connects just fine after that, until the next reboot. Any idea what I'm doing wrong?

I'm running lucid and have a realtek network card (integrated into motherboard).
Thanks!
Ash

---

### Post by hannaman on 2010-05-13
I had the same problem.  I found that eth0 was not in my /etc/network/interfaces file so I added it.
Here is what my /etc/network/interfaces looks like now:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
```
After that my network came up on boot, but network-manager applet disappeared.
To fix that I edited /etc/NetworkManager/nm-system-settings.conf and changed "managed=false" to "managed=true" under the [ifupdown] heading.

---

### Post by Iowan on 2010-05-13
Do you have the "Available to all users" box checked?

---

