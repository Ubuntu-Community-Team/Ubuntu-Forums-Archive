---
title: "ICS &amp; content filtering (DNS vs Proxy)"
date: 2008-01-26
forum: Networking &amp; Wireless
---

### Post by Crinos512 on 2008-01-26
_My situation:_

My PC is currently the DNS gateway (bind9 and ICS) serving my home network of four computers (mine, plus one for my wife, and one for each of my 2 young teen sons). I use a host file on each of the clients to block ads, viruses, and pr0n... but I would like to pull the filtering back to the gateway to make updating the filters easier and to have some kind of logging. (I was a teenager once too.)

_My Question:_

I have looked a little into using a proxy to acheive these goals, but feel my head spinning at the possibilities. To that end, I ask for the board's opinion... do you think I should:

[LIST=1]
[*]Stay with DNS masquerading (...there may be a way to do what I want without using a proxy)
[*]Use a Basic Squid proxy, possibly with addons.
[*]use a non-Squid proxy option (please make suggestions)
[*]Other
[/LIST]

---

### Post by bwtranch on 2008-01-27
Seems like Option #1 is working for you quite well. I don't think I would change anything.

---

### Post by Crinos512 on 2008-01-28
So, um.... anyone else have a opinion?

<Added the Poll>

---

