---
title: "Port forwarding with ipmasq"
date: 2006-10-12
forum: Networking &amp; Wireless
---

### Post by WesleyWex on 2006-10-12
Does anybody know how can I forward some port from an specific machine, so it can be reached from the Internet?

I'm using ipmasq (installed by apt-get), but the only help I found was telling to edit /etc/rc.d/rc.firewall-iptables ([found here]("http://tldp.org/HOWTO/IP-Masquerade-HOWTO/forwarders.html")), which does not exist. However I found nothing about how to insert this on /etc/ipmasq/rules.

My network is configured as this:

eth0 -> Internal network connected to my switch and shares my Inernet

eth1 -> External network connected directly to my ADSL modem. The modem connects and shares the internet only to ubuntu.

---

### Post by WesleyWex on 2007-03-19
Anyone?

---

### Post by alamba on 2007-03-19
Does your modem give you a public IP on the router interface or on your gateway interface? This is what I can tell you so far:

If your router interface has a public IP and your "external" network interface is an ethernet connection to the router with a private IP set, then you need to port forward on the router itself. 

However, if the router is say connected to the PC by USB (guessing here) and you get a public IP on the PC, then I'd suggest setting up the port fowarding using shorewall.

A

---

### Post by WesleyWex on 2007-03-19
Let me explain somethings:

My modem is connected through an ethernet cable to the eth2 (it was eth1 until something happened and now it's eth2). It connects to the internet and act like a router. The modem's IP is 192.168.1.1 and Xubuntu 192.168.1.2. I've configured it to forward all connections to Xubuntu.

eth0 is connected to a switch and to my other 2 computers on the network 192.168.0.x (Xubuntu being 192.168.0.1).

I don't know if I'm doing something wrong, but without ipmasq I could not access the internet, only intranet.

As you can see I'm a complete n00b at networking =\.

---

### Post by alamba on 2007-03-20
For the setup you have (ethernet based ADSL router) ip masq is needed for you to go out to the internet. You're absolutely right about that. On the other hand, for what u're trying to do, you need to enable port mapping on the router to your ubuntu box.

For example, if you want to ssh into your box from the internet, you will need to enable port forwarding on the router for port 22 to the internal IP address of 192.168.1.2 of the ubuntu box.

This is because, once u're on the internet, you can only reach your router since it has the Public IP, once it hits the router the router needs to forward the packet to the appropriate box hosting the service.

A

---

