---
title: "Port Forwarding problem..."
date: 2007-08-15
forum: Networking &amp; Wireless
---

### Post by dsmithjmajllc on 2007-08-15
I have a ubuntu box with 2 nic cards installed... I have Firestarter running on the ubuntu box.

1 card has the ip address of 192.168.254.2 and is connected to my DSL modem. On my DSL modem, I have nat forwarding enabled and have directed it to 192.168.254.2 ....

the second card is 192.168.1.1 and is the gateway for the rest of the network.

one computer on the network is running IIS (I'm playing arround with asp.net) This computer has the IP address of 192.168.1.229

I have a firestarter policy that forwards port 80 to the 192.168.1.229

I have a domain name pointing to my static IP address (my internet IP address)

From outside the network, I can view the site no problem (aka, at work I can view the site fine) From inside the network, using 192.168.1.229 I can view the site no problem...

But if I try to use my domain name to view the site from inside the network, I'm routed to my DSL modem (I know this because the modem login screen shows up)

This is a really annoying problem for me, does anyone know how to fix it? I need to have in network traffic to my internet IP address on port 80 forwarded to 192.168.1.229...

Thanks
David

---

### Post by noob12 on 2007-08-15
Yes, by editing iptables rules directly.  I don't know how to get the same underlying rules with firestarter.  There may be a way or you may have to edit them manually.

This thread of a few days ago is essentially the same topic: [http://ubuntuforums.org/showthread.php?t=524674](http://ubuntuforums.org/showthread.php?t=524674)

---

### Post by Synflux on 2007-08-16
I think this is because your dsl modem has recognised that the request has come from inside and therefore hasn't applied the NAT and forwarding rules. This is quite common in my experience.

Two things I can think of off the top of my head:

1) Run your webserver on a different port. Because you're using the same port as the admin page for the router, you may find that running it on a different one helps.

2) add a static mapping onto your internal hosts that points any requests for your domain name straight to the web server.

I'm not saying that either of these will help for definate but that's what I would play with.

Hope that helps you out. :)

---

