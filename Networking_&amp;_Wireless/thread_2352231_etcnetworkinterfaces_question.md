---
title: "/etc/network/interfaces question"
date: 2017-02-10
forum: Networking &amp; Wireless
---

### Post by jrs2 on 2017-02-10
When setting a static IP address for eth0 in /etc/network/interfaces, 'nameserver' was used rather than 'dns-nameservers'

This address was also placed in /etc/resolvconf/resolv.conf.d/head using 'nameserver'

Will this cause connection issues? if an incorrect name is used on one of the lines in the stanza, is it ignored? The address is correct, just not the name.

---

### Post by chili555 on 2017-02-10
>  if an incorrect name is used on one of the lines in the stanza, is it ignored?Yes, indeed. It is ignored and not utilized. Ubuntu doesn't have a "well, I know what you meant to do so I'll do it for you" function. It is either correct or it is not.

Why not just correct it, something like:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.150
netmask 255.255.255.0
gateway 192.168.1.1
dns-nameservers 8.8.8.8 192.168.1.1
```

---

### Post by jrs2 on 2017-02-11
Unfortunately, this was done remotely and I don't have access to the device physically at this time.

So if the DNS address is ignored in /etc/network/interfaces, but it's correct in /etc/resolvconf/resolv.conf.d/head, should the device still connect?

---

### Post by chili555 on 2017-02-11
I believe 'nameserver' is the correct declaration in *head*. The correct declaration in *interfaces* is 'dns-nameservers'. To be honest, I don't know what happens if one is correct and the other incorrect. I assume that it didn't connect correctly since you haven't any access now; presumably by ssh.

---

