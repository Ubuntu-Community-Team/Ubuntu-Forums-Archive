---
title: "Sharing Internet connection using wireless router"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by tolano on 2008-01-03
After spending a long time searching in google and some other specifc forums, I have to ask you guys if someone here can help me.
I know the basics of iptables, and networking, I have some experience with linux, but these days I want to set up a server for routing purposes, and as it's the first time I try , I have no idea how to solve the problem.
I have the server running Ubuntu, connected to the internet through eth0. eth0 is an network adapter wired to the router. I also have eth1 which is the wifi pci card.
I want to configure the system so I can get internet from the router, and share it through eth1 to the laptops I have at home.
I have read the excellent how-to [http://www.debuntu.org/iptables-how-to-share-your-internet-connection-p3](http://www.debuntu.org/iptables-how-to-share-your-internet-connection-p3) but I can't get it to work.
I have tried 2 different configurations:

1-) I disabled the NAT in the router, so I have direct access to the internet from the server. Then I asigned eth1 the address 192.168.1.1 and used the script of the tutorial mentioned above. $IPT -t nat -A POSTROUTING -o $WAN -j MASQUERADE. I configured one laptop like this: IP: 192.168.1.2, netmask:255.255.255.0, gateway;192.168.1.1. It didn't work.

2-) I enabled the NAT in the router. The server gets the ip 192.168.0.4, the laptop gets 192.168.0.2, the gateway of the router is 192.168.0.1. I configure iptables like the tutorial above, and the laptop: IP: 192.168.0.2, netmask:255.255.255.0, gateway;192.168.0.4 (the server). It didn't work.

In both cases, I can get pings from each computer but there is no access to the internet.

So what I want is to share internet connection through the wireless device (eth1) using the eth0 device conected to the internet.
                                           
```

                              --- WIFI
                            /
INTERNET ------> ROUTER ---- 
                            \ --- Cable ----> (eth0) Server (eth1) ---> WIFI( using router )

```
I hope someone can help me. Thanks a lot!

---

### Post by Aussiejoe on 2008-01-22
You might want to check this link out [https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)  I think you are wanting to create an ad-hoc network. I am trying to solve the same problem, but using a dial-up connection.

---

