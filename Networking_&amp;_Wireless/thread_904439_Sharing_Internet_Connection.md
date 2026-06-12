---
title: "Sharing Internet Connection"
date: 2008-08-29
forum: Networking &amp; Wireless
---

### Post by tzo on 2008-08-29
Hi I am new in linux and I have a question regarding internet connection sharing:

I want to implement an Asterisk server on an ATCA - telecom platform. On it i have 2 blades with HDD one running CentOS 4.4, one running Montavista(i think it was specially designed for ATCA).The blades are connected through the backplane of the ATCA. I can only access through rlogin the blade running Montavista(10.168.33.52/21). Then i can ssh into CentOS(10.168.33.51). I have set the default gateway for CentOS 10.168.33.52. 
From 10.168.33.52 i can ping the PC(that's running Ubuntu 8.0.4) at 10.168.33.53. This PC has also the internet connection on another NIC with 192.168.53.0/22. It's default gateway is 192.168.52.1.

The first problem is that i can't ping the PC from CentOS(do i need a static route , or another default gateway somewhere?) 
The second question is how do I get internet access for 10.168.33.52(Montavista)? Do I need NAT implemented or static route? How do I connect the /21 subnet to the /22 subnet?

Thanks

---

### Post by Iowan on 2008-08-29
Hope [this]("https://help.ubuntu.com/community/Internet/ConnectionSharing") can provide some help.

---

### Post by tzo on 2008-08-29
Thanks for replying, but the problem is that my networks have different "/" notation. The one connected to the internet has 255.255.252.0(/22) and the other one is 255.255.248.0(/21). I can't change neither one because the /22 was given to me by the network management of my company and i can't change the /21 subnet because it was defined prior. 
I know that the gateway from the /22 is 192.168.52.1, but i don't know what happens from there(if they are summarized or not).
Please help:P

---

