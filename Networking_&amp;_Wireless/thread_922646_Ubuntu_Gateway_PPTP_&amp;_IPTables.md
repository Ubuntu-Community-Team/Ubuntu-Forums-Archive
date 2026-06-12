---
title: "Ubuntu Gateway PPTP &amp; IPTables"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by RogueEntity on 2008-09-17
A few months back, I decided to turn my server machine into a gateway for my network, the system has two NIC's and is configured to connect to my DSL provider through one of them. I wrote an iptables script to configure forwarding so hosts on my LAN could access the internet, and poke holes to allow me to connect to my machine remotely. It all worked fine, other PC's on my network could access the internet, and everything worked (MSN, AIM, Skype etc). I wanted a better setup than a bog-standard home router could do, without spending the money on expensive Cisco gear which would be overkill. The only problem, is that PPTP was not working.

My dad uses PPTP (that built-in windows VPN client) to connect to his company network, and it works fine through the bog-standard home router I have, but it wont work when connecting through my gateway machine. This means I have to stick with the old setup, so that he can still connect in when he needs to, and it means I cant have my gateway machine to do what I want, including auto-scanning downloads for viruses using a transparent proxy.

I wiped the machine clean and installed Ubuntu Server 8.04 using kernel 2.6.24-19-server 64bit, I configured the machine to connect to the DSL provider and I used the same IPTables script I had used before under Debian.

I had tried seeking support for the problem on an Irish site (boards.ie), as well as Experts Exchange and also on debian's forums and mailing list and I got none. It was a friend of mine who told me that Ubuntu offers better support, and since its debian based, the system would be familier to me, which is why I reinstalled it.

My iptables script is as follows:
```

#!/bin/sh

#
# Firewall & Gateway Script v0.3
#

# Delete Existing Rules
#
iptables -F
iptables -t nat -F
iptables -t mangle -F
iptables -X

#  
# GREEN LAYER - Always Accept (Trusted Stuff)
#

# Always Accept Loopback Traffic
#
iptables -A INPUT -i lo -j ACCEPT

# Always Accept LAN Traffic from our Network
# We might remove this later, so we can restrict outgoing traffic..
#
iptables -A INPUT -i eth0 -s 192.168.0.0/24 -j ACCEPT

#
# BLUE LAYER - Logging..
#
iptables -A FORWARD -j LOG --log-prefix "IPTF: "
iptables -A INPUT -j LOG --log-prefix "IPTI: "

#
# YELLOW LAYER - Configure our Gateway
#

# PPTP Forward/Passthrough
#
iptables -A INPUT -p gre -j ACCEPT
iptables -A FORWARD -p gre -j ACCEPT

# Allow Established Connections
#
iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT
iptables -A FORWARD -i ppp0 -o eth0 -m state --state ESTABLISHED,RELATED -j ACCEPT

# Allow Outgoing to the Internet
#
iptables -A FORWARD -i eth0 -o ppp0 -j ACCEPT

# Enable NAT Masquerade
#
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE

# Transparent Proxy Redirect
#
#iptables -t nat -A PREROUTING -i eth0 -d ! 192.168.0.254 -p tcp --dport 80 -j DNAT --to 192.168.0.254:3128

#
# ORANGE LAYER - Poke Holes for Services
#

# Allow HTTP
#
iptables -A INPUT -p tcp -m state --state NEW --dport 80 -j ACCEPT

# Allow Restricted Access to SSH
#
iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --set
iptables -A INPUT -p tcp --dport 22 -m state --state NEW -m recent --update --seconds 60 --hitcount 3 -j DROP
iptables -A INPUT -p tcp --dport 22 -j ACCEPT

#
# RED LAYER - Drop Everything like a Hot Potato
#

iptables -P INPUT DROP
iptables -P FORWARD DROP

# Enable Forwarding
#
echo 1 > /proc/sys/net/ipv4/ip_forward

```

