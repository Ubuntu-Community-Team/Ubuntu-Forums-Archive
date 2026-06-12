---
title: "pptpd connects but I cannot get it to share internet through vpn connection"
date: 2014-10-05
forum: Networking &amp; Wireless
---

### Post by computergroove on 2014-10-05
I am trying to setup / test a pptpd server install I have installed on my ubuntu server 14.04 x32 I setup following this guide -> [https://help.ubuntu.com/community/PPTPServer](https://help.ubuntu.com/community/PPTPServer). I can connect but when I do I immediately lose internet browsing capability in windows. The connection stays connected though. Here is a copy of my comment stripped pptpd.conf:

```
localip 69.29.91.172 (its a fake address)
option /etc/ppp/pptpd-options
remoteip 10.0.0.100-200
```

My ubuntu server is hosted on a virtual private server a few states away from where I am. I need to make a pptpd vpn because I need to connect a ddwrt router to the connection and I am aware of it not being up to today's security standards. I do not currently have a firewall installed on the server and the server has only a public ip address. I believe this is a problem with the way I need to configure my pptpd.conf. When I run ipconfig from my windows computer connected to the pptpd server I get:

ip 10.0.0.100
subnet 255.255.255.255
gateway 0.0.0.0

and the internet wont load web pages. 

As per the instructions in the link above I have added my iptables rules to /etc/rc.local and I have tried 3 different sets of iptable configurations:

First:
```
iptables -t nat -A POSTROUTING -s 10.0.0.0/24 -0 eth0 -j MASQUERADE
iptables -A FORWARD -p tcp --syn -s 10.0.0.0/24 -j TCPMSS --set-mss 1356
```

Second:
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE
iptables --table nat --append POSTROUTING --out-interface ppp0 -j MASQUERADE
iptables -I Input -s 10.0.0.0/8 -i ppp0 -j ACCEPT
iptables --append FORWARD --in-interface eth0 -j ACCEPT
```

and Finally:
```
iptables -t nat -A POSTROUTING -o eth0 -j SNAT --source
```

and suggestions?

---

### Post by William_Parks_Walk on 2014-10-06
[http://i.imgur.com/uByEkJD.jpg](http://i.imgur.com/uByEkJD.jpg) here is a topology chart of what im looking to do.

---

