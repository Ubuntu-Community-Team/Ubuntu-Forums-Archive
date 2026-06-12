---
title: "help understanding iptables route"
date: 2020-04-07
forum: Networking &amp; Wireless
---

### Post by keratos2 on 2020-04-07
I've created a IPsec/L2TP VPN and it seems to work fine. Server and Client can ping each other's IP and can both access internet.
Server is an Ubuntu 18 droplet in Digital Ocean's cloud.
Client is an arch Linux box.
I followed these guides for server and client:
[FONT=Verdana]https://github.com/xelerance/Openswan/wiki/L2tp-ipsec-configuration-using-openswan-and-xl2tpd
[/FONT][FONT=Verdana]https://wiki.archlinux.org/index.php/Openswan_L2TP/IPsec_VPN_client_setup
[/FONT]
However, two questions for a networking-guru please:-

1. On the server, the recommendation was to add the following rule but without it , all seems well. So what is it for - as in if everything works without it then why? In fact, I do not have any rules, neither on the server nor the client !. All necessary ports are open on the cloud firewall. It works fine.
[FONT=Verdana]iptables -t nat -A POSTROUTING -o eth0 -m policy --dir out --pol none -j MASQUERADE

2. I have a LAN at home behind an ISP provided router. I can only connect to my cloud VPN server with one client on the LAN. An attempt to connect a second LAN client collapses the tunnel and the first client needs to reconnect. I have spent a lot of time researching this and am minded to accept that this is the reported and known limitation of IPsec and that NAT-T will not solve the problem. NAT-T is enabled on both sides as indicated in the **ipsec verify **outputs on left and right. I did try applying all the **iptables route **additions suggested in the guides but they made no difference so either it's not possible or I am doing something wrong.

I am at the limits of my knowledge and ability now so reading more hasn't helped hence hoping a rather kind chap will help out here.

[/FONT]

---

### Post by SeijiSensei on 2020-04-08
You would only need to use MASQUERADE if the box is acting as a gateway router between your local network and the Internet.

I use simple [static point-to-point tunnels via OpenVPN]("https://openvpn.net/community-resources/static-key-mini-howto/") between my local network and my cloud servers.  A machine on my local network connects to one of the cloud servers which acts as a router for the other servers.  My router has a static route that directs traffic for the 10.1.1.0/24 cloud network to the local machine running OpenVPN.

IpSec/L2TP always seemed much more complicated that it was worth.

---

### Post by keratos2 on 2020-04-08
It's a standard ubuntu 18.04 droplet on the Digital Ocean platform.
Does that make it a gateway between itself (its the only one on that side)?

On the left side, my ISP router, is that a gateway?

---

### Post by SeijiSensei on 2020-04-08
Since there's only one remote server, it's not really a gateway to anything.  On the remote machine you would run OpenVPN in server mode. On your local network, you would need a machine running OpenVPN in client mode. It can be behind your ISP's router. That machine does function as a "gateway,"  in this case between your local network and the remote droplet. 

My local LAN is on 192.168.100.0/24. The remote machine has a virtual OpenVPN interface at 10.1.1.1. A PC on my local network running Linux connects to the public IP address of my cloud server and sets up a tunnel between the two machines using addresses 10.1.1.1 (cloud) and 10,1.1.2 (local). 

Because I own the router between my network and my ISP, I used its software to add a static route that forwards traffic for addresses in 10.1.1.0/24 to the gateway PC. That machine has an address on 192.168.100.0/24 and a tunnel interface of 10.1.1.2. Traffic from, say, 192.168.100.50 to 10.1.1.1 would first arrive at the network's default gateway, the one between me and my ISP, and then forwarded to the gateway PC which sends it on to 10.1.1.1. The cloud machine has a route back to 192.168.100.0/24 via 10.1.1.2.

If you cannot modify the ISP's gateway router, you can add static routes to each workstation on your network that forward traffic for the cloud network to a gateway machine. It's just easier if you can centralize the routing on your network's default gateway.

---

### Post by keratos2 on 2020-04-09
Thankyou muchly for that detailed reply. 

I have used openvpn but ditched it despite making a raft of enhancements to speed it up.  I was getting max 20Mb/s on an 80Mb/s line.  I now hand craft ISPsec/L2TP solution that delivers 75Mb/s and it's a noticable improvement, very much. 

BTW, With openvpn it set up all the routes , so I do not know why you need to do that in your setup

SoftEther in IPsec/L2TP mode is good but I could never get clients to see each other on vthe VPN  so ditched that too.

---

