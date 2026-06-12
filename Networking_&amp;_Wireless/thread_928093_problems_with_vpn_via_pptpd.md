---
title: "problems with vpn via pptpd"
date: 2008-09-23
forum: Networking &amp; Wireless
---

### Post by archerp01 on 2008-09-23
HI

I am using ubuntu server 8.04

I have set up pptpd

Using the following settings
/etc/pptpd.conf
localip 192.168.0.21
remoteip 192.168.3.252-254

/etc/ppp/options
ms-dns IPS Nameserver
ms-dns IPS Nameserver

added a user in
/etc/ppp/chap-secrets

carried out a 
echo 1 > /proc/sys/net/ipv4/ip_forward


I can connect ok from my Windows XP PC

it shows the following settings
Device Name		WAN Miniport (PPTP)
Device Type		vpn
Server Type		PPP
Transports		TCP/IP
Authentication		MS CHAP V2
Encryption		MPPE 128
Compression		(none)
PPP Multilink frm	Off
Server IP		192.168.0.21
Clent	IP		192.168.3.252

On the server
# route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.3.252   *               255.255.255.255 UH    0      0        0 ppp0
localnet        *               255.255.255.0   U     0      0        0 eth0
default         192.168.0.1     0.0.0.0         UG    100    0        0 eth0

:/var/log# ping 192.168.3.252
PING 192.168.3.252 (192.168.3.252) 56(84) bytes of data.

--- 192.168.3.252 ping statistics ---
11 packets transmitted, 0 received, 100% packet loss, time 10005ms


I get a message to say I can connect ok

But - I can not ping the server

From the server I can not ping the PC

Also when I connect I lose connectivity to the web on my pc


Any suggestions

Regards

Paul

---

### Post by IainPurdie on 2009-01-17
On your PC, go to the VPN connection in Network Connections. Right click and select Properties. Go to the TCP/IP section and go to Advanced. Remove the (default) tick in the box for "Use server as default gateway" or similar. I can't remember the exact wording and I'm not near an XP box - sorry! It should be obvious, though.

Disconnect / reconnect and you'll certainly have your internet back. With the tick in the box, the PC routes all web access down your VPN...

---

