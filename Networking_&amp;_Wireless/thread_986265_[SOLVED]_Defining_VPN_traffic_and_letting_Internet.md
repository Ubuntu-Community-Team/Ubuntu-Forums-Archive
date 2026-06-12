---
title: "[SOLVED] Defining VPN traffic and letting Internet breakout locally"
date: 2008-11-18
forum: Networking &amp; Wireless
---

### Post by Insane_Homer on 2008-11-18
Hi there,

Thanks to some very useful posts in the past few days I've got my VPN(PPTP) to my work networked connecting again.

However, I have a small problem, due to some incompetence from our networking team  (outsourced & managed) they are unable to route internet over the VPN connection (the hows, whys and wherefores I've given up on since I know them to be incompetent).

The problem is that when I'm connected to the VPN all traffic is routed down the VPN tunnel = no internet since they can't route it out again.

How do I route internet traffic out through my Wireless Router (local default gateway) and then only route traffic for my work network down the VPN tunnel?

I need to route only  10.2.x.x, 10.1.0.0 down the tunnel. Everything else can break out to the internet locally.

---

### Post by jakommo on 2008-11-18
I need the same thing, in 8.04 there was an option "only use vpn for these adresses" but I cant find it in 8.10.
btw. can someone tell me where to find a description of all the new options in networkmanager-pptp?

Cheers jakommo

---

### Post by Insane_Homer on 2008-11-21
anyone?

---

### Post by Songwind on 2008-11-23
I recently did all the homework on this issue, and wrote up the post on how to do it over at my blog.

[http://dragonseptarts.com/blog/?p=159](http://dragonseptarts.com/blog/?p=159)

---

### Post by Insane_Homer on 2008-11-24
> **Songwind said:**
> I recently did all the homework on this issue, and wrote up the post on how to do it over at my blog.

[http://dragonseptarts.com/blog/?p=159](http://dragonseptarts.com/blog/?p=159)

Woo Hoo! thanks very much, I can't believe it was that simple :lolflag:

---

### Post by Songwind on 2008-11-24
Glad to help :)

---

### Post by jakommo on 2008-11-24
I tried it now and it works, thank you.
I'm looking forward to your blog post about the dns stuff.
Greez
Jakommo

---

### Post by Songwind on 2008-11-25
Post #2 about BIND is up now, too.
[http://dragonseptarts.com/blog/?p=165](http://dragonseptarts.com/blog/?p=165)

---

