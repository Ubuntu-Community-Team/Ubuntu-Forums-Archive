---
title: "Two Ethernet connections one server"
date: 2015-11-05
forum: Networking &amp; Wireless
---

### Post by mlang2 on 2015-11-05
Hi All,

Prob a bit of a daft question, but was just wondering about this.

I have a server set up at home, used for streaming video, music, storage, and also hosting a web site and mail server.

Having added a Gbit ethernet card, I was wondering Is it possible or even worthwhile to have all my local traffic from the server serviced by my Gbit connection, and the web site, mail and any other connections needed to the outside world (updates etc) served by the now unused 100Mbit Ethernet connection?

Cheers

---

### Post by SeijiSensei on 2015-11-05
Probably not.  Your outbound circuit is no doubt slower than 100Mbit, so bandwidth isn't really an issue.  

If you did want to send the local network through the server, you'd probably want to reverse the two adapters so the Gigabit one faces your local network.  However you'd either need a second router to handle the local traffic, or enable packet forwarding and masquerading on the server so that traffic can cross the interfaces and be sent outside.  Moreover you'd probably need to install isc-dhcp-server to allocate addresses for the local network.

So overall, I'd say it's more work than it is worth.

---

### Post by mlang2 on 2015-11-07
Many thanks for the reply, saves me some hassle lol

---

