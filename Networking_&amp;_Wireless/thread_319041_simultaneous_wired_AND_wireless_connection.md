---
title: "simultaneous wired AND wireless connection"
date: 2006-12-15
forum: Networking &amp; Wireless
---

### Post by russellchamp on 2006-12-15
Currently I have a server at school that's running Ubuntu Edgy Eft which is connected up to the network with a traditional wired connection.  The network is only 10Mb/s ](*,)  so the connection is awfully slow when a couple people are on at once.
There's also a 11Mb/s *wireless* connection available that I *could* use if I chose to get a wireless card.

-> My question is this: would it be possible to utilize BOTH the wired **and** the wireless connection at the same time to give me the ability of about 21Mb/s ?
Is this just a pipe dream I have or could I do something like this?  If it isn't currently possible, would anybody be interested in working/looking into this?  After all... Hoooooray open source!

-RussellChamp

---

### Post by cracker on 2006-12-15
It is possible, but it would require a lot of routing configuration to get load balancing to work gracefully.

---

### Post by russellchamp on 2006-12-15
hmmm... :-(  There's the rub.  I don't have any access to the router whatsoever.  I can't even get the guys to do port forwarding for me so I could access by server from off campus.  (Although I can really see their reasoning in refusing me this request. ;-) )  Would it be possible at all to instead of having a **balanced** load simply a system where the first connection would be handled by one, the second connection by the other one, the third by the first again... or even (possibly the easiest way) to have a separate IP for each method of connection to manually "balance" everything?
Thanks once more!

---

### Post by cracker on 2006-12-16
That is what load balancing is. You see, without proper routing set up on both ends, the machine would just pick one connection and use it until it was no longer available, then try the other one, and use it until it became unavailable, and so on, never really using the available bandwidth. Balancing the load over multiple interfaces pretty much requires dynamic routing.

---

### Post by russellchamp on 2006-12-16
ah.  Ok.  would I still be able to at least set up a system where is handles every other incomming connection on each connection type.  (If you understand what I'm saying.)  Also, do you get seperate IPs for the different connection types or do you keep one IP?  Sorry, I'm still quite the "newb" here!

---

