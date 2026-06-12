---
title: "Set differenct DNS for each user account"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by MichiganMan on 2007-10-27
I want different DNS servers specified between different user accounts (ie. Tom on OpenDNS, Sue using the ISP's DNS)

Is this possible on a single system?

---

### Post by kidders on 2007-10-30
Hi there,

Setting user-specific DNS services is not possible (and for very good reasons). I wouldn't recommend trying to engineer it.

What are you trying to do, exactly? Perhaps there is another way of achieving the same effect.

---

### Post by MichiganMan on 2007-10-30
Hi. Thanks for the answer. :)

What I wanted to do was utilize the Adult Site Blocking of OpenDNS when my kids were using their accounts, and my ISP's DNS servers when the adult accounts were in use.  OpenDNS would be ideal as it would help keep them in kid safe(r) areas of the web while being resource neutral.

---

### Post by kidders on 2007-10-30
Ahhh...

I would say DNS is the wrong level to be approaching that on. A proxy with a content filter might be worth considering. You see, any modification you made to resolv.conf (the place your nameserver is stored) would be system-wide.

---

### Post by FXEF on 2007-10-30
> **MichiganMan said:**
> Hi. Thanks for the answer. :)

What I wanted to do was utilize the Adult Site Blocking of OpenDNS when my kids were using their accounts, and my ISP's DNS servers when the adult accounts were in use.  OpenDNS would be ideal as it would help keep them in kid safe(r) areas of the web while being resource neutral.

I don't think you understand what DNS servers are used for. The DNS server translates the domain names to an IP address. My advice is both _you_ and the kids stay away from adult sites.
:-({|=

---

### Post by kidders on 2007-10-31
> **FXEF said:**
> I don't think you understand what DNS servers are used for.I disagree. Intentionally causing name resolution failures (by using specialised services specifically designed not to look up improper hostnames) can be remarkably effective at fending off viruses, unsolicited porn, and a variety of other things. It's also waaaaaay easier to set up than a content filter. So I'd say MichiganMan knows exactly what he's talking about hehe.

In his case however, the problem is that (a) denying his children access to certain material this way would impact his own web browsing, and (b) these "doctored" DNS services are not good at stopping *deliberate* attempts to access things a parent might be concerned about.

---

### Post by FXEF on 2007-10-31
> **kidders said:**
> I disagree. Intentionally causing name resolution failures (by using specialised services specifically designed not to look up improper hostnames) can be remarkably effective at fending off viruses, unsolicited porn, and a variety of other things. 

Kidders,

I went to the OpenDNS site and now see where they now provide a filtering service. I have used the OpenDNS on several boxes but never used the new filtering service. Things are changing fast, may be too fast. I guess I'm still living in the days of the /etc/host and localhost loopback.

---

### Post by MichiganMan on 2007-10-31
> **FXEF said:**
> I don't think you understand what DNS servers are used for. The DNS server translates the domain names to an IP address. My advice is both _you_ and the kids stay away from adult sites.
:-({|=

Actually I do understand what DNS servers are used for, as does OpenDNS, which is why they offer free adult content blocking for those that use their servers (perhaps *they* don't know what dns servers are for...) As for the adult sites you suggest I stay away from, the ones I would be concerned about include thesmokinggun.com (blocked for adult themes) tmz.com (blocked as a lingerie site) and ruthlessreviews.com (a movie review site whose perspective I enjoy, blocked for adult themes)

Your concern for me is appreciated, but you may overestimate my sensitivity to the level of material on these sites.

---

