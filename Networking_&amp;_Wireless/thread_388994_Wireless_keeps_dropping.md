---
title: "Wireless keeps dropping"
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by mcflynnthm on 2007-03-20
I installed Ubuntu 6.10 last night. It was a clean install, so no residual stuff left around. I set up my wireless adapter (Linksys WUSBF54G, 802.11g adapter w/ WiFi finder) using ndiswrapper. Now, it seems if I put too heavy a load on the connection (or just when it feels particularly bitchy) the connection drops. I ran into this in Debian while using ndiswrapper; then, I would unplug the adapter, wait a minute or two, plug it back in, and reactivate wlan0. In Ubuntu, this doesn't seem to work. Any suggestions? Should I just go out and get a different, better-supported 802.11g adapter?

---

### Post by Uriel2006 on 2007-03-20
> **mcflynnthm said:**
> I installed Ubuntu 6.10 last night. It was a clean install, so no residual stuff left around. I set up my wireless adapter (Linksys WUSBF54G, 802.11g adapter w/ WiFi finder) using ndiswrapper. Now, it seems if I put too heavy a load on the connection (or just when it feels particularly bitchy) the connection drops. I ran into this in Debian while using ndiswrapper; then, I would unplug the adapter, wait a minute or two, plug it back in, and reactivate wlan0. In Ubuntu, this doesn't seem to work. Any suggestions? Should I just go out and get a different, better-supported 802.11g adapter?

I had a similar problem time ago; may you check pingin' your gateway with different packet sizes?
Maybe the problem is related to packet size and not with load, as for my case:

ping -s 100 router
ping -s 200 router
...
ping -s 1500 router

and see what happens.

If the problem is the packet size, i resolved it with the following command:

ip link set wlan0 mtu 1282

i don't know why this value is sensitive with ndiswrapper, but it just works.

hope being useful,

Uriel

---

### Post by mcflynnthm on 2007-03-20
Thanks for the tip. I'll give that a go when I get home from work :)

---

