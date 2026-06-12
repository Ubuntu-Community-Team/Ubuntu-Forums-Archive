---
title: "IPv6 Repositories?"
date: 2008-03-06
forum: Networking &amp; Wireless
---

### Post by FliesLikeABrick on 2008-03-06
Can anyone point me to some decent Ubuntu repositories that are available via IPv6?  I found a very, very old thread on the forums with a list of a few, but they all either didn't work or gave speeds under 10KB/s, mostly around 2KB/s.

I've recently been deploying IPv6 tunnels at home and for some servers I manage.  I would love to provide some demand on IPv6 repos.

---

### Post by netztier on 2008-03-06
> **FliesLikeABrick said:**
> Can anyone point me to some decent Ubuntu repositories that are available via IPv6?  I found a very, very old thread on the forums with a list of a few, but they all either didn't work or gave speeds under 10KB/s, mostly around 2KB/s.

I've recently been deploying IPv6 tunnels at home and for some servers I manage.  I would love to provide some demand on IPv6 repos.

In Switzerland, mirror.switch.ch (aka ch.archive.ubuntu.com) is reachable:

```
marc@blaze:~$ nslookup
> set type=AAAA
> ch.archive.ubuntu.com
Server:         127.0.0.1
Address:        127.0.0.1#53

Non-authoritative answer:
ch.archive.ubuntu.com   canonical name = mirror.switch.ch.
mirror.switch.ch        canonical name = moon.switch.ch.
moon.switch.ch  has AAAA address 2001:620:0:8:203:baff:fe52:38e6
moon.switch.ch  has AAAA address 2001:620:0:8:203:baff:fe52:38e5

```

It's quite fast - at least around here ;-), I don't know where you'd be connecting from, though.

best regards

Marc

---

### Post by FliesLikeABrick on 2008-03-06
Thanks, that is far faster than the ones I've found so far (170KB/s).  I'm hitting it from a number of US machines, so any US/Canada or otherwise closer mirrors would be awesome.

edit: I found a couple on my own, it turns out a few of them on the ubuntu mirrors list ([https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)) have ipv6 addresses.  These include (in the US portion):
- [http://lug.mtu.edu/ubuntu](http://lug.mtu.edu/ubuntu) (ftp and rsync also)
- [http://mirrors.cat.pdx.edu](http://mirrors.cat.pdx.edu) (ftp and rsync also) - the ipv6 seems a bit flaky on this one, it refuses the connection sometimes.  Hopefully they'll clean this up.  When it does work, it is damned fast.  It saturated my 10mbit connection (over a v6 tunnel)

If anyone knows more, definitely post them here!

---

