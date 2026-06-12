---
title: "Ubuntu as router/firewall with WAP"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by tooscaredtotry on 2006-10-02
Hi!

I want to have Ubuntu act as my router/firewall (so that it can do QoS and bandwidth logs and that sort of thing).  I have a d-link DI-524 that I use as my router and access point now.

I have two network cards in my computer ubuntu machine, and a bunch of cat5 cables.  I want to run dhcp, etc on the ubuntu machine and have everything else on the network access the internet through the router (with nat and dhcp turned off).

Is this possible?  Do I need a cross-over cable between the router and the second network card of the PC?  How can I set it up so that the router has an IP (so that I can configure wireless)?  What should my dhcpd.conf look like?  Any advice?

thanks,
-t

---

### Post by darth_vader_ca on 2006-10-02
so to get this right. are you looking to bridge the network cards together, then have the ubuntu control dhcp and nat, and just simply use the router as a gateway as well as dns server? also what type of network logs are you looking to get. what type of traffic do you want to go through ubuntu with? sms etc..

cheers

---

### Post by tooscaredtotry on 2006-10-02
I want the router to just be a switch with an IP, basically.  I need it to continue providing wireless, but I want ubuntu to control dhcp, and all the other network services the router current provides, plus QoS and bandwidth stats.  Ubuntu would be visible to the world, and the router(acting as a switch/hub) and all the clients would be inside the network, just as they are now.

DNS can be handled by my ISP, or eventually a DNS cache on ubuntu (I'll do this later, not priority).

As for "gateway" I'm not familiar enough with networking to say one way or the other. I thought gateway and dhcp server were the same thing.

---

### Post by darth_vader_ca on 2006-10-02
just for your knowledge. the dhcp server assigns IP's as you know, however the gateway will provide the way to communicate out to the net. think of it as a route out to the internet.

you should be able to do what you are trying to do. however the wireless portion is still going to be controlled by your router. by the looks of it. if this is the case the wireless nodes will have to be set statically by IP and the metric routes would have to be set statically. 

Is the Ubuntu node going to be used just for ethernet based nodes and if so are you going to have a mixed environment for eg windows, linux or mac?

cheers.

---

### Post by jimmy20013 on 2006-10-02
If you want to do everything you mentioned without hassle, install firestarter. It allows you to do QoS, you can monitor your bandwidth and it also acts as a DHCP server.

Good Luck.

---

### Post by tooscaredtotry on 2006-10-07
I was using firestarter but I couldn't get dhcp to work correctly.. 

Do I need a cross over cable for the second NIC --> router?

---

### Post by Hitman_Forhire on 2006-10-27
No you don't need a crossover cable, and you're best bet for nice consistent connectivity is to set it up like this:

Net -- >  Linux Firewall/NAT/ClamAV/etc ---> To a switch

Then have all of your LAN machines AND the wifi should be hooked into the switch. 

Doing this will ensure that your ubuntu box is handling all of the routing and the port forwarding etc. and that everthing that is hooked into the switch will have connectivity and the switch will make the LAN that much more efficient rather than having a router/hub bouncing an insane amount of packets around on the local LAN. 

To hook up your wifi router just plug a cable from the switch into the "internet" port on the router. From here all wifi traffic will be NAT'ed from your normal WIRED lan and things will be much more secure and efficient than most ways I can think of. Cheap 4/8/12/24-port switches are very cheep and worth the money to make a scalable LAN and with a nicely configured Ubuntu box at the forefront of things you can only expect to see some nice results.

-Hitman

---

