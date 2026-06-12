---
title: "Unexplained traffic: Cannot explain 1 KiB/s &quot;leak&quot;"
date: 2008-10-03
forum: Networking &amp; Wireless
---

### Post by henklaak on 2008-10-03
Hi all,

I have a Belkin F5D8053 that works just fine, after building and installing the driver of the supplier (Ralink).

There's this small annoyance that I want to understand:

The System Monitor shows a steady trickle of 1 KiB/s in incoming messages.
However: when I start up wireshark, I do not see any traffic, other than the occasional WPA authentication (once every 14 seconds).

Using "netstat --tcp --udp" gives me not a single connection.

Yet all this time, the 1 KiB/s keeps trickling in.

Any ideas what this traffic is and how I can trace it?

Cheers, Henk.

---

