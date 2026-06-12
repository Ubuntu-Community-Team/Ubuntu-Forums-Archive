---
title: "Help! Wireless config with WEP from CLI"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by DJ Wings on 2007-08-06
I'm stuck in a command line on one system, with no connectivity from it, and no X. I can download .deb files, and I've got my Intel PRO/Wireless 3945 working. But the network I'm on needs a WEP kep (ascii) to work (which I have). Which file should I edit to add the key?

---

### Post by Nythain on 2007-08-06
i just edit my /etc/network/interfaces and add the lines like such
```

auto ra0
iface ra0 inet static
    address 192.168.1.138
    netmask 255.255.255.0
    network 192.168.1.0
    broadcast 192.168.1.255
    gateway 192.168.1.1
    wireless-essid XXXXX
    wireless-key XXXXXXXXXXXXXXXXX

```
there are also iwconfig commands you can use to set it up

---

### Post by DJ Wings on 2007-08-06
Thanks, I've got it working.

---

