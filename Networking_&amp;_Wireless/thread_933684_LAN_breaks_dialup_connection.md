---
title: "LAN breaks dialup connection"
date: 2008-09-29
forum: Networking &amp; Wireless
---

### Post by BrantlyMedders on 2008-09-29
Unfortunately, I have to use dialup to access the internet.  However, I just got a netgear router to enable filesharing/etc between my ubuntu machines.

I use Network Manager to do my dialup, and have the following options enabled for my PPP connection:

Set modem as default route to internet
Use the Internet Service Provider nameservers
Retry if the connection breaks or fails to start

When I plug into the router, however, my dialup connection ceases to function.  As far as I can tell it stays connected, but nothing works.  (I'm unable to ping any external ip nor resolve domain names).

I guess Network Manager (or something) sees the ethernet connection as the default gateway to the internet.

Can someone help me please?

---

