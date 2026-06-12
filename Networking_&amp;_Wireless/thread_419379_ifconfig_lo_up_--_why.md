---
title: "ifconfig lo up -- why?"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by potterzot on 2007-04-22
I have recently realized that my local net thingy isn't starting automatically.  I haven't changed anything in /etc/rc2.d, and I've checked on /etc/network/interfaces.  Nothing seems amiss.  But lo isn't started on boot.  If I want to start apache, I first have to ifconfig lo up to get it up, and then apache works great.  The same goes for giFT.  I spend a gazillion hours trying to figure out what was wrong before I did a random ifconfig and realized that lo wasn't starting on boot.

Anyone know why?  Is this a new ubuntu policy?  How can I change things so that lo starts on boot once again.

---

### Post by ssam on 2007-04-23
can you post you /etc/network/interfaces

does it have

```

# The loopback network interface
auto lo
iface lo inet loopback

```

---

