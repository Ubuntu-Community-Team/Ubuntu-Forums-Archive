---
title: "Forwarding ports through unaccessible router in Ubuntu?(URGENT)"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by Extreme Coder on 2007-01-06
Hi.
I'm having a problem here. My internet connection runs from a router that I do NOT have access to. While this may not be a problem while web browsing, checking e-mail or chatting, it can prove to be quite a big one when downloading files using a torrent client, or using SSH or VNC to connect to someone else's PC. I get dial-up speeds of 2 and 3 KB, and Deluge, Azureus and KTorrent report not having an incoming connection and saying that I maybe behind a firewall or router(which is true), and I get NAT errors when testing ports in them. When my BitTorrent client was blocked, I used to get speeds of 50 or 60 KB, which is the speed of my internet connection. All internet connections here in Egypt are served through LAN connections, which means you get a LAN cable from a router you do NOT have access to.

So, long story short, is there any way possible to forward ports through a router that you cannot access? This is proving to be quite a problem, since I maintain about 15 PCs with Ubuntu installed, and this problem is on each one of them :/


Thanks a lot in advance,
Extreme Coder

---

### Post by Crakie on 2007-01-06
Sorry, but I don't think it's possible. Legally, that is. But are you sure your provider has ALL ports blocked? There may be a portrange that you can use. 

Seems that Egypt is way 'ahead' in the whole copyright infringment nastiness (sorry... lame joke)

---

### Post by Extreme Coder on 2007-01-06
Anyway, I don't see what  is illegal about it. How do I check what ports are blocked and what are not?
And it isn't technically a provider, but more like: Somone gets a high bandwith DSL connection from a certain company here to his router, and he gives LAN cables from his router to everyone he provides. That's how you get connected here in Egypt :( I hope that makes it clearer.

And about the joke, nah.. its ok. But you should know that Egypt is the worst country in terms of copyright protection... Afterall, how could you believe that the Microsoft Center here uses pirated Windows?
 (Hooray for scholarship to Canada!)

---

### Post by Rob_H on 2007-01-06
There is a technique called "punching" that can be used to open ports through a firewall. Skype uses it. Not sure if it can be applied to a BitTorrent session, though. Here's a link that explains what it's all about:

[http://www.heise-security.co.uk/articles/82481](http://www.heise-security.co.uk/articles/82481)

---

