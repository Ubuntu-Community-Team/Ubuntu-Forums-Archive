---
title: "One server, two gateways, and two networks."
date: 2016-02-29
forum: Networking &amp; Wireless
---

### Post by jed3 on 2016-02-29
Good day all,

I have a network project that I am going to undertake shortly and I'd like some advice on the best way to go about it. We currently have one server preforming DHCP, Firewall, Gateway, IPS, File, and Print server duties. We have one DSL modem, connected to eth0. We are looking to add another DSL modem, so that we have a second IP address. We will then have a LAN setup on the inside of the server/gateway and we would like to run two separate networks with. One network will exclusively access one DSL modem for the internet. And the second network will exclusively access the other DSL modem. but both networks will be able to access the server resources(print, file, and such).

The current server is running Ubuntu 15.10 with a Zentyal overlay and three Ethernet cards. two will be(external) for the modems and incoming traffic. And one will be (internal) and go out to a Cisco 24 port switch. We will be using static ip addresses. I was going to assign the computers to separate networks via ip address/subnets, and then give them different gateways. 

Will this work, and will Ubuntu keep the traffic separate between the two networks, and not try to combine them? Any other insights, sugessitions, or potential issues I should address?

Thank you for your time.

---

### Post by newbie-user on 2016-02-29
Yeah, it will work. You might also want to set up virtual NICs with two VLANs on the server's internal port, and then trunk the Cisco port to which the server is connected. The Cisco switch then will need access ports for the two vlans. Then you'll want to set up firewall rules so that both networks can't talk to each other.

---

