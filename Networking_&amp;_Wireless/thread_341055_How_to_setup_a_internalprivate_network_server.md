---
title: "How to setup a internal/private network server"
date: 2007-01-18
forum: Networking &amp; Wireless
---

### Post by Ionix on 2007-01-18
Hi, I'll like to first explain what is the kind of network I am talking about, it's not the normal LAN connection i am referring to.

I was working in a military camp, and the networking they have interest me alot... and I am trying to learn how to setup one. Please kindly advise.

The network is not connected to the world wide web... but there are a lot of url available for linking to different unit's homepage. The url comes with very strange protocol.. it's not http:// but some other "strange" protocol, erm... I think it's ift:// etc.

Beside this they also have internal email network, where their "@domain.com" also look very different from the standard emaill address we can see on the web.

Things that puzzled me is that, do they need to register the domain names and bind them to the server?

Will really like to know how to setup this kind of network.. Please teach me...
Thanks in advance.

---

### Post by Ionix on 2007-01-18
*bump

---

### Post by Ionix on 2007-01-19
*Bump

---

### Post by Ionix on 2007-01-19
*bump

---

### Post by mips on 2007-01-19
> Hi, I'll like to first explain what is the kind of network I am talking about, it's not the normal LAN connection i am referring to.

The network is not connected to the world wide web... but there are a lot of url available for linking to different unit's homepage. The url comes with very strange protocol.. it's not http:// but some other "strange" protocol, erm... I think it's ift:// etc.

Sounds like a standard LAN to me on which resides a Web server & a dns server, this could be one server. Could also be multiple LANs attached via a enterprise WAN like in a big company environment. Will really like to know how to setup this kind of network.. Please teach me...
Thanks in advance.

never heard of **ift**, not thinking of **ftp** ?



>  Beside this they also have internal email network, where their "@domain.com" also look very different from the standard emaill address we can see on the web.

Things that puzzled me is that, do they need to register the domain names and bind them to the server?

If the network is purely internal you can use whatever domain name you feel like and you don't have to register it. It's a different story if you try and connect it to the outside world. If the domain name looked funny it could be because it was from a MS domain controller.



>  Will really like to know how to setup this kind of network.. Please teach me...
Thanks in advance.You don't really provide much information to go on but I think the above should cover your questions.

---

