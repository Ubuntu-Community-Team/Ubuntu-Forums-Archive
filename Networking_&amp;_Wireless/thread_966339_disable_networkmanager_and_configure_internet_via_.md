---
title: "disable networkmanager and configure internet via etc/interfaces"
date: 2008-11-01
forum: Networking &amp; Wireless
---

### Post by hachel on 2008-11-01
hi,
because there is that problem that the nm doesn't keep your changes i tried something i found in another forum. it said you could disable or remove the nm and instead edit your interfaces-file.
so far my interfaces looks like this:
```
auto lo
iface lo inet loopback

```
I added this:
```
auto eth0
iface eth0 inet static
        address 192.168.1.5
        netmask 255.255.255.0
        network 192.168.1.1
        broadcast 192.168.1.255
        gateway 192.168.1.1
```
(now, i don't know what broadcast is, never had to state it anywhere before)
when i reboot, my interet doesn't work anymore. under system->administration->network tools my eth0 is listed with the correct ip.
when i type sudo /etc/init.d/networking restart it tells me it can't bring up eth0.
any help?

thanks

---

### Post by whoop on 2008-11-01
I tried that hachel (and alot of other things). Didn't work for me either.
I find it so strange that this huge problem is not getting (enough) attention.

I mean COMMON, no static ip? that's kind of a necessity for some. I thought one of ibex's main goals was connectivity? I must have been wrong :-(

---

