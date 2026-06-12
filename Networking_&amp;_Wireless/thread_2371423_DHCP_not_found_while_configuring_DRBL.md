---
title: "DHCP not found while configuring DRBL"
date: 2017-09-14
forum: Networking &amp; Wireless
---

### Post by ally2 on 2017-09-14
Guys if I connect a server directly to a switch can I run DHCP services on the server so that anything I plug into the switch would get basic i.p details.

If so what would the network config look like? would I just specify subnet mask, i,p addy bearing in mind no router would be involved?

Lastly what would the DHCP setup look like? 

Many thanks for guidance

---

### Post by SeijiSensei on 2017-09-14
[https://help.ubuntu.com/community/isc-dhcp-server](https://help.ubuntu.com/community/isc-dhcp-server)

---

### Post by ally2 on 2017-09-14
I have setup a switch with a router connected to it and have told the router to issue DHCP.  When I hook up nodes to switch they get a ip adress and I can ping the router.

However when I try and configure a DRBL server and issue the command drblpush -I. I get to a Dhcp config and it cannot find a DHCP server.

If I already have a DHCP server running do I have to specify it exists in a config file? I cannot understand why it isn't detecting DHCP.

---

### Post by SeijiSensei on 2017-09-14
DHCP relies on broadcasts so the server and its clients must all be on the same physical network.  Just to be sure, are the clients and the server all  on the same LAN?

I've never used DRBL so I don't know how it should be configured.  As a guess, does it need to be bound to an interface the way isc-dhcp-server does?

---

### Post by papibe on 2017-09-14
Hi ally2.

I slightly changed the thread tittle to better reflect your concern, and attract the correct eyes.

Regards.

---

### Post by ally2 on 2017-09-14
The switch, router, and server are on the same lan. There is no outside connection the router is plugged directly into switch. I think when you run the command drblpush -I
 
It runs through a setup process which helps you configure the DRBL / Clonezilla service and DHCP however I am getting a warning saying no DHCP is detected on my ethernet.

Although the nic is getting a ip from the router. I think I manually have to setup a DHCP isc server so that DRBL can use it for Pxe.

The whole thing is confusing me

---

