---
title: "Iptables and network configurations issues/questions"
date: 2020-03-18
forum: Networking &amp; Wireless
---

### Post by runenlyd on 2020-03-18
Hello folks !

I'm a newbie, first days on linux oriented stuff, but I wanna do great things ! :D 

My plan is to have a Freenas server and to do lots of things within. First I installed PiHole on it to in a VM using Ubuntu 18.04 TLS. Working perfectly. I had to stop DHCP server on my router to use PiHole (activating DHCP inside). Then on an another VM I installed another Ubuntu 18.04 TLS to VPN all my network. I followed point by point Jeff's Craft Computer tutorial ([https://www.youtube.com/watch?v=xFficDCEv3c](https://www.youtube.com/watch?v=xFficDCEv3c)) to do it but I got issues when I'm doing ```
sudo bash /etc/openvpn/iptables.sh
```

If I do sudo bash connect.sh I'm connecting to openvpn, i'm sure it works because curl ifconfig.me gives me another address than my public address and I can ping 8.8.8.8 correctly from here. But when I do sudo bash iptables.sh before, I can't even ping google, all connections are blocked.

All my computers are on 192.168.1.xx (Freenas on 30, PiHole on 40, Openvpn on 50....). 

Here is my iptables.sh file, and I don't know what to do then.
 Hope you can help me :) And I hope I'im clear enough, I'm new to this and not english :)



```
[COLOR=#000000][FONT=Arial]#!/bin/bash[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]# Flush[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -t nat -F[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -t mangle -F[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -F[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -X[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# Block All[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -P OUTPUT DROP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -P INPUT DROP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -P FORWARD DROP[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# allow Localhost[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A INPUT -i lo -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A OUTPUT -o lo -j ACCEPT[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# Make sure you can communicate with any DHCP server[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A OUTPUT -d 255.255.255.255 -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A INPUT -s 255.255.255.255 -j ACCEPT[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# Make sure that you can communicate within your own network[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A INPUT -s 192.168.1.0/24 -d 192.168.1.0/24 -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A OUTPUT -s 192.168.1.0/24 -d 192.168.1.0/24 -j ACCEPT[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# Allow established sessions to receive traffic:[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# Allow TUN[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A INPUT -i tun+ -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A FORWARD -i tun+ -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A FORWARD -o tun+ -j ACCEPT[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -t nat -A POSTROUTING -o tun+ -j MASQUERADE[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A OUTPUT -o tun+ -j ACCEPT[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# allow VPN connection[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -I OUTPUT 1 -p udp --destination-port 1194 -m comment --comment "Allow VPN connection" -j ACCEPT[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# Block All[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A OUTPUT -j DROP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A INPUT -j DROP[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A FORWARD -j DROP[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]# Log all dropped packages, debug only.[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]iptables -N logging[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A INPUT -j logging[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A OUTPUT -j logging[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A logging -m limit --limit 2/min -j LOG --log-prefix "IPTables general: " --log-level 7[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables -A logging -j DROP[/FONT][/COLOR]

[COLOR=#000000][FONT=Arial]echo "saving"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]iptables-save > /etc/iptables.rules[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]echo "done"[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#echo 'openVPN - Rules successfully applied, we start "watch" to verify IPtables in realtime (you can cancel it as usual CTRL + c)'[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#sleep 3[/FONT][/COLOR]
[COLOR=#000000][FONT=Arial]#watch -n 0 "sudo iptables -nvL"[/FONT][/COLOR]

```[COLOR=#000000][FONT=Arial]
[/FONT][/COLOR][FONT=Verdana]
[/FONT]

---

### Post by TheFu on 2020-03-18
The way that routing knows where to send traffic is by differences in the subnets.  If that difference is hidden, for any reasons, or it tries to route to the subnet already being used, then it won't work. To avoid the problem, you'll need 3 different subnets.

[LIST]
[*]Home
[*]VPN
[*]Where ever the VPN client is
[/LIST]
These must, MUST, be different.

First, using 192.168.1.0/24 for any of those subnets should be avoided. It is too common around the world, so when you are at a cafe, the local subnet there will likely be 192.168.1.0/24.  How can the VPN route traffic from 192.168.1.0/24 in the cafe to 192.168.1.0/24 at your house?  It cannot.

We don't have any control over the LAN at someone else's house, business, cafe, whatever, so we much make our home LAN and VPN LAN have odd subnets.

Step 1: make your home subnet something not commonly used. Avoid 192.168.0.0/24 192.168.1.0/24 192.168.100.0/24 10.1.10.1/24, or any common, human, numbers for subnets.  Make them odd.  192.168.131.0/24 or 10.9.8.0/24 or 172.31.21.0/24.  You cannot just pick any subnet you like. These must be in the specific ranges allowed for "private" LANs.   Wikipedia has an article about that.

Start there.

---

### Post by runenlyd on 2020-03-18
Thanks for you answer. Yes, that sounds totally wise. Just to be sure, before doing mistakes : for example I turned off DHCP on my ISP router to have PiHole managing DHCP between 192.168.1.0 and 198.168.1.100. If I set in DHCP server a range like 108.45.22.0 and 108.45.22.100 in PiHole and put my other machines with static IPs on this range that's ok ?(sorry if it sounds dumb)

---

### Post by TheFu on 2020-03-18
> **runenlyd said:**
> Thanks for you answer. Yes, that sounds totally wise. Just to be sure, before doing mistakes : for example I turned off DHCP on my ISP router to have PiHole managing DHCP between 192.168.1.0 and 198.168.1.100. If I set in DHCP server a range like 108.45.22.0 and 108.45.22.100 in PiHole and put my other machines with static IPs on this range that's ok ?(sorry if it sounds dumb)

You cannot just pick IPs out of the blue.  They MUST be from the private LAN subnet ranges and the rest of the network MUST know about those ranges.  108.45.22.100 is a public IP.  You cannot use it without breaking stuff.

DHCP ranges and static IPs should NOT overlap. That's basic DHCP stuff.  Say you use  192.168.131.0/24 (which isn't a bad choice).  Then all your systems LAN IPs would be in that range.  Say static IPs are .1 - .50 and DHCP IPs are .100-.254.  Ok?   Personally, I limit DHCP IPs to be 3x the number of guest devices I expect. My known devices are static either through local file-based configuration or by using DHCP reservations to the static IP range for that subnet.
[https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](https://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management)

I don't use pi-hole and won't pretend to know all that it does. Often there are subtle choices tools like that have to make that would be less than standard.

---

### Post by runenlyd on 2020-03-18
Thanks a lot. I'll set a better private LAN, configure everything correctly and try again :)

---

### Post by SeijiSensei on 2020-03-18
I didn't read your rules carefully, but blocking the OUTPUT chain can certainly cause issues.  This would only make sense if you're worried that computers on your network were taken over by malware and are attempting to communicate with host upstream.  If that's a concern, you can add rules for it later on.  Trying to debug problems when you have blanket policies like dropping OUTPUT packets becomes very difficult.

---

