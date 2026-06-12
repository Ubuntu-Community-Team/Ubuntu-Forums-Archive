---
title: "Upload Speed"
date: 2005-08-18
forum: Networking &amp; Wireless
---

### Post by JediSpam on 2005-08-18
My upload speed is absolutely horrible from my XP Pro to Ubuntu. I have a linksys 4 port router. It is ridiculous. When I sent a file over on msn it's ridiculously slow and from another xp pro machine to my xp pro computer it's like instant. I guess it has to do with Ubuntu's drive on my network card.

---

### Post by DJ_Max on 2005-08-19
If you are having the same issues with XP, Ubuntu isn't to blame. Ubuntu being on your HD shouldn't effect your network card.

Sending files on your local network will always be faster. Sending files over WAN will depend on your ISP, as well as the network of the address you're sending it to, and distance. When you mean slow, what are the speeds?

---

### Post by bogyit on 2005-08-19
@JediSpam: for the MSN upload problem it's a Gaim related problem, it doesn't depends on Ubuntu:

> [i]**MSN File Transfer**
The MSN protocol supports several different file transfer methods which are used under different network conditions. **Currently, Gaim only supports a method that transfers through the MSN servers.** While this is guaranteed to work under any network condition (even if both sides are behind NAT devices, for instance), it is unbearably slow.

Your task this summer is to implement at least one other MSN file transfer protocol: one that directly connects the two clients. You will also need to provide a mechanism that will easily fallback on the slow through-the-server method in case your new method fails. This may involve reverse engineering, but there are other free software implementations you may use as a reference.[/i]- [http://gaim.sourceforge.net/summerofcode/](http://gaim.sourceforge.net/summerofcode/)
bye :)

---

### Post by JediSpam on 2005-08-26
thanks for the reply.

---

### Post by s_p_a_r_k_y on 2005-08-26
send files over samba (File sharing) or winSCP

---

