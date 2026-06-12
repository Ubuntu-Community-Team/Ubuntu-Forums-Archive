---
title: "Connect Clients of 2 OpenVPN Servers Using Different Subnets"
date: 2008-05-22
forum: Networking &amp; Wireless
---

### Post by kalyptus on 2008-05-22
I have installed 2 OpenVPN Servers with different subnets. Will you help me make the clients from both OpenVPN server see each other.

---

### Post by SpaceTeddy on 2008-05-22
each openvpn server created it's own virtual network device. i guess you have two virtual network card, called tun0 and tun1 (or so i hope).

what you need to do to allow the clients to connect to each other is the follow:

1.) enable ip_forwarding
2.) push the routes to the other network to the clients via openvpn
3.) make sure iptables is not in the way

step 1.)
you can enable ip_forwarding temporarily with this command:
```
sudo sysctl -w net.ipv4.ip_forward=1
```
and permanently (even after reboot) with by editing the /ect/sysctl.conf and removing the # in fron of of the ip_forwarding line.

step 2.)
i am assuming your vpn subnet are 10.0.0.0/24 on tun0 and 10.0.1.0/24 on tun1 . Please correct them according to your setup (as you have not supplied any information about that).

for the tun0 device, edit the config and add the following the line
```
push "route 10.0.1.0/24"
```
respecivly, add the config for the tun1 device and add this line
```
push "route 10.0.0.0/24"
```

AGAIN: make sure you change the routes to the real networks. Each subnet should push the range of the other one to it's clients. This will result in your clients search the other vpn via the vpn server, which can then forward them to the appropriate client.
Also, make sure you restart the server after the change so they reload their config.

step 3.)
the simplest way here is the commaind
```
sudo iptables -P FORWARD ACCEPT
```
which will allow all any any traffic to pass through your computer. a little more sophisticated would be this one
```
sudo iptables -A FORWARD -i tun+ -o tun+ -j ACCEPT
``` which will only allow traffic to pass between the tun devices (i am still assuming you are using tun devices)

if you want to go into more detail here, i need to know more about your setup, your devices and your ips.

hope it helps :)

---

### Post by kalyptus on 2008-05-23
Thank you for your explanation SpaceTeddy. The following simple drawing is the supposedly architecture of the network I am trying to achieve...
 
>                      
clt1.3 
| 
|----- clt1.1 
| 
|----- clt1.2
|
server1
.
.
.							
server2	
| 
|----- clt2.2
|
|----- clt2.1 
| 
clt2.3 



The explanation for this architecture is as follows:
1. each servers as well as clients are located in different branches. 
2. server1's subnet is 10.11.0.0/24 and 10.0.1.0/24 for server2.
3. server1 is a client of server2 and vice versa.
4. for failover purposes, if the clients of server1 cannot connect to server1
   they will connect to serverr2 and vice versa.

I know it is possible to implement this architecture... just need help!

---

### Post by SpaceTeddy on 2008-05-24
right-o - i didn't know you are talking about two different machines - that puts things into a little different... perspecitve - but this is far from impossible :)

basicially, your two server share a network somewhere upstream to the internet (or they're already on the same subnet) - for me to know that, i would need to know how to the servers can communicate to each other... for now, i will assume the following setup:

VPN 1
|
Server 1
|
Network -> Gateway (to the Internet)
|
Server 2
|
VPN 2

This is a setup where both vpn serves are ON THE SAME subnet. To get this working here, you have two choices:

a) add a route for VPN1 to server2 and add a route for VPN2 to server1 
b) add both routes to the gateway. 

i would always prefer the first, as it enabled anybody else also on the Network to access the VPN's aswell - less configuration hassle - so to say. I guess the strange thing here is that the configuration is acctually done on a third server that is not touched by the vpn :)
So, for VPN1 (assumed network is 10.0.0.0/24) you would add the following route to your gateway
```
sudo route add -net 10.0.0.0 netmask 255.255.255.0 gw %server1
```
where you replace %server1 by the ip of the server.
for VPN2 (assumed network is 10.0.1.0/24) you add this rule to the gateway
```
sudo route add -net 10.0.1.0/24 netmask 255.255.255.0 gw %server2
```
again - replace the %server2 by it's ip

since any server and any client will send it's requests to the gateway, and the gateway now knows where the vpn's are, it can route the network correctly. Also, make sure that the VPN servers still push the correct route to the other VPN to the clients, or the requests will NOT reach the gateway to be routed directly.

hope it helps :)

PS: if the two servers are NOT on the same subnet, you will need to add the routers at the proper connections point and on the way there  TO ALL ROUTERS on the way there.

---

### Post by kalyptus on 2008-05-30
thanx SpaceTeddy. It seems the info you have given is enough for me to try the network architecture I am thinking of. Neverthiless, is it possible that I'll use the servers as my gateway instead of creating a new one. :)

---

### Post by SpaceTeddy on 2008-05-31
yes, one of the vpn-servers can be the gateway - that one must then hold the routes to the other vpn server (if that is what you mean). but then i don't understand the redundancy - if the gateway with one vpn fails, the second won't be reachable anymore as it has no connection left to the internet... 

or am i understandhing you wrong ?

---

### Post by kalyptus on 2008-05-31
The idea was for load-balancing and network failover - if one vpn server fails the other client will connect to the other server.

---

### Post by SpaceTeddy on 2008-05-31
then if one server is gateway as well as vpn-server, and that server fails, the other server still works, but is unreachable - therefore a failure on one server will make both unavailable. 

To make my point more clear, i am thinking of this setup right now


Internet
|
VPN1/gateway
|
switch
|
VPN2

if VPN1 fails, VPN2 will not be reachable - even if it is up and running...

---

### Post by kalyptus on 2008-06-02
I am thinking of making server1 as gateway for the first subnet and server2 for the second subnet. does it make sense...

---

### Post by SpaceTeddy on 2008-06-02
if the setup looks like this, yes, it does make sense :)

VPN1/Gateway -> Subnet1
|
Internet
|
VPN2/Gateway -> Subnet2

which is essentially the same setup as i was suggesting before.. i think.

sorry for the confusion :)

---

### Post by kalyptus on 2008-07-12
It's been a while... got to work for some project... 

Anyway... knowing the architecture... can anyone give the possible solution from what we want to achieve...

setting of gateway.. router... firewall...

---

