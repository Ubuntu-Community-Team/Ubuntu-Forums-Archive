---
title: "Question on connecting via the LAN"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by mdurham on 2008-01-31
Hi guys/gals, I'll try to make this as clear as I can, so here goes.

I have a 4 port modem/router connected to the internet.
I have my computer and a 4 port wireless router connected to this modem/router by cable.
I have some computers connected by wireless to the wireless router.
I know all addresses assigned to all devices (modem/router, wireless router and computers).

Assuming that shares are set up correctly, my questions are :
Is it possible to connect from the computer connected to the modem/router to the computers connected to the wireless router?
If it is possible, how?

Cheers, Mike

---

### Post by margori on 2008-01-31
Off course it is possible. The only thing you have to do is create routing tables in both router.

You have to think that there are three networks:
- wireless router = network 1
- modem router = network 2
- internet

The route table of the wireless router have to say something like this:
- Every package with IP of network 1, delivery directly
- Every other, delivery to modem router

The route table of the wireless router have to say something like this:
- Every package with IP of network 1, delivery to wireless modem
- Every package with IP of network 2, delivery directly
- Every other, delivery to internet

And that all. Every router have software to configure routing table.
I hope help.

See you.

---

### Post by mdurham on 2008-02-01
Thanks for the info margori, I'll give it a try.
Mike

---

