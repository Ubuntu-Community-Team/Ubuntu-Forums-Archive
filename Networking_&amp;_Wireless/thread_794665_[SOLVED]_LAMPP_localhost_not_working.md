---
title: "[SOLVED] LAMPP localhost not working"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by fontenot_1031 on 2008-05-14
Got Lamp installed and fixed the problem with the mysql.server file pointing to #!/usr/bin/sh however localhost still does not load on my computer.

here's the twist though :(

Little different though due to some hacks I had to do /etc/network/interfaces.  I modified that file so that I could get ndiswrapper to work here is my current /etc/network/interfaces.  If anyone knows how I could get LAMPP to work along with my wireless configuration.  I used this guide to get wireless working by the way [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)
```
auto lo
iface lo inet loopback

auto lo
iface lo inet loopback

```

---

### Post by mmichalik on 2008-05-14
what errors are you getting, exactly?

---

### Post by fontenot_1031 on 2008-05-14
> **mmichalik said:**
> what errors are you getting, exactly?
Localhost just kinda times out.  I don't know if this has anything to do with the problem but Azureus complains that the port on 127.0.01:3386 (I get that even when LAMPP is not running) or something like that is not open.

---

### Post by jetsam on 2008-05-14
The duplicate interface definitions will cause it to fail when networking is started.  Try taking one of them out.  The file should just look like this:
```
auto lo
iface lo inet loopback
```
Then restart the computer.  

I'd suggest "sudo /etc/init.d/networking restart," but that just caused my desktop to freeze when I was testing this, so you're probably better off restarting the computer.  

The Azureus problem I think is also caused by no working localhost.

---

