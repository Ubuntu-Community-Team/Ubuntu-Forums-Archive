---
title: "2 network card  with 2 diffrent gateway"
date: 2016-02-28
forum: Networking &amp; Wireless
---

### Post by farhadhelix on 2016-02-28
Hi
Im newbie to ubuntu server
This is my server situation

I have a vps with 1 network card that already have 1 ip 
I requested For another ip on another gateway they gave me the ip with a new nwtwork Card

The subnet gateway for this 2 ip is diffrent(158.58.x.x and another ip is 10.201.x.x)
i added the second ip tp the second network card in interface but i cant access the server throght second ip
Can someone please tell me what exactly i have to do to make this 2 ip accesibLe from network?
Thank you

---

### Post by newbie-user on 2016-02-29
Sounds more like a networking issue than a server issue. Your second IP is a private IP, so it's not routable over the Internet. If you have another vps within the same 10.201.x.x local network, you should be able to communicate with the server.

---

### Post by farhadhelix on 2016-03-03
the second ip was an exaple to show they are in diffrent subnet.they both can have access to internet .but i cant just make the second ip on second NIC to work.

---

### Post by SeijiSensei on 2016-03-04
Please post the results of the commands "ifconfig" and "route -n" inside [noparse]```

```[/noparse] tags.

---

