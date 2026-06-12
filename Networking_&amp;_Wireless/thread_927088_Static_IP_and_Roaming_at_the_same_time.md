---
title: "Static IP and Roaming at the same time?"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by sickasabat on 2008-09-22
Hi all,

I am new to ubuntu linux. I am trying to learn about web design and servers so I wanted to set up a web server on my laptop to access on the local network. While I was following a tutorial on setting up a LAMP server it said that I would need to use a static IP for the web server. 

When I switch to using a static IP I get problems when I try to connect on a different network. Is it possible to have ubuntu try to get the static IP but switch to roaming if there's a problem?

thanks

---

### Post by Iowan on 2008-09-22
> **sickasabat said:**
> Is it possible to have ubuntu try to get the static IP but switch to roaming if there's a problem? If you configure it as static, it will be static... maybe in it's own little world. Guess I'm not sure how it would know if there's a problem.
> ...need to use a static IP for the web server.  You don't *need to*, but you'll *want to*.  My LAMP server auto-configured itself for DHCP - works for now, but I must check **ifconfig** whenever I boot it - if I expect to see a web page.  I'll change that later - for now, it's a development machine.

---

