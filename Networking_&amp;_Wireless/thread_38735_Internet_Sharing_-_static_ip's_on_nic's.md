---
title: "Internet Sharing - static ip's on nic's"
date: 2005-06-01
forum: Networking &amp; Wireless
---

### Post by n21roadie on 2005-06-01
howdo setup internet sharing from my ubuntu acting as internet server with two network cards, eth0 dynamic to my dsl router, and eth1 static ip for my home network,

---

### Post by Mez on 2005-06-01
[http://www.tldp.org/HOWTO/IPCHAINS-HOWTO.html](http://www.tldp.org/HOWTO/IPCHAINS-HOWTO.html)

That link is a good place to start learning how to do this sort of thing

---

### Post by az on 2005-06-01
To serve dynamic addresses, you need to be a dhcp server.  You also need to do ip and dns masquerading.  Easy:

Install dnsmasq (a dns masquerade as well as a dhcp server) and ipmasq (ip masquerading.)

Configure dnsmasq by editing the config file and making it go: (basically, two things)
sudo /etc/init.d/dnsmasq restart
configure ipmasq to allow dhcp requests, otherwise you need to stop ipmasq to make a connection.  You need to copy a .rul from the documentation directory into the /etc config and edit the interface name.  Then reconfigure ipmasq to start after networking has been started

sudo dpkg-reconfigure ipmasq.

---

### Post by alastair on 2005-06-02
Maybe a bit more than required, but I think "Shorewall" is an excellent firewall that also lets you easily set this sort of thing up. The docs are good as well. I think the basic config is pretty easy.

It's available as a package. Web site at [http://www.shorewall.net](http://www.shorewall.net)

P.S. I don't think the poster requires a DHCP server - I suspect the router assigns that. It's probably a DNS cache as well.

---

### Post by n21roadie on 2005-06-02
Many thanks for the replies, i should have mentioned that this pc is dual boot (xp + ubuntu ) with two network cards (1) etho - dynamic ip address from the dsl router (2) eth1 - static ip ( 11.*.*.3) - for my home network , on the other pc's (all Xp) on the home network the browser proxy setting for http-ftp-socks are (11.*.*.3 - ports 808 +2121 +1080) ,and i would hope to leave them as is , so when i boot on the server ( this pc ) between Xp and ubuntu , i don't have to reconfigure them on the client pc's ,

```
"Shorewall"
``` 

Once again , this is all new to me but i like to perist with linux - which version of shorewall is suitable for ubuntu ?

---

### Post by az on 2005-06-02
[http://packages.ubuntu.com/hoary/net/shorewall](http://packages.ubuntu.com/hoary/net/shorewall)

Shorewall is in hoary.  Shorewall-doc is in universe.   I highly reccommend the shorewall-doc package, too.  It provides you with example configuration files.  You just copy them into /etc and tweak them and you are good to go.

---

