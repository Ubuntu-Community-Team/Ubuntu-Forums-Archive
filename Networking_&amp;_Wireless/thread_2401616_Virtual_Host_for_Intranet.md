---
title: "Virtual Host for Intranet"
date: 2018-09-20
forum: Networking &amp; Wireless
---

### Post by neidait on 2018-09-20
Hi All,
I've been playing around with Server 16.04 for some time but have just switched up to Server 18.04 for my intranet project.
OK, my issue...

I need to create an intranet that will reside on an internal network ONLY (further developments might see this move to our external hosting provider). Ive got the server up and running, configured a static IP and configured a virtual host.
However, I cannot connect to the assigned address or IP of the VH. I have created my own unique extension (so as not cause problems with established extensions such as .com .net .org etc) and I 'think' this might be my issue.

Am I correct and if so, how can I get around this?

---

### Post by TheFu on 2018-09-20
You can't just make something up on the one host and expect other systems to find it.  Most larger places will use DNS to resolve names to IP addresses.  Small places may modify every /etc/hosts file on all the client systems.  Those are pretty much the only choices if you are talking about HTTP traffic.  In short, you need to setup proper domain name resolution across the network.

Just for clarity, what do you mean by "virtual host"?  There are like 5 different meanings for that term and the post above is vague.

---

