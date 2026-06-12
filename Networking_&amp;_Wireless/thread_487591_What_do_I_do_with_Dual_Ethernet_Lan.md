---
title: "What do I do with Dual Ethernet Lan???"
date: 2007-06-29
forum: Networking &amp; Wireless
---

### Post by cap10kirk on 2007-06-29
I just put together a new server. The motherboard comes with dual ethernet Lan connections. I don't know how to take advantage of having two ethernet lan connections as opposed to just one. Is there a way to double the internet connection to the server? I tried to assign my static IP address to both etho0 and etho1. This did not work, as I could not connect to the internet. I guess i'm asking what good is that second ethernet lan, and how can I utilize it? Can I double my internet connection with 2 ethernet lan connection? Also. this box uses Feisty Fawn. 

Thanks in advance,
Kirk

---

### Post by netztier on 2007-06-29
> **cap10kirk said:**
> I just put together a new server. The motherboard comes with dual ethernet Lan connections. I don't know how to take advantage of having two ethernet lan connections as opposed to just one. Is there a way to double the internet connection to the server? I tried to assign my static IP address to both etho0 and etho1. This did not work, as I could not connect to the internet. I guess i'm asking what good is that second ethernet lan, and how can I utilize it? Can I double my internet connection with 2 ethernet lan connection? Also. this box uses Feisty Fawn. 

Thanks in advance,
Kirk

First: having two IP interfaces in the same subnet is an absloute "no go thing", unless you know exactly what you are doing and take some countermeasures against the side effects this has. Suggested search keywords in forum search: **multiple interfaces**

Most simple solution:
Use only one. They're probably gigabit anyway, and your server will already have a hard time saturating one of the links.

Advanced solution:
Use **bonding** to create a single virtual **bond0** interface that gets the (single) IP address of the box. Depending on how you'll configure the bonding, you may need to have special features activated on the LAN Switch (Link aggregation, LACP), but there's also bonding modes that do not require switch support - you'll have to read some documentation about it and determine what best fits your needs. Good starting point: [http://ubuntuforums.org/showthread.php?t=283113&highlight=bonding](http://ubuntuforums.org/showthread.php?t=283113&highlight=bonding)

About "doubling" the Internet Speed: possible, but difficult and requires a lot of network and Linux-specific routing knowledge: see this thread: [http://ubuntuforums.org/showthread.php?t=481961](http://ubuntuforums.org/showthread.php?t=481961)

best regards

Marc

---

### Post by t4thfavor on 2007-06-29
Easiest thing to do with 2 interfaces is make a wan router. Just so you can say you did it. 
Plug one into the cable modem, and the other into the lan, then set up a firewall and nat. 
Its a great learning experience, and you will get that personal sense of satisfaction you can only get from a do it yourself project. 

Of course you will never want to use your home made router since it will probably not be as secure as a dedicated firewall appliance :)

---

### Post by cap10kirk on 2007-06-29
Thanks, fellas. I needed to be pointed into the right direction for some research on how to utilize the dual lans.

Kirk

---

### Post by t4thfavor on 2007-06-29
One more thing, you could do what I do and turn the second one off. It always helps me get more real work done instead of messing with my lan connection. 

I also find if I have a wireless card that doesn't support packet injection that I will be less likely to deauth my coworkers which makes me more likely to actually work.

---

