---
title: "SSH While At Work"
date: 2007-03-01
forum: Networking &amp; Wireless
---

### Post by MinhD on 2007-03-01
Hi, my first post here, so Yay!  This forum rocks by the way, the community is great.

I have ssh (server) setup on my home server and it works from within my local network (tested it via putty from an XP machine), it also works fine over straight internet (tested it from a friend's home).

The problem I'm having though is when I'm at work, I can't connect.  Here's a bit of info on my setup.

I don't have a static ip from my isp (who does these days...), so I use dyndns with a custom dns setup, works great, I'm also running apache and the website shows up fine.

At work, we're locked down fairly tight, so the only ports that are open to Joe Public are 80 and 443 (for https).  So I figured a way around this would be to have my ssh server run on port 443, which is how I have it setup.

What happens though when I try to connect @ work is if I use the dns (eg:  myaddress.com), I get:  "Unable to open connection to myaddress.com Host does not exist".  If I use the IP (that I get by logging into my dyndns account), I get:  "Network error:  No route to host".

I know the dns setup is working, because it can resolve my website no problem (running off the same server as the ssh), so I don't understand the first problem.  Then, when using the IP, I don't understand the 2nd problem either.  :confused:

I also know it's not a router/firewall/iptables issue because as I said, I can connect to it from the internet no problem - it's only when I'm at work.

Any thoughts or suggestions?  Is our work firewall somehow recognizing the traffic type and blocking it?  I thought as long as the port is open, it's all tcp traffic to the firewall?

---

### Post by gunthr on 2007-03-01
Are you sure your server is listening on 443 and your client is sending there? I set up iptables my client to reject outgoing packets on port 22, and was able to connect to my server using an alternitave port.

---

### Post by MinhD on 2007-03-01
Yes I'm sure because I have tested it from various outside internet connections, won't connect on 22 anymore, only on 443.

Just doesn't work from work.

---

### Post by netztier on 2007-03-01
> **MinhD said:**
> 
Any thoughts or suggestions?  Is our work firewall somehow recognizing the traffic type and blocking it?  I thought as long as the port is open, it's all tcp traffic to the firewall?


Have you checked if your work network has a default route towards the internet at all? It might be that every connection to outside hosts goes through a proxy or a cascade of proxies. In that case, all your network needs is a route up to that proxy server.

Open a SSL/HTTPS connection to some outside host and check your systems TCP connection table (**netstat -na** on windows, **netstat -napt** on Linux), so you have one way to find out the ip address and port of the proxy.

With this info, configure an SSH client that can use proxies (such as PuTTY for Windows) to use a HTTP proxy when talking SSH on port 443 to your home IP address. 

My work network has such a setup - and for a while I was able to tunnel through it.

best regards

Marc

---

### Post by MinhD on 2007-03-01
That did the trick!!!!

I completely forgot about our proxy server, put it into Putty and worked like a charm!

Thanks, you guys rock!

---

