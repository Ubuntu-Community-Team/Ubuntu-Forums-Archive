---
title: "Remote Network Administration"
date: 2008-09-26
forum: Networking &amp; Wireless
---

### Post by RFXCasey on 2008-09-26
Is there any way to remote desktop from the internet to your home network and choose (at will) which network computer you will be controlling for that session? Then later (probably a new session) connect to a diffenent machine on that same network. Or can you only connect to one machine on the network and then possibly have that machine control another. I hope my question makes sense. Or does one main network computer have to host shares to the other machines on your internal network if you want access to specifics files? 

   OK the question will probably be asked "what am I trying to accomplish?" I have no idea.... No but seriously, I have a home network with 2 Ubuntu desktops, one Mame arcade machine running windows,a Dell poweredge server running debian,and a wireless access point(used for the arcade machine and my laptop) all connected to a wired router which is then connected to my cable modem. I also have a laptop I would like to use to administer the network via the internet while I'm out in the world. Can everyone give me suggestions on a network strategy. I could just connect to the Dell poweredge server via Remote desktop and then possibly have shares from the other machines mounted on it but that seems to limited for me. I want to be able to control it all. Or maybe a better question would be If I have a laptop I want to use to connect to my home network from anywhere, is there a way to have total reign over the network and all machines there in?

---

### Post by doug-M on 2008-09-27
Sounds like you have a number of things you want to accomplish:
- Incoming connection from the outside world to one or more of your machines.
- Assuming I can connect to a machine how do I remotely control it.

I'll address a bit of the first one. Probably the best way of doing this would be with a VPN connection such as OpenVPN. If you have a static IP address on your cable modem then you should be able to set up port forwarding to one of the machines so that machine can act as a VPN server. In fact you can do this with some routers such as flashing DD-WRT onto a Linksys WRT54G or many other brands. Once the VPN is connected your laptop should be able to reach all the machines.

Another approach would be to port forward ssh to one of the machines and use ssh to tunnel your X desktop. You could probably ssh to another machine in your network then do the X desktop tunnel.

---

### Post by doug-M on 2008-09-27
Oh I forgot. If you have a dynamic IP address from your ISP then you can use something like dyndns.org, along with a little client program on one of your machines, to be able to contact your network.

---

### Post by RFXCasey on 2008-09-29
Right, sounds good. I don't have a static IP on my modem but I do have an account on Dyndns that posts a domain name that is constantly updated with my current IP. I believe this will work because I already use it to host an FTP server in my garage. Is the tunneling process complicated. I haven't' even set up SSH yet. Any advise on that and will I have to make special accommodations in my firewall to allow traffic to pass or does it use standard ports? I will read up on all this tonight. Thanks for the information.

---

### Post by doug-M on 2008-09-29
For the VPN stuff you could read up here:
[http://openvpn.net/howto.html#quick](http://openvpn.net/howto.html#quick)
I prefer doing it routed and with a PKI (not static key) but YMMV.

Ssh uses a standard port, openvpn uses a standard port as well although not as many firewalls know it by name, in any case the default openvpn port is 1194. 

Some people put it on port 80 (HTTP) or 443 (HTTPS) in order to avoid being blocked by other firewalls.

---

### Post by RFXCasey on 2008-09-30
Cool beans! If I knew how to post a thanks I would.:D

---

### Post by doug-M on 2008-09-30
More information about OpenVPN here:

Concise OpenVPN installation. . .?
[http://ubuntuforums.org/showthread.php?t=812065](http://ubuntuforums.org/showthread.php?t=812065)

I think to give thanks you hit the little icon that looks like a star or medal in the bottom right corner of a post by someone else.

---

