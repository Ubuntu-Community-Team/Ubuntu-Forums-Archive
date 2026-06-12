---
title: "dhcp vs static ip"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by caddict on 2008-09-28
I've just set up (with the help of this forum!) a little wired network of 4 computers running Hardy and many versions of windows, all behind a 4-port D-Link router. 

What are the pros and cons of dhcp vs static ip for a set up like this? Each computer is generally wired to its own router port, so the flexibility of dhcp is not an issue.

It could be my imagination, but the static ip option seems to give faster connection times??

Any thoughts on which is better?

---

### Post by doas777 on 2008-09-28
If you are going to share files or services, then you will need static IPs for servers (unless you use a higher level protocol for service discovery, which is unlikely since you are multi-platform).

otherwise you would have to find the current address of each dhcped server before you could use it.

I use static for my machines, and DHCP for guest PCs.

good luck
frank

---

### Post by lisati on 2008-09-28
The main advantage (for me anyway) of using a static IP is being able to tell which computer is connected where on your network. I accidentally reported as spam an email I sent from one of my email accounts to another account, and in due course received a notification from the email provider that this had happened - I was able to quickly tell from the email headers which machine I was using at the time and which OS it was (it happened to be Ubuntu, so I knew it wasn't likely to be malware)

I'm not aware of any speed advantages of one method of assigning IP addresses over another. (edit: once connected, that is!)

EDIT: Kia ora, fellow Kiwi!

---

### Post by doas777 on 2008-09-28
btw, static would not really give you a faster connection, thought it would be faster to get started, since you did not have to wait for a response, but thats only once per session and is only a second.

---

### Post by kevdog on 2008-09-28
Use static if you need to run a server and do any port forwarding from the router to the particular computer in question.  There is no speed (bandwidth) advantage however.

---

### Post by caddict on 2008-09-29
Thanks all for those answers. Static is definitely the choice for me :)

Kia ora lisati. Good to see ubuntu has taken hold in new zealand.

---

### Post by Iowan on 2008-09-29
When/if you decide to experiment with DHCP (as a learning exercise), note that "static addresses" can be converted to "static leases".  One potential advantage (not so much on a small system) is that address management can be done through DHCP server. I currently have my servers (printers, routers...) on static addresses, clients via DHCP.  Sometime soon, I'm gonna try setting up one with a static lease - to see if it works.

That said... another advantage to static leases - one less manager.  If DHCP server goes down, the rest of the network should still work - unless the DHCP server also happens to be your router...

---

### Post by caddict on 2008-09-30
Thanks Iowan, sounds like a good plan for a future experiment.

---

