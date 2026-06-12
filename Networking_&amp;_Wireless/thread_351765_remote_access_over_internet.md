---
title: "remote access over internet"
date: 2007-02-02
forum: Networking &amp; Wireless
---

### Post by Odyssey1942 on 2007-02-02
I have two Ubuntu computers at my office on a lan which access the internet through a router and we have a fixed external IP address there. Computer 1 has a remote connection server running and I can remotely access computer 1 with computer 2 using its browser over the lan.

I want to be able to access computer 1 from my Ubuntu computer at home and know that computer 1's remote server needs to have the IP address of my home computer (more on that in a moment).

My first question has to do with getting through the router. If I enter the fixed ip address of our office in my browser at home, I will reach the router, not computer 1, correct? So do I need to configure my router to somehow pass the request through to computer 1, and if so how?

Secondly, I have a fibre optic dsl at home which supposedly has a DHCP external IP address (although every time I check it with GRC, it is always the same so maybe it's fixed and my dsl ISP just doesn't want me to know it-cause they can charge extra for fixed IP's). However, assuming that it is DHCP, is there any way that I can "simulate' a fixed IP for purposes of configing computer 1's server package?

Also what else is it clear from the above that I don't understand yet that I will need to deal with?

---

### Post by kingmonkey on 2007-02-02
> **Odyssey1942 said:**
> I have two Ubuntu computers at my office on a lan which access the internet through a router and we have a fixed external IP address there. Computer 1 has a remote connection server running and I can remotely access computer 1 with computer 2 using its browser over the lan.

I want to be able to access computer 1 from my Ubuntu computer at home and know that computer 1's remote server needs to have the IP address of my home computer (more on that in a moment).

My first question has to do with getting through the router. If I enter the fixed ip address of our office in my browser at home, I will reach the router, not computer 1, correct? So do I need to configure my router to somehow pass the request through to computer 1, and if so how?

You need to port forward a port on your router to your pc. [www.portforward.com](www.portforward.com)

> **Odyssey1942 said:**
> 
Secondly, I have a fibre optic dsl at home which supposedly has a DHCP external IP address (although every time I check it with GRC, it is always the same so maybe it's fixed and my dsl ISP just doesn't want me to know it-cause they can charge extra for fixed IP's). However, assuming that it is DHCP, is there any way that I can "simulate' a fixed IP for purposes of configing computer 1's server package?

Also what else is it clear from the above that I don't understand yet that I will need to deal with?

[http://dyndns.com/](http://dyndns.com/)

---

### Post by Odyssey1942 on 2007-02-02
Thanx for these. The reading has begun!

---

