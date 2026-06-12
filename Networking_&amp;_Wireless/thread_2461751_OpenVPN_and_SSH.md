---
title: "OpenVPN and SSH"
date: 2021-05-06
forum: Networking &amp; Wireless
---

### Post by cccfran on 2021-05-06
Hi I have a Ubuntu 18.04 server with openVPN and openSSH installed. The openVPN is using the default setup of [https://github.com/angristan/openvpn-install](https://github.com/angristan/openvpn-install).

I am able to connect the VPN but cannot SSH or even ping when I am using Verizon wifi service. I can still access the Internet and my ip has changed to the server's public IP.

On the other hand, I am able to VPN and SSH to the server if I am using the hotspot. I suspected it is a firewall issue so I have tried resetting the router but in vain. I also called verizon support but the internet is fine and there is nothing they can do. 

I am frustrated because I have no idea what is going wrong now. I have been using my hotspot to connect to the remote server but it is not a lasting solution. Any idea? Thanks!

---

### Post by TheFu on 2021-05-06
Typically, carrier wireless/wifi APs hosted outside your home do not allow inbound connections.

Any inbound connection requires each network device in the way to forward the required port to the next inner layer.

OpenVPN could be a client or a server.  Those instructions claim to setup an openvpn server, which means someone had to modify the WAN router to forward that port into your internal system running the ovpn server process.  The same is required for ssh to work.

So, if you will get very specific and show real IPs, perhaps we can see what we can see from outside your LAN and be of help?

Resettings the router?  Not sure I understand how that would help.  Settings need to be modified to forward specific ports from the WAN (public IP) connection to your LAN server running each openvpn and ssh.  The LAN server should have a static IP on the LAN.

Terms like "Verizon wifi service" and "hotspot" are vague. Please be more specific.  Where are you when this is accessed?  What subnet is your client machine on?

There are some LAN routing things which could issues if you are at a cafe with a 192.168.1.x/24 subnet and your home LAN subnet is the same. Your home subnet should be a little weird.  I use 172.22.22.x and 172.22.21.x and 10.51.22.x, just to ensure that a cafe, coffee shop, hotel, subnet is unlikely to conflict.

---

### Post by cccfran on 2021-05-15
@TheFu. Thank you for your help. Yes I did try to reset the route but it did not work. 

Let me clarify the setup. On the server side, it is behind a router assigned with local ip 192.168.1.2 and I used [COLOR=#000000] [/COLOR][https://github.com/angristan/openvpn-install](https://github.com/angristan/openvpn-install) to set up an openVPN server. And an .ovpn file is generated for the client. The default of the setup is to use UDP and to listen to port 1194. On the client side, which where the problem is, I use Verizon for internet and the device is assigned 192.168.1.152 on the LAN. I am able to connect to openVPN using the .ovpn file. Then the public ip on the client side becomes the ip of the server when I search "my ip" on google. And the client is assigned with 10.8.0.5 on the LAN and I am able to ping the others in the subnet of openVPN (10.8.0.*). However I am not able to ping others in the subnet of the server (192.168.1.*). 

Then when I am typing this out loud, I see that the subnet clashes at the server side and the client side. I changed the server subnet and PROBLEM SOLVED. Now I see why when using the hotspot of a cell works: the hotspot subnet is different from the server's. Thanks!

---

