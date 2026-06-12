---
title: "Gutsy DSL connection kind of times out!"
date: 2007-10-24
forum: Networking &amp; Wireless
---

### Post by y-man on 2007-10-24
Hi everyone,

I have a fresh install of Gutsy, Have been on Dapper for about a year.

In Gutsy I am experiencing this, which I have never seen with Dapper. No change in ISP, modem, line anything...

After working for a while, (about 1/4 to 1/2 hour, but may also be after some inactivity of data transfer, hard to say) Firefox suddenly start  popping "server not found" window for all destinations,

ifconfig, shows PPP all right, but any ping to well known servers like google, yahoo, even my own ISP all come back with "unknown host". 

Back to back poff/pon immediately cures the condition.

What can be missing in my setup?

Update after another day:

I found out that the mis-behaviour has nothing to do with lack of traffic. There was continuous data flow as I down and upload. it still happened.

I also tried to put a tight loop script to send one-per-minute pings to my provider, it did not miss a beat, yet Firefox and Konqueror both had the same problem of not being able to resolve the names after about 1/2 hour.

/etc/ppp/resolve.conf always had the same data, two nameserver IP addresses.





Thanks in advance.

---

