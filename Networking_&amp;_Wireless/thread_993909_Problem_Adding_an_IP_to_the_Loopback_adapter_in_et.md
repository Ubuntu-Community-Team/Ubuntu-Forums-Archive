---
title: "Problem Adding an IP to the Loopback adapter in /etc/network/interface 8.04 LTS"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by MikeDixson on 2008-11-26
Hi all,

I'm encountering a strange little foyble of Ubuntu/Debian/*nix.

**Goal**: To use an IP address that is used to access one of two servers internally via our load balancer and add it to the loopback adapter so that exim runs listening on that address instead of 127.0.0.1 and sending out on the server's address.

**Current Setup:** Traffic to 10.0.9.33 hits our loadbalance and get's directed to 10.0.11.33 or 10.0.12.33.
Exim on those servers is set up to listen on 127.0.0.1 but when it makes an SMTP connection to other SMTP servers it goes out on the 10.0.x.33 address is NAT'ed through out FW/Router.

As such I've been trying to add 10.0.9.33 to the loopback adapter. What I'm finding is the following.

**Problem Description:**
If I add the ip address to the loopback adapter using ifconfig command all works fine but the change is not persistent between boots of course.
```
ifconfig lo:0 10.0.9.33/8
```

If I add the configuration to /etc/network/interfaces whilst the config is read ok by ifup and implemented all traffic to **all** interfaces is dropped. My interfaces file contains the following for the loopback adapter:
```

auto lo
iface lo inet loopback

auto lo:0
iface lo:0 inet static
address 10.0.9.33
netmask 255.0.0.0

```

Then I use ```
ifup -a
``` to bring up the interfaces from the /etc/network/interfaces file.

I'd be grateful for any feedback on why one method does work and the other doesn't and also some proposed solution for keeping this ip address persisten.

---

### Post by betweenbrain on 2009-07-12
Hi Mike,

I realize that this is a fairly old thread ... but on the off-chance you get ... did you have any luck? I'm in a similar situation and kind of stuck myself. 

Thanks for any help anyone can offer.

Best,

Matt

---

### Post by Iowan on 2009-07-12
Dunno if "iface lo:[COLOR="Red"]1[/COLOR] inet static" would make it any happier?

---

### Post by mikelittle on 2009-09-09
> **Iowan said:**
> Dunno if "iface lo:[COLOR="Red"]1[/COLOR] inet static" would make it any happier?

Iowan,
Thanks, this worked for me. I now have a 10.10.0.x IP address pointing to my local Apache server and I can reproduce the client's set-up exactly!


Mike

---

### Post by Iowan on 2009-09-09
Wow! Echos from the past... glad it helped!

---

