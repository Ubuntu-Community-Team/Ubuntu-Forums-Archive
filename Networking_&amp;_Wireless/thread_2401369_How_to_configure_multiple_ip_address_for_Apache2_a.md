---
title: "How to configure multiple ip address for Apache2 and Nginx with RTMP service."
date: 2018-09-17
forum: Networking &amp; Wireless
---

### Post by bob512 on 2018-09-17
Hello,

Ubuntu 16.04 server with Apache port 80 on xxx.xxx.xxx.77, Nginx port 80 with RTMP port 1935 on xxx.xxx.xxx.76.

Five static ip address from isp provider, range xxx.xxx.xxx.75 - 79, .75 is for isp router.  ISP provider is Frontier FIOS Internet.

Set up ip address using the Ubuntu Network Configuration Manager GUI tool.  Netmask is 255.255.255.0. 

Using ethernet switch in front of isp router, routing xxx.xxx.xxx.75 only to isp router and xxx.xxx.xxx.76+ native ethernet cables direct to Ubuntu 16.04 server.

Ubuntu 16.04 server also has LAN 5G wifi connection with the isp wifi router for local lan dhcp address, this works ok.

Static ip address xxx.xxx.xxx.75 is assigned to isp router, auto forward port 80, 7070, and 1935 to Ubuntu 16.04 server.

Static ip address xxx.xxx.xxx.76 is assigned to built-in nic Ubuntu 16.04 server, added as Nginx WEB Listen xxx.xxx.xxx.76:80 server_name xxx.xxx.xxx.76 and Nginx RTMP Listen xxx.xxx.xxx.76:1935.

Static ip address xxx.xxx.xxx.77 is assigned to adapter #1 nic card Ubuntu 16.04 server, added as Apache2 WEB Listen xxx.xxx.xxx.77:80

Static ip address xxx.xxx.xxx.78 and 79 is assigned to adapter #2 nic card Ubuntu 16.04 server, not yet used on the server.

Client workstations on LAN (behind isp router) and clients workstations can view and see Apache2 xxx.xxx.xxx.77 and see Nginx xxx.xxx.xxx.76 web pages.

**Internet client** workstations on WAN can view and see Apache2 xxx.xxx.xxx.77 default page **but NOT see Nginx** xxx.xxx.xxx.76 default page?

There is no iptables firewall, I issued sudo iptables -F to flush ip tables.

What am I over looking for Nginx default web page not displaying to Internet clients?

Thank you for your assistance,
Bob

---

### Post by TheFu on 2018-09-17
Welcome to the forums.

If the provider is Comcast with a /29, I use a router with static forwards for the specific IPs to the specific WAN-facing services.  That way I don't have to expose a server directly to the interent.  Plus, I screw up the server firewall rules, the router is still providing protection.

In my setup, .145 is my first IP .149 is the last and .150 is the ISP router/gateway. Sounds like yours is the other way around.

To me, having a WAN router is a basic security consideration.  If I want directly connected servers, I'd use a VPS where a security failure doesn't risk anything on my LAN.

BTW, you can't have both apache and nginx listening on the same IP on the same port.  Only 1 listener is allowed.  That first sentence has to be wrong.

Anyway, putting multiple IPs on a 16.04 NIC isn't hard.  [https://ubuntuforums.org/showthread.php?t=2368932](https://ubuntuforums.org/showthread.php?t=2368932) explains - see 
darkod's #2 post.

---

### Post by bob512 on 2018-09-17
Thank you for reply TheFu.

Here is correction to first sentence.

[COLOR=#000000]Ubuntu 16.04 server with Apache port 80 on xxx.xxx.xxx.77, Nginx port 80 with RTMP port 1935 on xxx.xxx.xxx.76.[/COLOR]

[COLOR=#000000]Five static ip address from isp provider, range xxx.xxx.xxx.75 - 79, .75 is for isp router. ISP provider is Frontier FIOS Internet.[/COLOR]

[COLOR=#000000]Set up ip address using the Ubuntu Network Configuration Manager GUI tool. Netmask is 255.255.255.0. 

I have three nic cards, the first is built-in nic having .76, the next is adapter #1 nic card assigned .77, not using the next adapter #2 nic card.

I may try manual edit the network setting file.

Bob.

[/COLOR]

---

### Post by bob512 on 2018-09-17
Manual entries ip address in /etc/network/interfaces 
Causes the reverse to occur Apache2 is NOT view able to internet users while Nginx is view able to internet viewers.
Although, Apache2 has listen and server name defined as xxx.xxx.xxx.77 and Nginx has listen and server name defined as xxx.xxx.xxx.76
If using Ubuntu Network Manager GUI tool, the Internet viewers can see .77 (Apache2) and not .76 (Nginx)
If using manual /etc/network/interfaces file, the Internet viewers cannot see .77 (Apache2) and see .76 (Nginx)

[COLOR=#000000]# The primary built-in nic network interface
[/COLOR]auto enp3s0
[COLOR=#000000]iface enp3s0 inet static[/COLOR]
[COLOR=#000000]address xxx.xxx.xxx.76/24[/COLOR]
[COLOR=#000000]netmask 255.255.255.0[/COLOR]
[COLOR=#000000]gateway xxx.xxx.xxx.1[/COLOR]
[COLOR=#000000]dns-nameservers 8.8.8.8

[/COLOR][COLOR=#000000]# The next adapter #1 network interface
[/COLOR]auto enp6s0
[COLOR=#000000]iface enp6s0 inet static[/COLOR]
[COLOR=#000000]address xxx.xxx.xxx.77/24[/COLOR]
[COLOR=#000000]netmask 255.255.255.0[/COLOR]
[COLOR=#000000]gateway xxx.xxx.xxx.1[/COLOR]
[COLOR=#000000]dns-nameservers 8.8.8.8

Appreciate any assistance, thank you.

Bob[/COLOR]

---

### Post by TheFu on 2018-09-17
Ubuntu Network Configuration Manager - never touch that. Sorry.

You can't just take an entire /24 on the public internet.  Not cool.  Not cool at all.  

```
 address xxx.xxx.xxx.76/24
```
says you own  xxx.xxx.xxx.1 -  xxx.xxx.xxx.255. You do not. You have a /29 and for some reason have decided to use different NICs.  Use 1 NIC for the public IP and just assign all the public IPs to it and use the other NICs for management, LAN and/or storage networks.

Really, I'd put a router in between the server(s) and internet and do the exact IP and port forwarding to the internal system(s) as needed. For some reason, that isn't in your plans.

---

