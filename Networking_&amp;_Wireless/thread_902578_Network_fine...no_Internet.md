---
title: "Network fine...no Internet"
date: 2008-08-27
forum: Networking &amp; Wireless
---

### Post by TJCIB on 2008-08-27
Hi, this really isn't "Ubuntu related" per se, but you guys rock and the rest of the internet sucks...I've searched...

Basically lightning torched my big network.  Here is my setup
ADSL Modem connected to "wireless router 1".  That "wireless router 1" feeds PC#1, and Switch 1.  Switch 1 connects my computer lab (10 ubuntu computers).  PC#1 is a standalone XP workstation and used to log in to the ISP.

I can ping all of the computers on the network using IP addresses.
I have Internet connection on PC1, which has the login for the ISP.
None of the other computers are able to access the internet however.
I am assuming it is some configuration in the modem or maybe the router.  The modem is a Brazilian modem with no documentation in English (yay Brazil).  The router is a D-link DE 614+...i know its old, but lightning sucks.

Again, all the computers are connected fine and can communicate and mount NFS shares, be assigned IP address from the DHCP, etc...just no access to outside our LAN.

Any help, direction, etc. would be great.  Also, I didn't set up this ridiculous network, I had it dropped on me...so please hold back the flames =)

---

### Post by jimv on 2008-08-27
So the computer that's not connected to the switch gets internet, but the ones that are connected to the switch don't?

---

### Post by merlin051 on 2008-08-27
Try setting the gateway/dns server address on the ubuntu machines to the IP address of the XP workstation.

make sure you have all of the options in xp turned on for internet sharing :)

Otherwise, try setting the IP as your router's address.

---

### Post by Iowan on 2008-08-27
What provides DHCP? Default **dhclient.conf** gets dns-server address from DHCP - although you can fix that via prepend.

---

### Post by TJCIB on 2008-08-30
We use the modem itself as the DHCP server.

That modem is going through the router, the XP machine is also connected to the router and has internet fine.  Any other computer connected to that computer at the same time (wirelessly or hard wireds) has network functionality, but no Internet connection.

I'm thinking it's a block the ISP has manually put on our computer, since the technician installed it while I was away.  Probably an attempt to keep us from sharing our internet connection (good job so far...yay Brazil again).  I think this because of the login process they include to use the ADSL connection, rather than having an "always on" connection.

I found a private technician who used to work for the ISP, he's going to come and "do his magic", I'll report any progress also.

---

