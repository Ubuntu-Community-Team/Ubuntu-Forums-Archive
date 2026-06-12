---
title: "Unable to access PPTP server's external IP"
date: 2014-01-21
forum: Networking &amp; Wireless
---

### Post by Eric_Leung on 2014-01-21
Hi, I consider myself a newbie, and I am not good at explaining my problem. Sorry in advance.

I have an Apache development server (ex: 143.72.250.1  |  dev.example.com ) setup at work that is used only for internal dev purpose. I have UFW setup to only allow access from 143.72.0.0/16 to port 80. So that all workstation within this class B network can access it. It works well.

Now, I wish to access from the outside "securely". Since I only have one server, I installed PPTPd on 143.72.250.1. I have opened port 1723 to the world. It uses NAT and has an internal IP of 10.99.99.99. I have no problem getting internet access through PPTP or accessing OTHER servers that is blocked to the outside network through PPTP.

However, I cannot access the development server itself via its external IP or hostname, only via the internal IP (10.99.99.99) assigned by the PPTP NAT.

Example:
143.72.250.1 - Apache Dev Server, PPTP Server. Only allow access from the subnet. PPTP port open to the world.
143.72.250.2 - Other Server. Only allow access from the subnet.

My Macbook, located outside of the network, have no problem accessing 250.2 through PPTP. However, when I try to access 250.1, it tries to go the regular, non VPN, route (verified with traceroute). Of course, in the regular route, it gets blocked by the Firewall on 250.1.

I could get it work by editing the hosts file on my Macbook so dev.example.com always point to the internal IP (10.99.99.99). But the means when I bring my laptop to work, I have to either remove that line on the host file or always connect through PPTP.

What did I miss? Is it a UFW problem? NAT problem? PPTP problem? or problem with the setup on my laptop?

I setup pptpd following the instruction from this site: [http://silverlinux.blogspot.ca/2012/05/how-to-pptp-vpn-on-ubuntu-1204-pptpd.html](http://silverlinux.blogspot.ca/2012/05/how-to-pptp-vpn-on-ubuntu-1204-pptpd.html)

THANK YOU!

---

### Post by SeijiSensei on 2014-01-22
Dump PPTP and use SSH instead.  It's orders of magnitude more secure.  If you really do need to set up a tunnel with the server and not simply run a terminal session, then use [OpenVPN with static keys]("http://openvpn.net/static.html").

---

