---
title: "RTL8187 Weirdness"
date: 2007-10-26
forum: Networking &amp; Wireless
---

### Post by FlyingIsFun1217 on 2007-10-26
Hey!

New issue, I have NEVER had this issue with the card, even with Gutsy.

Some things with the wireless work (such as; going to ogre3d.org, irrlicht3d.org, mech.eltaweb.net, private servers [not google, yahoo]), and others don't (such as; google.com, mail.google.com, mail.yahoo.com, [http://www.alsbonsai.com/](http://www.alsbonsai.com/)). The most interesting part about everything is, all of the non-working (in Ubuntu 7.10) sites work when I boot into windows' partition. :/

I haven't done anything new lately, so I'm really not quite sure what is going on here. Where should I start to figure this thing out?

FlyingIsFun1217 :)

---

### Post by kevdog on 2007-10-26
Sounds maybe like a dns problem to me.  Have you tried to reach those troubled sites by IP address rather than by URL name??

---

### Post by FlyingIsFun1217 on 2007-10-26
> **kevdog said:**
> Sounds maybe like a dns problem to me.

Thats what I thought right away too, but there's two problems:

1)    Windows uses the same DNS info (since it's a modem that has the wireless built in, 2WIRE), and it works just fine

2)    I usually use OpenDNS, set at the router level to be used. When I started having issues and thought it might be the DNS servers, I switched to my ISP's default DNS servers (to be set automatically by the router). Doing this does not change anything.

Thanks for the help!
FlyingIsFun1217

---

### Post by FlyingIsFun1217 on 2007-10-27
Bump.... :frown:

FlyingIsFun1217

---

