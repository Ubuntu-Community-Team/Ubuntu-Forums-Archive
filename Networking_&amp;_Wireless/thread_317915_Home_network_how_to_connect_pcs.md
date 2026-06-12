---
title: "Home network how to connect pcs"
date: 2006-12-13
forum: Networking &amp; Wireless
---

### Post by gmalac on 2006-12-13
Hi,
I found a lot of material on the forum and it helped me but I am still confused on the type of connections needed on a home network.
I am awaiting my new desktop and I'd like to make a small home network with a server (Ubuntu server) acting as 
- web server, 
- file server - NFS?
- backup (of other pcs)- SAMBA?
- print server (1 HP deskjet attached)
- internet connection (ethernet connection to router) 
- firewall, dns?, proxy?
Right now my two PCs (Ubuntu 6.10+ WindowsXP) are directly connected to the router. My laptop (Kubuntu 6.10) connects to the router too but wirelessly.
What I'd like is to have all PCs+laptop connect to the server instead and that the server manages all this. 
Is it enough to change something in the network configuration of the pcs-laptop to reach the server? Or do I need to physically or wirelessly connect them to the server directly?

Sorry for this long post. Any help most appreciated, thanks!

---

### Post by bernied on 2006-12-13
If you want to replace the function of the router with your new pc, you will need two network connections on the server and you will need to change the physical configuration to something like this:
ADSL modem or current router ---- new server ---- network switch or hub (could use current router as a switch) ---- other PCs

Note that you need extra hardware - another network card and either a new ADSL modem or a new switch or hub (you can't separate these functions on an ADSL modem/router) for this. And you'll want to maintain your wireless connection somehow.

But, my little bit of advice...
don't do it, because unless you know more than you seem to judging from your questions, you will mess it up for at least some of the time and make anyone else who depends on the internet upset with you. Better is to simply add the new pc to the network, build it how you like it, then gradually add services to it, such as networked storage and printserver (both can be done with samba), webserver, etc. For any services that accept connections from outside your network, you will need to change settings in your router, but otherwise there should be minimal (or no) disruption to the rest of the network.

Your router is already doing the job of firewall and DNS. Don't take over this job until you know what you are doing, because you won't do it as well.

---

### Post by gmalac on 2006-12-14
Thanks Bernied for your reply and advice!

I will follow it because indeed this seems quite above my (present ;)?) competences.

In the weeks/months to come I will try to understand better, maybe there is a good book out there on the matter.

Thanks again

Guy

---

### Post by bernied on 2006-12-14
You don't need a book, there is plenty of info on the internet. You just need to know what words to search for.

---

