---
title: "Can't see server after connecting through VPN (PopTop)"
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by lexarrow on 2007-05-04
I have set-up a server(Ubuntu Feisty) with a static routable address and installed pptpd server (administered through webmin).

local ip is 10.0.0.1
remote ip 10.0.0.*

I use a Windows Vista laptop to connect to the server through VPN. The connection works, but I have no Internet access afterwards. When I uncheck the "use default gateway on remote network" in the TCP/IP advanced settings, I can't see the server.

Another thing would be that I don't see a gateway assigned in Vista's VPN connection status and I get IPv4 local connectivity and IPv6 limited connectivity.

I have also enabled DNS server 10.0.0.1 and WINS server 10.0.0.3 from pptpd.conf file.

I would like both to access the server through VPN, still using clien'ts internet connection, or see  the server and use its internet connection through VPN.

Thanks in advance for your help.

---

### Post by Metacarpal on 2007-05-05
Here's a quick and easy for you:
Install these two packages: vpnc network-manager-vpnc

Once those are in, just left-click your network-manager applet, and you'll have a new menu for VPNs.  Click on Configure VPNs, then Add, and you'll get a wizard to enter your VPN info.  If you already have a configuration file, you can load it from there.

---

### Post by lexarrow on 2007-05-05
thx, I will try it and post the result

---

### Post by CCIEMD on 2007-05-06
I am having the same problem.
I have a windows VISTA computer and trying to connect to an UBUNTU 7.04 vpn server
with the POPTOP PPTP server.
I can connect to the linux vpn but have no Internet access through the tunnel.
(Unchecking the 'Use default gateway on remote server' causes Internet activity to route
directly through the local LAN/router which defeats the purpose of a Tunnel)
Also, cannot view the remote (server) samba shares.

Any help is appreciated.
Thanks.

---

### Post by lexarrow on 2007-05-07
it doesn't work but I've been reading some more and poptop doesn't assign a gateway, the computer should...but it doesn't. My question now is how to get a gateway assigned to the VPN client.

---

### Post by Opasen on 2007-08-25
I'm having the exact same problem as you.

From my XP machine I can connect to my Ubuntu VPN Server but cannot connect to the internet through the tunnel. When I do an ipconfig /all on my XP machine the IP address is the remote IP address which i set and correct, but it makes the gateway that IP as well and my subnet is 255.255.255.255 when it should be 255.255.255.0.

I've tried searching Google for a way so you can set your own gateway and subnet, I'm hoping that would fix the problem.

I'll keep searching and if I find a fix I'll definitely post it here, but if somebody could shed some light that would be excellent :)

Cheers

---

### Post by moon2js on 2007-09-12
> **Metacarpal said:**
> Here's a quick and easy for you:
Install these two packages: vpnc network-manager-vpnc

Once those are in, just left-click your network-manager applet, and you'll have a new menu for VPNs.  Click on Configure VPNs, then Add, and you'll get a wizard to enter your VPN info.  If you already have a configuration file, you can load it from there.

I just googled vpnc and it looks like it's a "client for the Cisco IPsec servers." Does that work with PopTop/pptpd?

---

### Post by moon2js on 2007-09-13
> **lexarrow said:**
> 
local ip is 10.0.0.1
remote ip 10.0.0.*

Can someone explain a bit about the [poptop/pptpd config]("http://poptop.sourceforge.net/dox/pptpd.conf.txt")? I've read the man and online stuff, but I'm still a bit fuzzy, especially on what localip is in the basic situation of a home server (192.168.1.x) behind a router (192.168.1.1), the latter of which does DDNS.

---

### Post by marcgvky on 2007-09-14
Can someone post a "working" poptop config file? I know this can't be as hard as I am making it! :)

---

### Post by Audiosears on 2008-02-02
I'm with you guys - I've been trying to get a PoPToP server running for a few days with the same symptoms.  In my case, I'm running a Gutsy server and attempting to use the built-in MS VPN client as most of our client machines are XP-based.

I too can seemingly connect and authenticate fine using MS-CHAPv2, but cannot actually get to anything on the remote network.

The network is in the office, run on a simple D-Link DGL-4300 whose port 1723 is forwarded to the server (192.168.1.9), and has built-in PPTP pass-through for GRE.  I assigned 192.168.1.175-199 for clients, and like you guys get the combination of the first IP with 255.255.255.255 as the subnet.

Another curious thing though is that I can connect the first time fine, and the connection seems stable, but if I manually disconnect and try to re-connect, it will hang at verification unless you wait about 15 mins to reconnect. This may be because the server is not recognizing the timeout, but I am administering via Webmin, and the options in the module don't go into great detail.

---

### Post by kafitz22 on 2008-04-01
Anyone got a solution for this? I'm also experiencing the aforementioned problems.

---

### Post by opteron180 on 2008-04-06
Hi,

I have a Windows 2003 PPTP RAS server, everything works fine if client is xp.

For vista and Ubuntu I am experiencing the same problem even through I am able to connect. (255.255.255.255 subnet and cannot browse computers)

Ubuntu users: u may need to manually set DNS server because client may not able to grab the right DNS. I suggest you use openDNS.

Researching the problem and will post updates/ findings!

---

