---
title: "Not getting router announcements in Gutsy"
date: 2008-01-14
forum: Networking &amp; Wireless
---

### Post by juanjobnt on 2008-01-14
Hi, all.
I recently set up an IPv6 tunnel to freenet6.net on a host in my network. I set up radvd on that host. But my laptop, running Ubunty Gutsy, doesn't pay attention to the router advertisement packets (though I can see them come in with radvdump).
My colleagues, in the same network, use the same version of Ubuntu as I do, and some have even the same hardware.
I have made sure ipv6 works in my laptop, as I am able to set up the ipv6 network by hand. But what should happen is that the laptop acknowledges the router advertisement packets and autoconfigures my network interface (which, by the way, is an Intel 82573L, works OK with IPv4)
As I said, I don't think it can be blamed on the hardware, but I basically have run out of ideas, after devoting several hours and a great deal of googling to try to solve this.
I'd really appreciate if someone could give me a hint about where to look.
Thanks to all for your attention.

---

### Post by juanjobnt on 2008-01-15
Partially solved. It occured to me this morning that it may be related with the expiration of assigned IPv6 addresses.
You see, before installing the tunnel service on the other machine I tested it (and the associated freenet6.net account) on MY machine. Therefore I was assigned a public IPv6 address. This IP address is now assigned to the other machine, and I guess my laptop wasn't eager to get a different address until after the assigned IP address expired.
This morning (some 14 hours after my last attempts and around 24 hours after I moved the tsp client to a different machine) I am getting a public IPv6 address. So I haven't had the opportunity to test whether I was right or no.
I hope this is valuable for anyone that encounters the same problem as me.
And now with the remaining problem: why am I not getting the IPv6 gateway address? I have to investigate it first. If I find out what the problem is, I'll post again, in the hope that it's useful for someone else.
Thanks for reading this :-)

---

### Post by juanjobnt on 2008-01-15
Finally solved. It turned out that the tspc had died on the router machine. That's the reason why I could ping6 it, but not the public internet (such as [www.kame.net](www.kame.net), [www.6bone.net](www.6bone.net), etc)
All in all, much ado about nothing. Sorry for the waste of bandwidth.

---

