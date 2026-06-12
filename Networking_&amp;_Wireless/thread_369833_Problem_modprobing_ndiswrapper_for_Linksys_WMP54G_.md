---
title: "Problem modprobing ndiswrapper for Linksys WMP54G driver in 6.10"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by born2heelflip on 2007-02-25
Hi, I'm somewhat new with Ubuntu. I've been using it since 5.04 but never really understood it. I am using 6.10. I have loaded my Linksys WMP54GS wireless drivers off my cd. I installed them with ndiswrapper. Now, heres the problem.

<name>@Ubuntu-workstation:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper.ko): Invalid argument

So then I try it with out sudo and I get the same thing only this time instead of Invalid argument its Operation not permitted. So then I try..

<name>@Ubuntu-workstation:~$ su
Password:            (I give my pass)
su: Authentication failure
sorry.   

Does anyone know how to solve this problem or have a better way of doing this? All I want is to get on the net but my only source is through my wireless card.

---

### Post by born2heelflip on 2007-03-02
sorry to repost but I found the answer, Thanx anyway

---

### Post by Asos_Illusionist on 2007-03-13
care to share the links to your solution plz..!! ;)

---

