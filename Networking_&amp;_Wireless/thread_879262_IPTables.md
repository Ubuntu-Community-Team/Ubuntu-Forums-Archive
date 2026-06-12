---
title: "IPTables"
date: 2008-08-03
forum: Networking &amp; Wireless
---

### Post by tsumaru on 2008-08-03
Hi there, 

I currently have a router set to forward all traffic to my server (router is 192.168.0.1, server eth0 is 192.168.0.2).

The server is my firewall, it has a list of ports to forward to specific computers inside my network, for example the microsoft remote desktop port is forwarded to 10.0.0.50.

My ISP has given me 8 IP addresses of which i can only use 5.

My dilemma is i want anything on address 1 (lets say 1.2.3.1) to be handled as it is at the moment, by my server but _ANY_ traffic that is on ip 1.2.3.6 to be forwarded to an internal machine (10.0.0.10) to handle, essentially DMZing it on the perticular IP.  I have looked around on the internet but can only find specific port forwards but it does not help when trying to foward any traffic on a specific IP.

Essentially i am giving my other computer a public facing ip address but the nic on said computer has an internal one?

Can anyone help me?

---

### Post by kevdog on 2008-08-03
Can you explain better what you want to do?  Iptables is able only to sort by tcp/udp/icmp header information.  So if there is something unique in these packet type headers that contain the information you would like to sort by, then iptables can do it!

---

### Post by tsumaru on 2008-08-04
Well, as mentioned, i have 5 ip addresses. basically i want anything received on ip 78.33.121.166 to be forwarded by iptabls to another computer on my network 

Anything received on 78.33.121.161 would just be handled by the server running iptables

---

### Post by kevdog on 2008-08-04
How many network cards do you have, or all your ip addresses externally translated to one IP address?  Im confused by how one network card can be assigned more than one IP address?  Iptables seems like it would be able to do what you want in that it would be able to filter by destination IP address, however I'm confused about your setup.

---

### Post by tsumaru on 2008-08-04
ok, i will try to explain my setup

```
ip
78.33.121.161
78.33.121.162
78.33.121.163
78.33.121.164
78.33.121.165
78.33.121.166
    |
 Router (192.168.0.1)
(Router is DMZ'd to 192.168.0.2)
    |
NIC 1 (192.168.0.2)
    |___SERVER_____
                  |
               NIC 2 (10.0.0.7)
                  |
          ______Switch
          |       
Rest of network including other web server 10.0.0.1
```


All i want is any connections on 78.33.121.166 to be routed to 10.0.0.1 and any other connections on any other ip is handeld by main server

I hope this has cleared that up?

P.S my router is useless, hence the DMZ to a linux box with iptables doing all my routing

---

### Post by tsumaru on 2008-08-07
any takers?

---

### Post by Ocxic on 2011-03-29
```

iptables -t nat -A FORWARD -s 78.33.121.166 -j DNAT --to-destination 10.0.0.1

```That should forward all incoming connections from 78.33.121.166 to 10.0.0.1

@KevDog-- you can setup virtual devices the would be named eth1:0 eth1:1 and so on, each one can have a different address, even though there sharing the same NIC

---

