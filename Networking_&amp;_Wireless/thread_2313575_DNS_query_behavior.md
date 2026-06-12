---
title: "DNS query behavior"
date: 2016-02-13
forum: Networking &amp; Wireless
---

### Post by tatodc2 on 2016-02-13
Hi everybody,
I got a question regarding DNS query behavior. I just implemented a new test network at home and I'm not having the DNS to work.

I have a DMZ NW (DMZNW), Server NW (SVRNW), and a User NW (USRNW). A DNS was placed at the DMZ and another at the SVRNW. DMZ DNS is allowed to go to the Internet with UDP 53 access and the SVRNW DNS has access to the DMZ to UDP port 53.

When I point my laptop to the SVRNW DNS it doesn't work unless I give it access to the Internet, but at that DNS server there's no indication to any Internet DNS address.

I'd like to figure it out why is this happening because for "security" reasons, only the DNS at the DMZ should contact the Internet.

Thanks.

---

### Post by papibe on 2016-02-13
Hi tatodc2.

In some cases DNS also use TCP, so I'd recommend open that too.

If I understand correctly, MZNW is the upstream server of SVRNW. Is that correct?

Could you explain a little bit more what do you mean with:
> **tatodc2 said:**
> When I point my laptop to the SVRNW DNS it doesn't work
What does not work? The name resolution? LAN names? Internet names?

Note that the laptop needs more than DNS resolution to access the Internet. I would need also a route to a gateway that allows/route its traffic.

Regards.

---

### Post by SeijiSensei on 2016-02-13
As far as I know, DNS only uses TCP for zone transfers.  Queries are a UDP service.

---

