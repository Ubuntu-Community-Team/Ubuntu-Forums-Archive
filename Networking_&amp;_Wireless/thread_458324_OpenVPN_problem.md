---
title: "OpenVPN problem"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by nel2007 on 2007-05-29
Hi,
I am trying to create VPN access to my openvpn server from my laptop. 
On the server i am running windows vista and  XP SP2 on the laptop. Both machines have windows firewall disabled at the moment. The Server has AVG antivirus on which i also tried disabling. I did put exceptions for port 1194 when i had the firewalls enabled.
The server is connected to the internet through a netgear DG834GT asdl router and laptop connects via a dial-up connection.

Below is a copy of the config files for both Server and Client. 
Server;

dev tun
ifconfig 10.10.10.2 10.10.10.1
secret static.key


Client;

remote 81.174.152.10 
dev tun
ifconfig 10.10.10.1 10.10.10.2
secret static.key
mute 10


I have mangaged to ping my public IP address and I know this works.
However I keep getting the following when i tried to connect to the server;
  UDPv4 Conection reset by peer (WSAECONNRESET) (CODE=10054)

On the server it just hangs on the connection screen.. PLEASE Help!!

---

### Post by chimaster on 2008-05-27
Me too!

Tearing my hair out.  I've got OVPN running on various configs, but can't get this going at all (start basic and work your way up).

What can I say, It doesn't even work when both pc's are on the same subnet. Windows XP SP3 serving, Windows XP sp2 clienting. Limited config.  I know this doesn't belong on a ubuntu forum, but I think it's related. :-p

---

