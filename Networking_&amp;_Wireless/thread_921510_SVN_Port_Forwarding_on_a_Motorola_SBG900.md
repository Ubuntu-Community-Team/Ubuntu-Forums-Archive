---
title: "SVN Port Forwarding on a Motorola SBG900?"
date: 2008-09-16
forum: Networking &amp; Wireless
---

### Post by Nuvious on 2008-09-16
I have a 2 part question:

First, what ports do I need to forward/trigger to access my SVN server (built on ubuntu and working on port 80) via a no-ip redirect?

Second and optional question is how do I set up a static ip locally on my cable router so my server always gets 192.168.0.2?

Been looking all over the internet for these answers and haven't found a thing.  Thanks in advance for serious replies!

---

### Post by nixscripter on 2008-09-17
First question: SVN (subversion) uses port 3690 (TCP or UDP depending on how the server is set up).

Second question: depends on the kind of router. It should be in the manual. There should be a way to change its parameters, and without reading that manual myself, I would guess it's through a webpage. Try going to the IP of your router in your browser. If your router was 192.168.0.1, for example, go to **[http://192.168.0.1/](http://192.168.0.1/)** and see if you can change things. It might ask you for a password, in which case you'll need the manual.

Falling short of that, I would suggest having the server not use DHCP and assign itself a static IP. The router should still route the packets correctly. You can make sure it works by trying it once with the command: ```
sudo ifconfig **eth-whatever** 192.168.0.4 up
``` For your network interface.

Hope this helps.

---