I searched Google for information on PPTP forwarding through NAT, and a lot of what I found pertains to using v2.4 of the kernel and modules: ip_nat_proto_gre & ip_conntrack_proto_gre
I had found threads here on the matter, but they suggested no problems with using PPTP over an iptables NAT. But they dont tell me much beyond that, and I am stuck on this issue, having found no useful help or advice anywhere else.

I tried loading ip_nat_pptp and ip_conntrack_pptp modules, which loads a few others including nf_conntrack_proto_gre and nf_nat_proto_gre. I dont know if they are newer versions of the older ip_nat_proto_gre/ip_conntrack_proto_gre modules or not. I has also read that GRE/PPTP support is broken in kernel 2.6.

I have only one physical machine that I can use as a gateway, and it also operates as a File/Print and DNS server for my home network (the latter because my ISP's DNS servers are flakey, and OpenDNS caused me problems).

I tried connecting both before, and after loading the ip_nat_pptp/ip_conntrack_pptp modules, with no success. I also tried re-running the firewall script after it. I have watched the logs while I tried to connect.. and connections were established on TCP port 1723.. but no GRE connections were established (or logged), not even attempted.. its like there is no support for it.. and I am honestly at a loss and desperate for help on this issue. If I cant fix it, I will just have to stick with my home router.. or install a dedicated distribution like IPCop, SmoothWall or ClarkConnect.. and install Samba and Bind on top of that... not an ideal situation.

---

### Post by RogueEntity on 2008-09-22
*bump*
Anybody?

---

### Post by seachnasaigh on 2008-10-16
The problem may not be your configuration of Ubuntu, necessarily.

Your da logs in via (I'm assuming) a Windows machine, using PPTP to a Windows VPN server on his company's network. There are some quirks to MS VPN (what they call RRAS). One of them is that the client has to have a unique resolvable IP to the RRAS server on the far end; my reading of your script does not allow for this. Instead, what the RRAS server on the far end will see is the masqueraded IP of your gateway server, to which IP it will attempt to respond to create the VPN tunnel. Your gateway server may not (I suspect does not) understand what to do with this traffic, as it doesn't see it as established/related and does not respond properly to the RRAS server on the far end. Your da sees a 721 error on his end. 

We've solved this on a corporate network by creating a VLAN for MS VPN traffic, and then creating a layer 3 rule about it on the Linux server that passes the traffic through. However, that was from the outside > inside; I'm not 100% sure this would work the other way round. 

If you have another static IP address that you could assign on the outside to your da's machine on the inside, you could create a static NAT that would route traffic destined to the world using that IP, and then route VPN traffic from the world back to that external IP directly to your da's machine. That may be impossible or prohibitively dear.

Alternatively, you could create a destination NAT to your da's machine if you could identify the character of the inbound traffic for his RRAS connexion. For example:

$IPTABLES -I INPUT -d [your external IP] -p tcp --dport 1723 -j ACCEPT
$IPTABLES -I FORWARD -p tcp --dport 1723 -j ACCEPT
(you're explicitly accepting this port 1723 traffic)
$IPTABLES  -A PREROUTING -t nat -p tcp -d 192.168.x.x [your da's internal address] --dport 1723 -j DNAT --to 192.168.x.x:1723
(you're creating a destination NAT to a specific internal address for such traffic, establishing the 1:1 relationship that MS RRAS is looking for)

Tinker with that a bit; that's how we handle some of these connexions, through prerouting rather than through input. Let me know how it works for you. 

Cheers.

--ckr

EDIT: Oops, sorry. In the example above, it should have been 
$IPTABLES  -A PREROUTING -t nat -p tcp -d x.x.x.x [your external address] --dport 1723 -j DNAT --to 192.168.x.x:1723

Sorry, rather late here and I'm quite tired, I missed that whilst typing it out. 
Also, sorry for the rather old-school RedHat syntax; I'm sure you can translate. 

--ckr

---

### Post by RogueEntity on 2008-10-31
I tried connecting with my Mac laptop with a bogus username/password, and it connected and prompted me for the correct password. The firewall logs showed connections both on TCP 1723 and on Protocol 47 (GRE).

However, on the Windows PC, it still refuses to connect, even if I disable encryption, it just times out and says it cannot find the VPN server.

Anyone hazard a guess as to why ppptpclient (Mac), will connect, while the Windows VPN client just times out. Why when connecting through the mac, I see GRE activity on the firewall logs, but nothing happens when I try connecting with Windows.

---

### Post by nardis_Miles1 on 2009-01-15
I'm just wondering whether there has been any resolution. I am also having difficulties making a connection to a pptp VPN from behind an IPTABLES firewall. 

In the daemon.log file, I receive the following:

Jan 15 18:40:00 lapdog NetworkManager: <info>  Will activate VPN connection 'Silicon Space Tech', service 'org.freedesktop.NetworkManager.ppp_starter', user_name '*******', vpn_data 'ppp-connection-type / pptp / pptp-remote / **.**.*.* / usepeerdns / yes / encrypt-mppe / yes / encrypt-mppe-128 / yes / encrypt-mppe-stateful / yes / compress-mppc / no / compress-deflate / no / compress-bsd / no / ppp-lock / yes / ppp-auth-peer / no / ppp-refuse-eap / yes / ppp-refuse-chap / no / ppp-refuse-mschap / no / mtu / 1416 / mru / 1416 / lcp-echo-failure / 10 / lcp-echo-interval / 10 / ppp-extra /  / ppp-debug / yes / usepeerdns-overtunnel / yes / routes /  / use-routes / no', route ''.
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 1 of 4 (Connection Prepare) scheduled...
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 1 of 4 (Connection Prepare) ran VPN service daemon org.freedesktop.NetworkManager.ppp_starter (PID 7922)
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 1 of 4 (Connection Prepare) complete.
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 2 of 4 (Connection Prepare Wait) scheduled...
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 1 -> 6.
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 2 of 4 (Connection Prepare Wait) waiting...
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 2 of 4 (Connection Prepare Wait) complete.
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 3 of 4 (Connect) scheduled...
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 3 of 4 (Connect) sending connect request.
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 3 of 4 (Connect) request sent, waiting for reply...
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 6 -> 3.
Jan 15 18:40:00 lapdog pptp[7926]: anon log[main:pptp.c:267]: The synchronous pptp option is NOT activated
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 3 of 4 (Connect) reply received.
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 4 of 4 (IP Config Get) timeout scheduled...
Jan 15 18:40:00 lapdog NetworkManager: <info>  VPN Activation (XX) Stage 3 of 4 (Connect) complete, waiting for IP configuration...
Jan 15 18:40:11 lapdog NetworkManager: <WARN>  nm_vpn_service_process_signal(): VPN failed for service 'org.freedesktop.NetworkManager.ppp_starter', signal 'ConnectFailed', with message 'VPN Connection failed'.
Jan 15 18:40:11 lapdog NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 3 -> 5.
Jan 15 18:40:11 lapdog NetworkManager: <info>  VPN service 'org.freedesktop.NetworkManager.ppp_starter' signaled state change 5 -> 6.
Jan 15 18:40:11 lapdog NetworkManager: <WARN>  nm_vpn_service_stop_connection(): (VPN Service org.freedesktop.NetworkManager.ppp_starter): could not stop connection 'XX' because service was 6.


The rules in rc.firewall are

echo "   Enabling SNAT (MASQUERADE) functionality on $EXTIF"
$IPTABLES -t nat -A POSTROUTING -o $EXTIF -j MASQUERADE
$IPTABLES -A INPUT -p gre -j ACCEPT
$IPTABLES -A FORWARD -p gre -j ACCEPT
$IPTABLES -I INPUT -d xx.xx.x.x -p tcp --dport 1723 -j ACCEPT
$IPTABLES -I FORWARD -p tcp --dport 1723 -j ACCEPT
$IPTABLES -A PREROUTING -t nat -p tcp -d xx.xx.x.x --dport 1723  -j DNAT --to 192.168.2.109:1723

I can connect if my laptop is outside the firewall. I should note that the connection si through a DSL modem, to a firewall box (IPTABLES implemented there), through a linksys router.

Any help would be appreciated.

Art Edwards

---

