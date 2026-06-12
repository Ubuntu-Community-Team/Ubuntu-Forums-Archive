---
title: "ssh port forwarding"
date: 2016-02-01
forum: Networking &amp; Wireless
---

### Post by carlo17 on 2016-02-01
hello everyone, I'm new and hope someone can teach me something helpful. :D

I have a linux based freesat box in my dad house and I need to access it to run some commands and update some file.

now I have all the login detail, but the only problem is that port 22 is closed.

at the moment I'm in London and the box is in Italy :D so local access is impossible for me.

I just scanned the opened ports on the remote IP and saw that port 15000 is opened.

can I access ssh through port 15000 and redirect to te port 22 on the box?

I have local IP of the box, which is 192.168.0.42 and ssh is active on it

is there any way I can use a tunnel or something like that to access ssh on port 22 of my box entering from port 15000 from the router?

thank you for all your help in advance
Carlo

---

### Post by Vladlenin5000 on 2016-02-01
Hi and welcome.

You need to add the proper port forwarding rule at the router where the destination device is connected to.

---

