---
title: "Wired Home Network"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by ghandi69_ on 2007-07-27
Is my understanding of the following devices correct??

A hub, layer one... takes any information coming in on one port, and outputs it on all the other ports.  This is nice for smaller networks of computers hooked up together, but can cause many collisions in a large network.
 
A switch, typically layer 2, knows enough to take information in on one port, and will only output it on the port of its destination.  This allows for pretty much no collisions, and allows all the computers to equally share bandwidth (meaning they can pretty much all get full 10MBS, 100MBS, er whatever).  But it still doesn't act beyond knowing anything besides its own ports.
 
A router, typically layer 3, knows enough to take information in on one port, and not only will it be able to tell the packet what port to leave on, but it will be able to tell the packet all the different stops along the way(or its 'route'.)  Another feature apparently that comes with this added computation power, is the ability to act as a firewall and to share an internet connection.  If 4 computers are acessing the internet through one router, the router will be able to make them seem like "one very busy computer" with a single IP address.  The router knows  how to access each computer, but the outside world doesn't.  I do not think a switch has the ability to act as a single ip address for multiple computers.
 
Now the reason I lay all this out, is because I was trying to setup a home network with two computers using either a 'switch' or a 'hub'.

I would run a straight through cable from the cable modem to the hub or switch(don't need both, I just tried both, one at a time) , and no matter how it was hooked up... it would only assign a public ip address to one of the computers (66.yada.yada.yada, not 192.168.yada.yada), and the other computer would not be connect.  I believe that if I was using a router, it would have assigned both computers private network address and both would have been able to connect at the same time?

---

### Post by noob12 on 2007-07-27
You need to buy a gateway router that will support NAT (network address translation) between your single public IP address and the multiple private addresses on your LAN.  Linksys, Netgear, and D-Link are common vendors of these boxes.  A lot of them will have wireless LAN support as well.

---

### Post by steveneddy on 2007-07-27
Using a Linksys router, you will be able to set up an always on internet connection, automatically assign both PC's a private IP address and connect to/from the internet seamlessly on both PC's. Also both PC's will be able to share files easily with a router and you have the ability to use an extra port from the router, going to your switch, and have a sub network somewhere in the house.

Using an inexpensive router is truly the way to go in this day and age, especially if you have broadband internet coming into your home.

We use a Linksys WRT54G router that also has a wireless connection as part of the configuration. The street value of this part is usually around $50 on sale at various times of the year. It is easy to set up and never have we had a failure in years.

---

### Post by dando80 on 2007-07-27
Enable the dhcp server on the modem/router if it has one and then configure the network interfaces on the clients for dhcp. As already mentioned, you will need to have NAT enabled on the modem aswell.

---

