---
title: "Can see network devices but no connection to Internet?"
date: 2007-06-26
forum: Networking &amp; Wireless
---

### Post by Mr_Moonlight on 2007-06-26
Hi!

I have the latest version of Ubuntu in a dual boot with windows.

Install went smooth and when I boot everything comes up nice.

HOWEVER I cannot connect to the internet. I have a Netgear ADSL router/modem which is plugged into a Linksys wireless broadband router. The computer is wired to the Linksys.

If I put in the IP addresses of either of the routers I can access them just fine and change any settings or whatever. BUT when I try to access a web page it simply doesnt load. I get a timeout error.

The modem is working as I can access it wirelessly from my laptop, so there is no issue there...

The connection IS enabled in Ubuntu and on DHCP so should be just fine...

Any ideas?

---

### Post by sadaraine on 2007-06-26
Your problem appears to be related to DNS.  Check to make sure you haven't specified DNS anywhere in your network settings.  Also, check the DNS settings on your modem and router.  You typically shouldnt' need specific DNS settings as they are normally assigned by your ISP (YMMV...different strokes for different folks).

---

### Post by Mr_Moonlight on 2007-06-27
Perfect THANKS!

Worked first time!

I DID need to specify the DNS passed on from the ISP.... No idea why but when I did the connection worked.

So Thanks again.

Dan

---

