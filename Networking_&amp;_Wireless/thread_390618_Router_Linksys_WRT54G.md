---
title: "Router Linksys WRT54G"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by narvus on 2007-03-22
Hi! I have to use a router, but I've never done it before and I don't know how.

I'll connect the router to my computer (RJ 45). the router must let several IP phones to communicate with the asterisk server, which installed in the computer. Connection between IP phones and router is wireless.

How can I make this work?

I'll appreciate any help you can give me.

Thank you.

---

### Post by tatster on 2007-03-26
HI Narvus,

I also have a WRT54G so I might be able to help!

I hope I've understood your post correctly.

So you have a PC running the Asterix server software connected by RJ45 lead to the router, and you have IP phones wirelessly connecting to the router, and then some sort of internet connection as well.   Is this correct?

If so, then as long as you have DHCP setup somewhere, and the wireless part setup, then the phones will be treated just as devices on the same local LAN as the PC.

Can you ping the phones from the PC?

Tat.

---

### Post by narvus on 2007-03-28
Hi, thanks for your answer.

I'm not working with the router and the Ip phones yet. I'm having some problems with ubuntu...

the configuration is just like you said: wireless internet connection, and a router wired to the pc where asterisk server is running. The ip phones should connect the router wirelessly. I'm using dhcp. I'm working in a company, would it be the same LAN?

---

### Post by tatster on 2007-03-28
Hi,

Yes, by default any wireless devices that associate with the WRT54G will be on the same LAN as devices connected to the LAN switchports on the router.

I say by default because you can change things on the router but out of the box all LAN and wireless is the same LAN.

You say you are having problems with Ubuntu - do you mean with the Ubuntu box and the router?  If so, what probs?

Tat.

---

