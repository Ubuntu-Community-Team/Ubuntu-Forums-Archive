---
title: "Connect to Ubuntu through the internet?"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by taylor102387 on 2009-02-09
Alright, I have set up a java based vnc viewer and it works great on my lan. Now I want to be able to connect through the web! But, sadly, when I go to whatismyip.com and connect using that ip, it goes to my router. If it helps, I have a WRT310N Linksys router.:)

---

### Post by alphacrucis2 on 2009-02-09
> **taylor102387 said:**
> Alright, I have set up a java based vnc viewer and it works great on my lan. Now I want to be able to connect through the web! But, sadly, when I go to whatismyip.com and connect using that ip, it goes to my router. If it helps, I have a WRT310N Linksys router.:)

I presume you will have to set up port forwarding on your router.

---

### Post by taylor102387 on 2009-02-09
No. Care to explain? Because my ip to my computer does not require a port, just the ip.

---

### Post by alphacrucis2 on 2009-02-09
> **taylor102387 said:**
> No. Care to explain? Because my ip to my computer does not require a port, just the ip.

If your ubuntu machine has an RFC ip address such as 192.168.x.x or 10.x.x.x, you can't talk direct to those over the internet as they are specifically for private use only. On the other hand your router has a public address that can be reached over the internet. You configure your router such that whenever it receives a tcp packet on whatever port you have configured vnc to listen on, it forwards the packet to the private address of your PC. It's a standard function that pretty much all modern routers can be configured to do. Have a look at the linksys manual under port forwarding.

Read this for an explanation:  [http://en.wikipedia.org/wiki/Port_forwarding](http://en.wikipedia.org/wiki/Port_forwarding)

The default port for vnc is something like tcp 5900

---

