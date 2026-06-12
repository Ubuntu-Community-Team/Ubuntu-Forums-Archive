---
title: "BitTorrent privacy with TOR/Proxy"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by ShawnB391 on 2010-04-25
I'd like to send tracker communications through TOR and peer  communications through an HTTP Proxy, which BitTorrent client would best fit my needs? I was using Vuze for awhile but I wasn't able to set up the HTTP Proxy correctly, and also I don't like being forced to seed if I don't want to.

I'm new to both TOR and Proxies so any advice would be very helpful.

---

### Post by Chronon on 2010-04-25
Please read this article for an elaboration on why you shouldn't route peer traffic through TOR:
[http://www.chrisbrunner.com/?p=119](http://www.chrisbrunner.com/?p=119)

---

### Post by WinterRain on 2010-04-25
> **ShawnB391 said:**
> and also I don't like being forced to seed if I don't want to.


If everyone had that attitude, bittorrent would not work. Seeding is essential.

---

### Post by marshmallow1304 on 2010-04-26
> **Chronon said:**
> Please read this article for an elaboration on why you shouldn't route peer traffic through TOR:
[http://www.chrisbrunner.com/?p=119](http://www.chrisbrunner.com/?p=119)

He said he's connecting to the tracker through TOR while peer connections go through an HTTP proxy.  It's an interesting read though.


@ OP:
I have had the most luck with proxies with KTorrent.  I send tracker communication through an HTTP proxy and peer connections through a SOCKS proxy, both through ssh port forwarding.  That said, I agree with WinterRain that you should always seed, especially if the Seeder:Peer ratio is low.

---

### Post by Chronon on 2010-04-26
You're right.  I apparently didn't read closely enough.  

KTorrent is the client I use too.

---

### Post by ShawnB391 on 2010-04-26
> **WinterRain said:**
> If everyone had that attitude, bittorrent would not work. Seeding is essential.

I'd rather not seed until my privacy concerns are addressed. It's not that I don't want to seed, I just want to seed anonymously.

I'll look into KTorrent, thanks for the information Marshmallow1304.

---

### Post by Chronon on 2010-04-26
Maybe you should post the particular problem you're having connecting through your proxy.  As marshmallow1304 said, KTorrent has extensive options for connecting via proxy.

---

### Post by ShawnB391 on 2010-04-26
> **Chronon said:**
> Maybe you should post the particular problem you're having connecting through your proxy.  As marshmallow1304 said, KTorrent has extensive options for connecting via proxy.

I've posted my connection issue on the Vuze forum. I'm just not a big fan of Vuze and I am looking for an alternative. I'm new to proxies, do you know any articles or tutorials that could help me set up TOR/Proxy in KTorrent?

---

### Post by melkespreng on 2010-04-26
What did you upload over there at the kde world?

Anon? Nah. Hide from the cops? Nah.  Depends on the laws of the land really. 

If we knew there would be blogs all over the place.

---

