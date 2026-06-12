---
title: "Merging two connections"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by ruza on 2008-09-07
Hello all,
I have two connections, one is broadband cable connection, and one is wireless. I would like to merge them so I can use both of them, to speed up my p2p download... Is there any way of doing that? Thank you.

---

### Post by fwre01 on 2008-09-07
are these to two different internet connections??

---

### Post by ctsdownloads on 2008-09-07
I know people used to do this with ISDN, but that worked because it was the same approximate speed. Adding a slower connection to benefit a wireless one does not sound plausible.

This said, it might be possible to get Iptables can be used to set up multipath routing, but I am not sure about merging them.

---

### Post by fwre01 on 2008-09-07
it depends, (its sounds unlikely at the moment) just to clarify, could you explain more about how this is set up?

---

### Post by ruza on 2008-09-09
Ok, let me explain. I have two separate connections... One is my cable broadband connection, and that is my main connection... But also I have wireless network that I can use to connect to internet. I would like to use them all to download some torrents... Is that possible?

---

### Post by fwre01 on 2008-09-09
You wont be able to do that, becasue you will appear on the net as two seperate IP addresses. You were right when describing ISDN, you can use PPP multilink to effectively bond multiple channels, but this is all acheived in one box, with one IP address.

Maybe you could acheive load balancing by running 2 virtuals machines, both with torrent programs running, but one VM using one connection, and the other VM using the other......but maybe a bit awkward

---

### Post by ruza on 2008-09-09
Well too bad for that, I really hoped I can do that... I thought, knowing about nature of peer to peer, that two ip adresses should not be problem when peer to peer download and networks, but guess I was wrong...

---

