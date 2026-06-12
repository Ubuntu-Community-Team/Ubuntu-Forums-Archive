---
title: "How to make Ubuntu to forward the network traffic to a VPN (NordVPN or other ones)?"
date: 2023-04-29
forum: Networking &amp; Wireless
---

### Post by aquerci on 2023-04-29
my Ubuntu Machine is the gateway for a network and in this network there is a PC that needs to use a VPN like NordVPN or something like that, but I can't directly configure this machine.
my question is, is it possibile to install NordVPN in my Ubuntu machine, and forward all the connections coming from my PC to the tunnel interface?

if it is possible, what kind of VPN do you advice for me? I need a stable and strong VPN in order to put in safe my data and mainly to change my geolocalization (I need to change my source public IP with another one). I read that NordVPN could be a good solution, but it's not free and, before to buy it, I need to know if I can manage the incoming traffic toward its tunnel interface or not. is it possible or not? at the end I wanna use my Ubuntu machine like a network device.

---

### Post by SeijiSensei on 2023-04-29
I use OpenVPN. I have static connections between my home office and my remote servers.

[https://openvpn.net/community-resources/static-key-mini-howto/](https://openvpn.net/community-resources/static-key-mini-howto/)

I own both ends of these connections. The servers are VMs I rent from Linode. I've never used a commercial service like OpenVPN.

---

### Post by aquerci on 2023-04-30
I got what you did, but it's more expensive rent a remote server on internet than buy two years of NordVPN (it's around 100$) then I need to change my location choosing the country that I need and NordVPN has been created to do this too. I found [this]("https://support.nordvpn.com/Connectivity/Windows/1047409882/Sharing-a-VPN-connection-through-an-Ethernet-cable.htm") articol on their official website, it explains how to share the VPN connection with another PC, it's for windows but, if there is a tunnel interface as I see, my Ubuntu machine could redirect all the traffic from the other PC toward this interface using the routing logic! what do you think?


before to pay NordVPN I need to be sure about this solution. has anyone NordVPN? can you confirm that there is a tunnel interface that I can use to forward the traffic incoming from other fisica interfaces?

---

### Post by HuTkW$* on 2023-05-10
You can  forward all the connections coming from your PCs to a single tunnel interface, but it is really really hard to configure, like : [https://zone13.io/post/raspberry-pi-vpn-gateway-for-nordvpn/](https://zone13.io/post/raspberry-pi-vpn-gateway-for-nordvpn/)     ; should you use another way ...
I advise you to configure a machine working as a physical router assigned to this : Nordvpn propose a tutorial by configuring a  nordvpn tunneled gateway : [https://support.nordvpn.com/Connectivity/Router/1047409322/Setting-up-a-router-with-NordVPN.html](https://support.nordvpn.com/Connectivity/Router/1047409322/Setting-up-a-router-with-NordVPN.html) if you have a router, or, 
[https://www.vpnranks.com/reviews/nordvpn/pfsense/#:~:text=1%20Open%20your%20browser%20to%20sign%20in%20to,preferred%20server.%20...%204%20Go%20to%20VPN.%20](https://www.vpnranks.com/reviews/nordvpn/pfsense/#:~:text=1%20Open%20your%20browser%20to%20sign%20in%20to,preferred%20server.%20...%204%20Go%20to%20VPN.%20)
building a virtual pfsense machine working as a virtual router ...

Good luck !

---

