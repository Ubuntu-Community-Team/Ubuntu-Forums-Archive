---
title: "can connect to net but network manager says 'no network connection'"
date: 2008-01-19
forum: Networking &amp; Wireless
---

### Post by ott0 on 2008-01-19
So I couldn't connect to the internet and then I saw that /etc/network/interfaces had no entry for eth0. So I added

```

iface eth0 inet dhcp
auto eth0

```

and now I can connect to the internet! But I find it odd that the network manager still reports 'no network connection' and the little icon in the top right of my screen shows that little error exclamation mark. If I click on it and go to manual configuration, the network settings dialogue shows 'wired connection' with a checked box next to it so and all appears to be in order...

Thanks for the help!

---

### Post by ott0 on 2008-01-23
okay well here's a tad bit more information in case *anyone* has some idea. seeing that I don't really know what I'm doing this might even be the right info.

/etc/network/interfaces looks like this

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp










auto eth0
```

network settings dialogue has two listings:
wired connction and modem connection
there is no loopback entry

---

### Post by ott0 on 2008-01-24
okay well now it's working all on it's own.

---

