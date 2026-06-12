---
title: "2 gateways"
date: 2007-08-21
forum: Networking &amp; Wireless
---

### Post by ericbkk on 2007-08-21
Hello,

I'm newbie in Linux world.
At our office (Bangkok) we have about 50 workstations (Windows) and 10 servers (Windows too)

We are installing our first Ubuntu computer and I'm sure it won't be the last.

We have 2 internet gateways, so 25 computers use gateway 192.168.1.1 and 25 others computers use 192.168.1.18 to access internet.

It works fine. The only problem is when an ADSL loine goes down then half of our PCs can't access Internet, the users have to change their gateway,..

So I would like to setup a Ubuntu server that would be the unique gateway, let say 192.168.1.121 and will balance the load to the 2 gateways 192.168.1.1 and 192.168.1.18. Of course it should be smart enough to detect a dead gateway...

Is it possible to do with Ubuntu?

Can some one help us about this?

Thanks a lot,

Eric

---

### Post by raijinsetsu on 2007-08-21
I believe IP Tables(linux kernel firewall and routing) has load balancing. I found [this]("http://www.damia.net/comos/balance/") link after very little searching. I hope this leads in the right direction for you.

---

### Post by ericbkk on 2007-08-21
Thanks for your link. I'm reading it...

The big difference is that our server only has 1 network card. The 2 routers gateways are connected to a 1 GB switch. So I need to setup Linux as a gateway to forward to the 2 gateways using a smart balancing algorithm.


Eric

---

### Post by raijinsetsu on 2007-08-21
That can be done too, not sure on the details of the IP Tables configuration though, but here's a rough outline.

COMPA - Ubuntu Server
COMPB - Gateway 1
COMPC - Gateway 2

All computers in your network will have COMPA as their gateway.
COMPA will be configured with NAT and load balancing to dispatch packets to COMPB and COMPC.

I haven't played with IP tables in a long while, so I can't tell you the commands/config to get this to work.
You may be able to use one of the many IP tables configuration scripts/GUIs to configure this correctly.
Just know, that it is very possible.

---

