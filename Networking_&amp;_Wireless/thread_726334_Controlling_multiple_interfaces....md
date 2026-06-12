---
title: "Controlling multiple interfaces..."
date: 2008-03-16
forum: Networking &amp; Wireless
---

### Post by Tixer on 2008-03-16
My server has an ethernet card called eth0, and a wifi card called wlan0. I want to know how I can control what interface a program uses to connect to the tubes. For example, how can I tell say, Firefox, to only use the wifi card?

---

### Post by SpaceTeddy on 2008-03-16
i believe you cannot control that. As far as i know, you can only control who can use the network and who cannot (as in user) - but you cannot not specify what part of the network (well, there is a way to even specifiy that on user basis - but that is getting really ugly).

but then, i do not see a sceanrio where that would be important. to allow a specific application access to only a specific network card...

---

### Post by koenn on 2008-03-16
You can probably do that with iptables and some routing (eg iproute) - here's an intro : [http://harrychanputra.wordpress.com/2007/12/16/example-of-load-balancingredundant-internet-connections/](http://harrychanputra.wordpress.com/2007/12/16/example-of-load-balancingredundant-internet-connections/)

This means you can differentiate based on port numbers, eg web browsing (destination port 80/tcp) through wireless, but dns (destination port 67 udp and tcp) through the wire. 
I.e. it only works for applications that can be identified by the port numbers they use.
Because it comes down to routing decisions, you can probably also use hostnames and ip adresses (traffic to hugedownloads.com via wire, all other web traffic via wireless)

So you can not do something like : web browsing with Firefox via wire, web browsing with Opera via wireless

---

### Post by Tixer on 2008-03-16
That's perfect, since I just need to be able to move blocks of applications to a different network. Is there any way to get more specific with traffic though? I'd like to be able to get all web browsers on wifi, but move LigHTTPd to eth0.

If not, that's good enough. I can always use a virtual machine tied to an interface if I need anything more specific.

---

### Post by SpaceTeddy on 2008-03-17
the difference between the two is that the browsers send to port 80(ssl on 443), while lighthttp listens on port 80(ssl on 443). that is fairly easy to setup with the article supplied by koenn.

---

### Post by koenn on 2008-03-17
Managing incoming connections, as in **towards** your httpd server, is different from routing/directing outgoing connections. The easies is to do it by DNS.
 If you have a DNS record saying
name_of_httpd_server has addres address_of_eth0, 
then connections to name_of_httpd_server will go to eth0
But a lot depends on how your network is layed out and how you connect to the internet : it gets more complex if NAT-routers etc. are involved, but the article I linked to seems to gave some pointers in how to handle this.

---

