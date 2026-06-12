---
title: "VPN (PPTP) without NetworkManager"
date: 2008-05-30
forum: Networking &amp; Wireless
---

### Post by Eugene RIMMER on 2008-05-30
I've got a LAN broadband connection. IP (static) 10.73.187.2, Gateway 10.73.187.1, no DHCP or zeroconf. When I need to get to the web, I have to engage a VPN connection to 10.73.100.1 with password authentification, no encryption. Everything goes fine under Windows, the connection driver seems to be PPTP. I get a new (automatic) IP address for it, but still it is some 192.168.x.x. When there's no VPN, I've got no Internet, only LAN. (Technically, I seem to get connected to some higher-range providers LAN, which is behind NAT and is needed for accounting reasons, obviously).

I tried to install network-manager-pptp into both Ubuntu and Kubuntu. The only problem is that for using it I have to rely on NetworkManager to configure my LAN connection, but since there's no zeroconf services in our LAN, NetworkMAnager configures my LAN improperly (gets some 169.x.x.x IP, and my prov dismisses me from LAN). Hence, I cannot see the VPN server, and VPN connection fails.

What should I have to do now? Is there any way to tell NM which IP/Gateway to use (it's poor old desktop, nothing's gonna change here, hence no roaming for me please)? Or should I use non-NM-methods rather?

---

### Post by Eugene RIMMER on 2008-07-22
Ok, problem is successfully solved. NetworkManager has nothing to do with Kubuntu, kvpnc is way better. We need debs for `kvpnc`, `menu` and appropriate backend program (`pptp-linux` in my case, fortunately found on Kubuntu CD, and this is your case also, if you used a dead simple VPN connection from Network Neighborhood under MSWin - it is PPTP protocol). 

Install the backend, menu and kvpnc (in this very order). Then run ```
$ kdesu kvpnc
``` (also accessible through main menu), configure the program itself and the connection (it was tricky to do this as our providers support couldn't help me much), you might need to play around with some options. If you try the connection and kvpnc connects successfully, but disconnects after a few seconds, then you need to add a route to your VPN host (that's easy as long as you know it's address, I'll describe the setup soon). That's basically it. I have VPN-routed Internet @ home now.

Eat this, community.

---

### Post by dmsurti on 2008-08-23
Hi,

I have got a similar setup. I work on my office LAN, but till I engage in a VPN connection, I have no access to world wide web.

I hand configured the script and it works fine.

Log extracts :

CHAP authentication succeeded
MPPE 128-bit stateless compression enabled
local  IP address <some address>
remote IP address <some address>
primary   DNS address <some address>
secondary DNS address <some address>

====================

With this I can access only my gateway on my office LAN, and the VPN
server 64.x.x.x

AFter running the script i do the following:

sudo route add -host 64.x.x.x gw 192.x.x.x dev eth0
sudo ip route replace default dev ppp0

where 192.x.x.x is my gateway on my office LAN.

Now I can access the web.

However, When I use my VPN connection from Windows it is pretty fast. For example I try downloading sun jdk and I get speeds of say 150Kb/sec in Windows but only around 10KB/sec in Ubuntu. What could be the reason?

These are logs that I see :

sent [LCP EchoReq id=0x1 magic=0xe8baef30]
rcvd [LCP EchoRep id=0x1 magic=0x17dc16b 09 01]
sent [LCP EchoReq id=0x2 magic=0xe8baef30]
rcvd [LCP EchoRep id=0x2 magic=0x17dc16b 09 02]
sent [LCP EchoReq id=0x3 magic=0xe8baef30]
rcvd [LCP EchoRep id=0x3 magic=0x17dc16b 09 03]
sent [LCP EchoReq id=0x4 magic=0xe8baef30]
rcvd [LCP EchoRep id=0x4 magic=0x17dc16b 09 04]


I am a novice as far as networking is concerned. Since you have a similar setup, it could be great if you can throw some pointers as to why this is happening?

Also a point to note is that ppp0 is assigned local and remote IPs in the range 172.x.x.x whereas my VPN server is 64.x.x.x

Thanks in advance,
Deepak Surti, India

---

