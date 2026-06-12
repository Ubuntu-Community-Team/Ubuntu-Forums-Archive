---
title: "Dynamic DNS"
date: 2018-03-09
forum: Networking &amp; Wireless
---

### Post by zerius on 2018-03-09
Hello, i am trying to set up a dynamic dns for my Ubuntu server
my router is a Sky Broadband router and i've found the setup page im just unaware how setting up a dynamic DNS works i also heard their are paid methods and free alternatives overall i just need some help figuring things out

---

### Post by QIII on 2018-03-09
Hello!

Most of the work is done outside of your router -- outside your modem even.  If you use a paid dynamic DNS service, all you have to worry about is installing the update client, forwarding a port and picking your domain name.  A good service will help with instructions for that. The dynamic DNS service will route traffic from that domain to the IP assigned from your ISP.  Your update client will periodically contact the dynamic DNS service.  If the IP lease with your ISP has expired and a new IP has been assigned, the service will update their records and route traffic to the new IP.  That will all happen transparently to you.

I'm not going to suggest a particular paid DDNS service, but you can certainly google one with the terms

```
dynamic dns service
```

Don't get too wrapped around the axle about what *you* have to do.  It's very little.  The service will do the heavy lifting for you.

---

### Post by zerius on 2018-03-09
> **QIII said:**
> Hello!

Most of the work is done outside of your router -- outside your modem even.  If you use a paid dynamic DNS service, all you have to worry about is installing the update client, forwarding a port and picking your domain name.  A good service will help with instructions for that. The dynamic DNS service will route traffic from that domain to the IP assigned from your ISP.  Your update client will periodically contact the dynamic DNS service.  If the IP lease with your ISP has expired and a new IP has been assigned, the service will update their records and route traffic to the new IP.  That will all happen transparently to you.

I'm not going to suggest a particular paid DDNS service, but you can certainly google one with the terms

```
dynamic dns service
```

Don't get too wrapped around the axle about what *you* have to do.  It's very little.  The service will do the heavy lifting for you.

Okay thanks
i found a service called noip.com it was actually suggested on my router so i checked it out and i think i can make my way from here Thank you.

---

### Post by QIII on 2018-03-09
Good!

Always, always consider security and protect yourself.  That's too big a subject to go into here, but study up a bit and work towards getting your system hardened against attack.

Cheers!

---

