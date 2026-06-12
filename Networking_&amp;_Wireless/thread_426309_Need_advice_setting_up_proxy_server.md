---
title: "Need advice setting up proxy server"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by whatsakernel? on 2007-04-28
Hi all,

I want to set up a proxy server for browsing the net from work but I don't know where to start. I think VPN is out of the question as I don't have the permissions to set it up on my work pc. What I want to set up is a static IP address where I can log in to my home pc and from there surf the net unrestricted. I'm a contract worker and need full access to the net to troubleshoot, however the company policy has locked down any site unrelated to the companies work. Can anyone suggest a nice user friendly gui setup or even just a step by step howto? I'm pretty experienced with windows but setting up something like this in linux is new to me.

---

### Post by dbott67 on 2007-04-28
I have done something similar to this before.  Basically, you need to do a few things:

1. Install [squid proxy server]("http://doc.gwos.org/index.php/Squid") on your home machine.
2. Install openssh server on your home machine.
3. Allow ssh traffic (port 22) to reach your Ubuntu computer from the outside world
4. Install PuTTY or other SSH client on remote machine
5. Setup an ssh tunnel from localhost:3128 (local) to localhost:3128 (remote)
6. Set web browser proxy to localhost:3128
7. Start putty, establish ssh connection to server
8. Surf!

Some useful reading:

[http://kimmo.suominen.com/docs/proxy-through-ssh/](http://kimmo.suominen.com/docs/proxy-through-ssh/)
[http://www.jtan.com/faq/vpnfaq.html](http://www.jtan.com/faq/vpnfaq.html)
[http://news.softpedia.com/news/Seting-Up-a-HTTP-Proxy-Server-with-Authentication-and-Filtering-52467.shtml](http://news.softpedia.com/news/Seting-Up-a-HTTP-Proxy-Server-with-Authentication-and-Filtering-52467.shtml)

---

