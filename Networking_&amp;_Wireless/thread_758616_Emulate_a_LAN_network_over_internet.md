---
title: "Emulate a LAN network over internet"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by DrCoolSanta on 2008-04-18
I have machines on an internet connection, which is behind a router, and I have no direct access to the router. Because of this I can't have a server started on my machine and expect it to be accessible over the internet, however I only need one or two machines to be able to connect to the server, therefore I was thinking if it was possible to emulate a network over the internet. The machine which needs to act as a server also has a firewall (iptables) for various reasons, and to explain them I'll have to explain you the whole scenario.

I have heard of a program called Hamachi, tell me how to configure it as well, with the firewall and stuff, if it is possible?

If you know of someother program, tell me of it please.

PS: Forgot to tell you, if it was possible to have it run on windows as well, not neccesary, but if possible . . .

---

### Post by rogirwin on 2008-04-18
From what I can gather... You need to open external ports on your router to point to the server on your local network. eg. To have a webserver you would open port 80 on your routers firewall to point to the webserver on your network.

OpenVPN is quite a good VPN that works on windows and Linux. Setting up the encryption keys and configuring can to a little tricky...

---

### Post by mlentink on 2008-04-18
You might want to take a look at Hamachi too
Actually you don't have to do much configuration with that. It's all pretty self-explanatory. Check out their website and forum, pretty informative. I use it myself to connect to the in-laws and that works like a breeze.

look [here]("https://secure.logmein.com/products/hamachi/vpn.asp")

---

### Post by rogirwin on 2008-04-18
I'd rather use Open source / GPL software...

I'm sure it works well but OpenVPN works well too and has done everyone I have needed it to in the past. SSH is also a great way of making remote connections. Very little configuration required.

---

### Post by Paris Heng on 2008-04-18
Just use the loopback address (Lo) in the kernel is sufficient.

---

### Post by DrCoolSanta on 2008-04-18
Thanks guys for the recommendations, but still did you consider that I can't forward ports or anything because the machine is behind a router I don't have access to . . .

---

### Post by rogirwin on 2008-04-18
You have to... At the server end anyway. If both ends are secured behind firewalls then they can't see each other.

The only possible way around this is to get them to log into a third location where they can authenticate with each other But I don't know what that is.

---

### Post by DrCoolSanta on 2008-04-18
Is there any software client in which a third machine owned by the software, acts as the server?

An online machine that would act like a server for our machines and provide client software would be good? I heard Hamachi would do that, is this true? I considered having my own machine act as the server, but i can't have it on for ever . . .

---

### Post by DrCoolSanta on 2008-04-22
Have to post again, hamachi for some reason can't connect from the machine to which I have no access to router. Any other recommendations for what I want?

---

### Post by mmichalik on 2008-04-22
Is this for personal or business use?

If it's business use, you could easily put the server into a cloud computing environment.

I'm, by no means, promoting my consulting firm here but, have you looked into it?  you can read our blog at [www.m-econsulting.com/cloud](www.m-econsulting.com/cloud) and get a general idea of what it is.  

Our consulting firm is using Ubuntu, solely, for everything from our in-house stuff to migrating existing clients off of proprietary O/S' and we are now moving into enterprise cloud computing solutions using Ubuntu as our cloud server solution.

It's exciting technology and we are going to use Ubuntu to further it.

---

### Post by DrCoolSanta on 2008-04-23
Persoinal use ... Need F/OSS

---

