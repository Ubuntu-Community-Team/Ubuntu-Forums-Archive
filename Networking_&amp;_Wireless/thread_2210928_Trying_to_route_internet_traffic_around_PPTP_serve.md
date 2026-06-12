---
title: "Trying to route internet traffic around PPTP server - NAT??"
date: 2014-03-13
forum: Networking &amp; Wireless
---

### Post by dale4 on 2014-03-13
Hi all,

Firstly, thanks to this forum ive avoided posting a question for over 3 years, this has been the one stop answer to all my questions!

Now im faced with a problem that i cannot seem to fix.
I have a Ubuntu Server 13.10, it runs PPTPd along with a host of other servers. 
Its IP address is:192.168.1.205
Its gateway is:192.168.1.1

The PPTP server is configured as:
localip 10.0.0.1
remoteip 10.0.0.100-199
bcrelay eth0

A windows client can connect and is given an IP address within the 10.0.0.x range however the only machine it can then ping is the VPN server, on both 10.0.0.1 and 192.168.1.205. It cannot ping anything else within the network, i dont want all the computers within the network to need to be connected to the VPN for communication between them, id rather the VPN server act as a NAT in a way.Further to this i use to use OpenVPN, with this software you can select on the server that you would not like to pass internet traffic though the VPN server, rather you would like the clients to send their data direct to the internet, i cannot for the life of me work out how i should set up the iptable to do this. 

The reason for this set up is i dont use a VPN to hide who i am or to change my IP address, i just use my VPN to access the internal network while im away from home. 

Any suggestions or pointers would be super great

many thanks
Dale

---

### Post by iloveyou2 on 2014-05-23
[HTML]iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE[/HTML]
I will always read original post once more before posting

try this on client side:
[IMG]http://cdn.joxi.ru/uploads/prod/2014/05/24/8ed/d46/5ddca9d0ffaa1863112a5a1c066890ef6cd41096.jpg[/IMG]

---

