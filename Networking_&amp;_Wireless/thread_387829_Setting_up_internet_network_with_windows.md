---
title: "Setting up internet network with windows"
date: 2007-03-18
forum: Networking &amp; Wireless
---

### Post by Overclocked89 on 2007-03-18
Hi, I'm a new Korean Linuxer.

I set up my ubuntu machine yesterday, and I did everything I want except one thing, network.

I've been using my desktop PC as an internet server. 

I got two lan ports on my mainboard-integrated lan card(Asus M2N32), 

so I could use one port for internet and the other for my old labtop.

With my windows xp, I could set my desktop as a local host automatically.

I don't know how I can do this with ubuntu. I could connect to internet, but my labtop doesn't receive any signal from my desktop.

I don't have router and wireless network, so I should figure this out to use my labtop(windows xp pro installed).

Wired connection (eth1) Address: DHCP  -- labtop lan port
Wired connection (eth0) Address: DHCP  -- internet lan port
Labtop is in "MSHOME" Workgroup

I need HELP. Any idea?

---

### Post by noen on 2007-03-18
Hello Overclocked89

I'm very new to linux also but I will tell you what I know. I am sure the experts will be around soon. One thing that I know is that when you network windows and any unix the network adapters should be using TCP/IP and not Microsoft's proprietary netware. There may be ways around that but, as far as I know, it is best to use the tcp/ip protocol in your local lan. 

And I think you will need to set up Ubuntu as a server and internet gateway, unless you want to keep your windows box as a server. That I don't know how to do. In fact, that's why I'm here. 

That is the best I can do, I'm a novice also, so take that into account.

regards
Brenda

---

### Post by Overclocked89 on 2007-03-18
Thanks for your help, Brenda.
I tried to fix my labtop network setting using TCP/IP, but it's still not working.
I'm sure that I should fix ubuntu setting, but I don't know how..

---

### Post by noen on 2007-03-18
Try here:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Especially here:

SHH Network
[http://users.bigpond.net.au/hermanzone/p11.htm](http://users.bigpond.net.au/hermanzone/p11.htm)

---

### Post by Overclocked89 on 2007-03-19
still not solved, but thanks

I don't have a router, so I should set up my ubuntu machine as an internet gateway

someboy please HELP~

---

