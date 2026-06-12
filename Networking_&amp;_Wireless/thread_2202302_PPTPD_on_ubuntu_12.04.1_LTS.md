---
title: "PPTPD on ubuntu 12.04.1 LTS"
date: 2014-01-28
forum: Networking &amp; Wireless
---

### Post by wowlol on 2014-01-28
Hi,

I recently bought a VPS, and wanted to set up a VPN with IP forwarding on it, both for resource sharing, and to DDoS protect a couple of servers.
I am not very experienced with networking on linux, but generally i can get by. However in this instance, i am a little stuck. When i connect to my pptpd server running on the VPS, the client never gets given a default gateway, and by extension has no internet access when using this connection as primary.
I followed this  [https://help.ubuntu.com/community/PPTPServer](https://help.ubuntu.com/community/PPTPServer) precisely, just with the addition of the following lines in /etc/rc.local to fix a GRE and authentication bug.
iptables -A INPUT -p gre -j ACCEPT
iptables -A OUTPUT -p gre -j ACCEPT
iptables -A INPUT -p tcp --sport 1723 -s 192.168.0.1 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 1723 -d 192.168.0.1 -j ACCEPT

Which means my rc.local has ONLY the following in it:

iptables -t nat -A POSTROUTING -s 192.168.0.0/24 -o eth0 -j MASQUERADE
iptables -A FORWARD -p tcp --syn -s 192.168.0.0/24 -j TCPMSS --set-mss 1356
iptables -A INPUT -p gre -j ACCEPT
iptables -A OUTPUT -p gre -j ACCEPT
iptables -A INPUT -p tcp --sport 1723 -s 192.168.0.1 -j ACCEPT
iptables -A OUTPUT -p tcp --dport 1723 -d 192.168.0.1 -j ACCEPT

In my pptpd.conf i have the following IP setup going on:
localip 192.168.0.1-10
remoteip 192.168.0.100-254

 

I am wondering if the reason this is not working, is because this tut  was meant for setups in a NAT environment, which is not the case here,
and as a result i have managed to confuse the settings by interchanging the public IP of the server, for a (non existent) NAT one.
This is reinforced by when i attempt to ping the servers public IP while connected with no gateway, i get a reply, but when i try and ping 192.168.0.1
there is no reply. Also, if i ping google, DNS resolution seems to work, as i get google's IP, however am unable to route to it, neither can i ping an external IP such as 8.8.8.8.

This is the ifconfig of the server, so you can get an idea of how it's currently setup.



lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:38 errors:0 dropped:0 overruns:0 frame:0
          TX packets:38 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1900 (1.9 KB)  TX bytes:1900 (1.9 KB)

ppp1      Link encap:Point-to-Point Protocol
          inet addr:192.168.0.2  P-t-P:192.168.0.101  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1396  Metric:1
          RX packets:2005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:131227 (131.2 KB)  TX bytes:120 (120.0 B)

venet0    Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:127.0.0.2  P-t-P:127.0.0.2  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1
          RX packets:217729 errors:0 dropped:0 overruns:0 frame:0
          TX packets:216833 errors:0 dropped:3145 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:15090022 (15.0 MB)  TX bytes:13313493 (13.3 MB)

venet0:0  Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00
          inet addr:172.245.x.x  P-t-P:172.245.x.x  Bcast:0.0.0.0  Mask:255.255.255.255
          UP BROADCAST POINTOPOINT RUNNING NOARP  MTU:1500  Metric:1


I have put the x.x as the last 2 octets of the IP, just to i'm not pasting server public IP's all over the forum.

Anyone have any ideas as to why i cannot get a default gateway, and why the clients are unable to access the internet?
Thanks

---

### Post by TheFu on 2014-01-29
I don't know anything about pptp - it has been hacked enough times that it is not considered secure - by anyone. It is good enough to keep non-tech people from seeing the data, but anyone who can google and capture packages .... 

However, you cannot have the same local and remote subnets.  If the remote pptp subnet is 192.168.0.x/24, then your internal LAN must be something outside that range, period. This is a very basic networking thing.  To learn the basics of IPv4 networking, read/listen to grc.com/sn episodes 25-35.

---

### Post by wowlol on 2014-01-29
Thanks for the reply, 
I am not using PPTP as a security measure, to obscure data. I don't care if the data has to be sent unencrypted. I am using this VPN, so that i may take advantage of the DDoS protection and firewall on a VPS, to protect another windows cloud server. This windows box will be hosting game servers, so i harly consider encryption paramount here. And on the instructions i followed, it said to use this:
localip 192.168.0.1
remoteip 192.168.0.100-200
And this server, nor the server that is wanting to dial into it, are in a nat environment - It's a direct WAN port to WAN port. I connect to this VPN
using the internet IP of the ubuntu box from a windows box hosted elsewhere.
Are you saying i should set the local IP to 192.168.1.x and the remote IP to 192.168.0.x? Or should i possibly
use the local IP as the external IP of the VPS that's acting as the VPN server? 

Forgive me if i have completly misundersood what you were trying to say.

---

