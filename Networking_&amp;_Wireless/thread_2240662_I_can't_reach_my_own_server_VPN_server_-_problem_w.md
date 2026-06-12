---
title: "I can't reach my own server VPN server - problem with iptables, NAT or VPN"
date: 2014-08-21
forum: Networking &amp; Wireless
---

### Post by pierre20 on 2014-08-21
Hello everybody!

This is my first post... but it's not going to be your usual, run-of-the-mill type "first post".
I need help with my setup. I have an error somewhere in my config or in my understanding of it. So, here she goes...

I have 3 computers and a Virtual Machine (Vbox) involved:
[B]
Server:[/B]
Runs Ubuntu 14.01.1 and is a webhost as well as a VPN host (pptp, as well as L2tp)
External IP: 123.456.789.001 (of course, it's not the real one)
Internal IP: 192.168.0.1
I also have a DHCP server configured which dishes out IP-addresses above and including 192.168.0.100 for VPN connections (no, I will never have more than 150 connections simultaneously, ever)
PPTP and L2TP have iptable rules attached to masquerade and forward all traffic.

**Gateway:**
Is a media center linux box running on ubuntu 13.10. It is connected to a router which servers as a WAN gateway. I also have two network cards in there eth1 and eth0
```
ETH1 (WAN): 192.168.56.2
ETH0 (LAN): 192.168.1.99
```

[B]Router (vbox on Gateway):
[/B]The router is running in VirtualBox on ubuntu 12.04. It has an ample amount of ram and full command over one the cores of it's hosts processor. All of the NICs are configured as bridged interfaces
```
ETH0 (WAN): 192.168.56.1
ETH0 (LAN): 192.168.1.10
PPP0 (pptp): 192.168.1.1xx
```
The router is configured to automatically connect to my server and establish a VPN connection, as well as to keep that connection up, or re-establish it as soon as it goes down. Iptable rules forward all traffic through to the ppp0 interface.
I am caching the hell out of my DNS with a program whichs name I just forgot.

Behind all that stuff sits a DDwrt router with it's DHCP server configured to give out the following to my workstation (I had problems getting the DHCP to run stable on my Router-Vbox, so I opted for the simple solution)
**Workstation(s)/Ipads/Cellphone/...:**
My Workstation is a Windows 7 PC
```
IP:192.168.1.20
Subnet:255.255.255.0
Gateway: 192.168.1.10
DNS1: 192.168.1.10
DNS2: 208.67.222.222
```

*The story behind this hot-mess:*
I am living in a foreign country and I need a VPN to access websites, as well as at least one layer of security when accessing my server (pptp... yes, I know that it's not perfect). My current country is also well known for messing with the DNS, that's why I need to bring in foreign DNS servers through my vpn and cache the results locally (over 300ms latency, not fun ... 1ms on my local cache, fun).
The media center Gateway however needs an untouched connection to the internet for streaming local TV over local IP addresses and for downloads/torrents (no need to send my Linux ISO's halfway round the world and eat up my precious server bandwidth).
My provider does not mind torrent traffic at all, or any other kind of traffic. The only problem they have is the amount of devices on their connection (not more than 3 or 5 devices, otherwise they'll induce some packet loss or hamper with your bandwidth or block port 80 - seriously). If I am right, they should only see three devices: the first small router, the media center and the Vbox-Router, right?
[I]
Is that concoction actually working?!
[/I]Yes, it is. It works beautifully... BUT and here comes the question

[B]_Why can't I reach my Server from my workstation?_
[/B]I started noticing a problem when I tried to SSH into my Server from my workstation. I just couldn't get through. I started looking into my NAT configuration but couldn't find anything out of the ordinary. I checked online, but my setup is kind of *unique* and I couldn't find much. Therefore I started reading up on Vbox's problems with SSH but came up short handed as well.
I made progress once I figured out that I couldn't even ping my Server from my workstation, which led me to believe that there is indeed something wrong with my NAT setup on the router. I started researching towards that direction again, but alas, came up empty handed. I had the feeling that my iptables would block all traffic other than port 80...
It was only now that I tried to ping another server directly under it's IP address... and it worked. Baffled, I tried to SSH into that server and it worked flawlessly.
I tried to SSH into my server from my router and it worked flawlessly.
I tried to SSH into my server from my workstation which was configured to use a different gateway, but was using my servers VPN... and it worked flawlessly.

I suspect the problem somewhere in my IPtables or in my IPconfig for the routers internal network - see how the server dishes out a 192.168.0.x and my router's internal net runs on 192.168.1.x? - However, should NAT not handle that?

Here's my IPtables rules on my router:

```
iptables -A FORWARD -o ppp0 -i eth0 -s 192.168.1.0/24 -m conntrack --ctstate NEW -j ACCEPT
iptables -A FORWARD -m conntrack --ctstate ESTABLISHED,RELATED -j ACCEPT
iptables -t nat -F POSTROUTING 
iptables -t nat -A POSTROUTING -o ppp0 -j MASQUERADE
```

Thanks in advance for helping or simply pointing me towards the right direction.

---

