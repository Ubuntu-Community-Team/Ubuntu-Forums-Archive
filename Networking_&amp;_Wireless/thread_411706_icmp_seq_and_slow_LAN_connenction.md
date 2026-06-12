---
title: "icmp_seq and slow LAN connenction"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by sc7090 on 2007-04-17
Hi to everybody,
i'm trying to setup a LAMP server with ubuntu server
but, before working on programs, i'd like to resolve a connection problem.
The NIC (realtec 8139 base cards) was correctly recognized, i disabled the IPV6 protocol, but
the connection is still very slow.
 The LAN, right now, is very small: there
is this LAMP server, a switch and a laptop running win2k.
If i ping the laptop the icmp_seq shows that some values get lost
(example:1, 2, 3, 6, 7, 11, ...): the avereage is about 50% of the values lost...
If i try an ftp connection this is terribly slow.
Any suggestion?
Please note that i'm a newbie so don't be afraid to give me simple suggestions.
My next step will be to connect the two computers via crossover cable so
i bypass the switch.
Thanks everybody for your attention and for any suggestion.

---
Claudio

---

### Post by sc7090 on 2007-04-20
The problem was the switch. Now, with the cossover ethernet  cable ping works fine on both the directions.

---
Claudio

---

