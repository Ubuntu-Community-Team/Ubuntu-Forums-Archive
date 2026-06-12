---
title: "VPN/PPTP ping and connection problem"
date: 2006-11-23
forum: Networking &amp; Wireless
---

### Post by Azalin on 2006-11-23
With the use of pptp-linux and pptp-config I have been able to get a vpn connection with the server at work (Microsoft Small Business Server 2003). However, when let pptp-config ping the ip I have received from the server, I get this message:

ping: sendmsg: Operation not permitted

When I ping my router (192.168.0.1) the ping is fine and I can connect to it as well. When I ping to the internal ip of the server (which is 192.168.1.1) I get the above message again.

Pptp-config tries to ping the ip received from the server, which is 192.168.1.51 so this and the server ip are in the same scope. Changing my whole network at home to something like 10.0.0.0 is unnecessary and also doesn't make any difference (I tried :) ).
In any case, sending a ping to an ip on the 192.168.1.0 network is not permitted, no matter if the ping command is issued from sudo or not. Pptp-config has to be run as root so issueing a ping from within pptp-config is not limited to user permissions.

Further, pptp-config has been configured at first to tunnel al data to the vpn connection, but that did not make a diffenrece as opposed to lan-to-lan or client-lan connection. I have it configured now as lan-to-lan so I can still access the local network. I have added 192.168.1.0/24 to the list of networks that need to be added to the routing table in pptp-config, but still no ping, no network shares, no network neighbourhood and most important of all, no terminal service client can be connected to the server or any of it's clients.

Pptp-config, when in lan-to-lan mode, does add the following to iptables, because I was suspecting it had something to do with iptables:

iptables --insert OUTPUT 1 --source 0.0.0.0/0.0.0.0 --destination 192.168.1.0/24 --jump ACCEPT --out-interface 'ppp0'
iptables --insert INPUT 1 --source 192.168.1.0/24 --destination 0.0.0.0/0.0.0.0 --jump ACCEPT --in-interface 'ppp0'
iptables --insert FORWARD 1 --source 0.0.0.0/0.0.0.0 --destination 192.168.1.0/24 --jump ACCEPT --out-interface 'ppp0'
iptables --insert FORWARD 1 --source 192.168.1.0/24 --destination 0.0.0.0/0.0.0.0 --jump ACCEPT
iptables --table nat --append POSTROUTING --out-interface 'ppp0' --jump MASQUERADE
iptables --append FORWARD --protocol tcp --tcp-flags SYN,RST SYN --jump TCPMSS --clamp-mss-to-pmtu

But this doesn't seem to make much difference. Also I have turned firestarter off at some point, the error (not permitted error) did not occur, but pinging did not succeed. I did not get a timeout as you would expect when an address is not configured properly or not reachable... It just looses 100% of it's packets.

Anyone ANY idea what is wrong? It doesn't really seem to be a firewall issue, but I am willing to try anything. Any way of backing up iptables configuration? I have seen some tips here and there of flushing all the iptables rules, but that resulted for all teh people involved in a non working internet connection, so backing that up would be a good thing to do I suspect... Any ideas are welcome!

---

### Post by Azalin on 2006-11-23
Anyone any idea?

---

### Post by Azalin on 2007-04-29
In feisty, using network-manager-pptp this problem persists, for me anyway, anyone any ideas???

I still can't ping to the VPN server, I still get the message
ping: sendmsg: Operation not permitted
and I am unable to browse the network which I am connected to through VPN nor am I able to make a terminal server connection to the VPN server through it's local network address (192.168.1.1) pinging this and it's vpn address doesn't work either by the way...

It amazes me that nobody is having these problems... or am I doing something totally wrong?

---

### Post by LanceM on 2007-05-02
I had a similar problem and had to manually add needed routes to my work network. Check your routing table and see if the correct routes are there.

---

### Post by Azalin on 2007-05-03
Since I am no expert on routing, I have no idea how to add the correct routes, nor do I know WHICH routes to add. I have tried a couple of things but they did not seem to work, so if you could post what you added to the routes, how you added it then I could try that. Maybe if you have a script, you could place it here?

---

### Post by LanceM on 2007-05-03
Here is the script I wrote. It makes the vpn connection then adds routes.

```
#!/bin/sh
#connect to work
sudo pon FCTG
#wait for connection
sleep 10
#add routes
route add -net  10.1.1.0 netmask 255.255.255.0 dev ppp0
route add -net  10.1.128.0 netmask 255.255.255.0 dev ppp0
```

---

