---
title: "Do we still need two network cards for terminals w/ net access?"
date: 2007-02-05
forum: Networking &amp; Wireless
---

### Post by AlexMorin on 2007-02-05
Hello all!

I was wondering if it is absolutely necessary to have two network cards in the server. I am running Edubuntu as an LTSP server for 25 diskless clients.
This setup is suposed to be shipped off to Africa at some point. We are giving this lab to a school over there. We are in Montreal, Canada.

If I have one NIC only, and setup the server and clients. Then I plug-in a DSL/cable router to the network switch, would it be possible to use that router as the default gateway and access the net from the terminals? I'm interested in answers from people from Western Africa who would know how net access is usually provided in larger towns and schools (DHCP or not? Routers? DSL? Cable modems? etc).

Because seting up an edubuntu server is less simple when you have two NICs, and this needs to be easy to run and maintain, since it will be across the ocean...

Thanks a lot for reading!

---

### Post by tturrisi on 2007-02-06
Yes, only one nic would be necessary if use a router as default gateway if that router also uses dhcp and nat.  All clients, including the server, would be assigned an ip address by the router, unless the server uses a static ip, which it should do on such a lan.  To do this though, you will need to know the internet they will be using in the Africa school.  This shows you how to setup a lan w/ internet using a router:
[https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring](https://help.ubuntu.com/community/UbuntuLTSP/LTSPWiring)

---

### Post by AlexMorin on 2007-02-06
Understood, thanks!

But don't you *need* to have the Edubuntu server running the DHCP in order to have a functional LTSP implementation?

---

### Post by tturrisi on 2007-02-06
> **AlexMorin said:**
> Understood, thanks!

But don't you *need* to have the Edubuntu server running the DHCP in order to have a functional LTSP implementation?

"It is possible however to use the same steps on the network gateway to allow the Server and the Clients to connect to internet." ...but it doesn't say how to do that IF a router is used as the gateway, but it appears that it couild work.  I imagine that the server must not be config'd as a gateway and let the router handle the nat by editing /etc/ltsp/dhcpd.conf.  According to the middle pic in above link you can do it w/ 1 nic, the 3rd pic = use 2 nics.  I would think it wise to use 2 nics and route all client internet traffif via the server so as to be able to use a proxy and/or govern bandwidth/traffic filtering.  Have some control over what the students can/can't do on the www.
[https://wiki.edubuntu.org/ThinClientHowtoNAT](https://wiki.edubuntu.org/ThinClientHowtoNAT)

---

### Post by koenn on 2007-02-06
> **AlexMorin said:**
> ...
Because seting up an edubuntu server is less simple when you have two NICs, 

might be true, but the network config will be more tricky. It is possible, as pointed out earlier in this treath. I'd prefer a 2NIC setup myself.

However; if you want the 1NIC setup, let me calrify a few points that seem to cause some confusion.

- you will need a router
- this router will need to be able to do basic firewalling : if it only does routing, your server may be exposed to the internet. Most " ADSL routers" do NAT, which offers minimal protection,  but pppoe ADSL or cable modems will result in having the server directly connected to the internet with a public, routable address - anyone from anywhere could (attempt to) connect to it.

- yes, I think the Edubuntu server will need to be dhcp server, because it uses dhcp options to  let thin clients load their OS. A router running a dhcp service will probably be unable to handle that unless it's quite sofisticated

- therefore, the dhcp service on the router will need to be turned off. The router's LAN inteface will need to be configured manually (ip address, netmask, ...). The address you use should be in the IP range of the LAN, obviously, but excluded from the dhcp range so that it won't be given to a thin client (via dhcp) as well.

- as the edubuintu server will not receive DNS server addresses from dhcp, you may have to add them manually in /etc/resolv.conf. You'd need to know the addresses too, but in theory, any public dns server will do. 

- I'm not sure about the "default gateway" for the thin clients. It's a "terminal server" setup, so the actual internetworking will be done by the server, the client only receive the screen output, they don't actually do anything, they don't access the internet themselves. Or do they ? 

- Cable and ADSL are not the same, and an ADSL by means of ppoe is different from ADSl via an adslmodem+router combination. The network config will have to be adapted to the situation - but I guess you already knew that since you asked about the situation in Africa for internet access. 
.

---

