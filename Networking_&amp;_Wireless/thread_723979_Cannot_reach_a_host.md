---
title: "Cannot reach a host"
date: 2008-03-14
forum: Networking &amp; Wireless
---

### Post by Oswald1 on 2008-03-14
Greetings,

My problem is that I cannot reach a certain domain from my laptop at times. Anything under University of Helsinki domain helsinki.fi becomes unreachable from time to time. Sometimes it works though.

The strange thing is that this doesn't appear to have anything to do with location I'm working at. Right now I'm actually inside the university network and no connection. Just last week I tried connecting from Norway and got no connection but the other day I got it. From my home I can connect with the other comps but not with the laptop (except sometimes the laptop connects too).

When I try to ssh to a server, I get:
ssh: connect to host xxxx port 22: No route to host

When trying sshfs, I get:
read: Connection reset by peer

And when trying to browse a web page I simply get no result.

I also tried changing to a public dns server with no help and using a plain ip-address of a server doesn't help either.


I suspect there's some simple explanation for all this, but unfortunately it escapes me.

Thanks for all advice!

---

### Post by dmizer on 2008-03-14
since you are traveling around and connecting to multiple different routers, i suggest disabling ipv6 if you haven't already.

[https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?](https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4?)

try that, and see if it helps.

---

### Post by Oswald1 on 2008-03-14
Ok, did disable ipv6 and apparently it also really is disabled, "as ip a | grep inet6" returns nothing.

Maybe disabling streamlines some other things, so thanks for the tip, but still, no connection :(

---

### Post by Oswald1 on 2008-03-16
Apparently I found the reason and solution for this problem.

At times I need to connect the laptop with a wired connection at the university and for this to work I need to manually set the ip, default gateway etc. I had left those set and now that I enabled the roaming mode everything seems to work just fine.

A bit surprising that the settings of the wired interface affects behavior of the wireless one when the wire isn't even connected. Of course there's probably some good explanation for this, but now I must unfortunately start working again as I can reach the necessary resources :roll:

---

