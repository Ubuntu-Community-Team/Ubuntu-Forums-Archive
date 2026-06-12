---
title: "Relayed http access to openvpn clients via openvpn server"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by chillifire on 2008-06-08
The situation: 
I have a number of OpenWRT based routers out there (OpenWRT is a LINUX distro for embedded devices), which I manage via a Ubuntu 8.04 LINUX server they all connect to. The Ubuntu server has a public IP address (1.2.3.4 in the attached diagrams), the routers do not. To be able to connect to them the Ubuntu server is running an OpenVPN server, the routers connect to the server on start-up as openvpn clients. I can ping and ssh into the routers from my server - no problem.

What I want to achieve:
The routers have a web GUI which is accessed via normal http or https (don't mind too much). I would like to connect remotely to the routers' web interface through a browser from any desktop/laptop. 
Also, I would like to do so without having to have OpenVPN installed on the accessing PC/workstation, so I can connect from anywhere. This would obviously have to work through the Ubuntu server with the OpenVPN server, as only the Ubuntu server has any knowledge of the OpenVPN network and clients. 

I figure this should be possible with port and/or IP forwarding, once I am connected via http or https to the Ubuntu server, but I do not understand enough about networking to make this happen. 

I know what to do on the OpenWRT routers, so don't worry about that. 

But can anyone provide some ideas/hints how this translation and forwarding on the Ubuntu server can be achieved? 

Cheers

chillifire

---

### Post by nixscripter on 2008-06-08
The simplest way to port forward, in effect, is to tunnel in this case. ssh can accomplish this, though it might be a mess:

ssh -L 1234:10.8.1.1:8080

If run on the Ubuntu server, this would listen on port **1234**, and forward all data over the connection to port **8080** at **10.8.1.1**, which only it could see.

It would be a mess, but you could map one port per device, and then connect the central server in a normal browser with a port in the URL to access that device. (1234 -> 10.8.1.1, 1235 ->10.8.1.2 etc).

---

### Post by chillifire on 2008-06-08
Thanks for that response. I thought about ssh port forwarding but this seems unpracticable to me fi we are talking about a few hundred routers. This solution would require that hundreds of ssh sessions are opened and it would replicate a secure channel/tunnel, which has already been established by OpenVPN. So I think based on a secure communication path being available through OpenVPN the answer must be based somehow in iptables based forwarding. Thanks for the response though.

Anyone any idea how this could be achieved with iptables based prerouting/NATing and forwarding ?

Thanks

---

### Post by SpaceTeddy on 2008-06-09
yes... this can be done.

But before i go into how to do this - if anyone ever find those ports (via a portscan, for example), they access websites which **are not meant to be accessed over the internet**. Please consider this carefully as this can be a major security flaw !!!

that said, i can think of two ways to achive this with only browsers. I prefer option 2 as it is more secure, yet also more complicated to setup.

1.) port-forwarding via iptables.
in this scenario, every openWRT router has it's own port on the server. so by accessing 1.2.3.4:8080 you would be forwarded to the first router, by accessing 1.2.3.4:8081 you'd be kicked to second and so on. The rules you need are DNAT rules and they look like this:

```
sudo iptables -A PREROUTING --table nat -p tcp --dport 8081 -j DNAT --to-destination 10.8.a.b:80
```
this would forward a request to the server on port 8081 to the client with the ip 10.8.a.b on port 80.
Also, you'll need one generic rule so that the pakets can find their way back properly (this is now SNAT)
```
sudo iptables -A POSTROUTING --table nat -o tun+ -j MASQUERADE
```

and don't forget to enable ip_forwarding with this command:
```
sysctl -w net.ipv4.ip_forward=1
```

Again - this is insecure and anyone finding those port could access your routers ! I'd advise against it... strongly. 

2.) apache2 mod_proxy
In this scenatio you run an apache2 on the ubuntu (1.2.3.4) server. Here you can have authentification (against apache2) as well as ssl (again, via apache2) so the router can acctually be password protected and NOT be found via  a portscan. In your apache2 configuration you could then enable mod_proxy and redirect certain subfolders for the management interfaces of the approriate routers. For example, an access to [https://1.2.3.4/router1](https://1.2.3.4/router1) would kick you to the management interface of router1.

the Second setup is a lot harder, as it requires a lot more setup, and i am not entirely sure if the subfolder thing even works (as the routers have a directory structure aswell which might get in the way of the redirection. So this is a lot more trying. 

I am willing to help with a little if you run into problems with any of the setup. Just let me know how it goes.

hope it helps :)

---

### Post by chillifire on 2008-06-10
Thanks for the hint. Running apache is not an option on a 4MB flash memeory device. It is a busybox/haserl kind of setup. I understand you security concerns and agree that ports should only be opened when really needed.

---

