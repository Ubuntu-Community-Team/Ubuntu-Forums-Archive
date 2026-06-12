---
title: "OpenVPN - Can't ping/access servers on local network from client."
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by Einewton on 2008-10-27
Hello,

The problem is that I cannot ping or connect to any of the servers that are on the same network as the OpenVPN server, except for the OpenVPN server itself. I am able to ping from the OpenVPN server to the client.
From the OpenVPN server, i'm able to ping any of the servers on the farm.

I've setup OpenVPN 2.1 on a clean install of Ubuntu 8.04 Hardy Server. OpenVPN authenticates to the LDAP directory. I'm able to successfully connect with XP and Vista (32bit & 64bit) PC's from home. The server is behind an ASA 5505, I've opened up port 1194 UDP on the firewall.

As you can see in the config, I push the route to another network range that exists on the network, and also does not work.

push "route 10.10.0.0 255.255.255.0"

If I do a tcpdump on my tap device (tcpdump -i tap0) I see the traffic trying to get through while I do a ping to 10.10.1.10...

10.10.1.100 --> Is the client IP that I'm doing the ping from.

listening on tap0, link-type EN10MB (Ethernet), capture size 96 bytes
16:18:52.972621 IP mainframe.lan.ssh > 10.10.1.100.53553: P 716457696:716457940(244) ack 1300730626 win 71
16:18:53.052740 IP 10.10.1.100.53553 > mainframe.lan.ssh: . ack 244 win 4290
16:18:57.243597 arp who-has 10.10.1.10 tell 10.10.1.100
16:18:58.073491 arp who-has 10.10.1.10 tell 10.10.1.100
16:18:59.072043 arp who-has 10.10.1.10 tell 10.10.1.100

Attached Below is a code snippet of the server config. If anyone could help me figure this problem out, it would be greatly appreciated!

```
local 10.10.1.13
port 1194
# TCP or UDP server?
proto udp
#This is key to configuring our bridge
dev tap0
#direct these to your generated files
ca /etc/openvpn/examples/easy-rsa/keys/ca.crt
cert /etc/openvpn/examples/easy-rsa/keys/server.crt
key /etc/openvpn/examples/easy-rsa/keys/server.key
dh /etc/openvpn/examples/easy-rsa/keys/dh1024.pem
ifconfig-pool-persist ipp.txt
#ensure the range of ip addresses you use in the last  two arguments
# of this statement are not in use by  either the DHCP server or any other
# device on your  internal network.
server-bridge 10.10.1.13 255.255.255.0 10.10.1.100 10.10.1.200
#needed to allow communication to internal network
client-to-client
keepalive 10 120
#encryption - very important ;)
#AES encryption is backed by many security firms
#however if you are concerned about speed use blowfish: "BF-CB"
cipher AES-128-CBC
#if you have another subnet you need to provide the route
push "route 10.10.0.0 255.255.255.0"
#server id protection
tls-auth ta.key 0
#compression for network speed
comp-lzo
# if packets are too large fragment them (only really useful if you have an old router)
#fragment 1400
#limit the number of connections
max-clients 100
#some secuurity settings
user nobody
group nogroup
persist-key
persist-tun
#log file settings
status openvpn-status.log
verb 3
# authentication plugin
#forces client to have a LDAP account to auth.
plugin /usr/lib/openvpn/openvpn-auth-pam.so login
```

---

### Post by mperry on 2008-10-27
I've had to set a few simple networking changes to make other systems on the same subnet as my openvpn server reachable from my ubuntu or xp client. Here the things I did to make it work:

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -A INPUT -i tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth1 -j MASQUERADE

The last rule will need changes based on your setup so don't cut and paste. You don't need to stop and restart the vpn server to make these changes either. When I do these things, my other systems become available for ssh, rdp, etc. I can also ping from my client ubuntu laptop to the other systems on the network besides my vpn server.

---

### Post by kevdog on 2008-10-27
Is this correct:  push "route 10.10.0.0 255.255.255.0"

should the netmask be 255.255.0.0?

---

### Post by Einewton on 2008-10-27
Wow, Thanks for your quick responces!

> **kevdog said:**
> Is this correct:  push "route 10.10.0.0 255.255.255.0"

should the netmask be 255.255.0.0?

Yes, Because i'm using 10.10.0.1,10.10.0.2,10.10.0.10,etc...

> **mperry said:**
> 
echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -A INPUT -i tun+ -j ACCEPT
iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth1 -j MASQUERADE
besides my vpn server.

In my sysctl.conf i've set net.ipv4.ip_forward=1

I've used these two statments that you've supplied:

iptables -t nat -A POSTROUTING -s 10.10.1.0/24 -o eth0 -j MASQUERADE
iptables -t nat -A POSTROUTING -s 10.10.0.0/24 -o eth1 -j MASQUERADE

Unfortunately I'm still seeing the same results, is there anything else that I might be able to try?

---

### Post by Einewton on 2008-10-27
Alright, I've been looking arround a bit, and got it working 1/2 of the way...

What i did was add:

iptables -A POSTROUTING --table nat -o ! tap0 -j MASQUERADE

And then added this setting to /etc/rc.local, so it would load on bootup, because this helped:

```
/sbin/iptables -A POSTROUTING --table nat -o ! tap0 -j MASQUERADE
```

Apparently, the traffic need's to find its way back to the client, and this made it happen for only the push route.

So, now I can see the whole network on 10.10.0.x, but I still can't communicate with the 10.10.1.x network from my client.

Is there some iptables command that I'm missing somewhere to enable the traffic to get back to the client for the 10.10.1.x network?

---

### Post by babyhuey23 on 2008-11-05
Any luck on this issue? im having the exact same problem

---

### Post by miq_ on 2008-11-13
> **Einewton said:**
> 
Is there some iptables command that I'm missing somewhere to enable the traffic to get back to the client for the 10.10.1.x network?

I was able to access the private network from the client after executing the following command in the VPV server.
```
iptables -I FORWARD 2 -i tap+ -j ACCEPT
```

---

### Post by Einewton on 2009-01-10
Thank you all for your suggestion, but they have failed to work so far. I've been limping along on one network for now.

If anyone has anything, please update this post, so that anyone else looking can easily fix this issue.

-Thanks!

---

### Post by swhi@yahoo.com on 2011-07-30
If you are setting up the server as a virtual machine, in a ESXi server there is a nasty little gotcha on the network card settings that needs to be changed.  The setting is in the VMWare ESX Management Client, then in Networking/Properties/Choose The VLAN your server is using/Edit/Security/Promiscous Mode/Check the box and choose Enable. Otherwise the bridge wont work because the ESX is preventing it from going into promiscous mode.

---

### Post by xrand on 2011-09-30
> **swhi@yahoo.com said:**
> If you are setting up the server as a virtual machine, in a ESXi server there is a nasty little gotcha on the network card settings that needs to be changed.  The setting is in the VMWare ESX Management Client, then in Networking/Properties/Choose The VLAN your server is using/Edit/Security/Promiscous Mode/Check the box and choose Enable. Otherwise the bridge wont work because the ESX is preventing it from going into promiscous mode.

THANK YOU VERY MUCH ;) i just spent two days figuring out whats wrong with my setup and id probably spend a few days more.

---

### Post by Colro on 2013-01-27
> **swhi@yahoo.com said:**
> If you are setting up the server as a virtual machine, in a ESXi server there is a nasty little gotcha on the network card settings that needs to be changed.  The setting is in the VMWare ESX Management Client, then in Networking/Properties/Choose The VLAN your server is using/Edit/Security/Promiscous Mode/Check the box and choose Enable. Otherwise the bridge wont work because the ESX is preventing it from going into promiscous mode.

UGH. I seriously hate to bump such an old thread, but I echo the HUGE THANK YOU for this. It was bugging me for HOURS. The second I enabled that everything magically came to life. You've saved me from going in to work looking like an idiot Monday. I know you'll never read this, but if you do, put up a Paypal donation link and I'll buy you a beer. Seriously. ARGH. Stupid VMware!

---

### Post by wildmanne39 on 2013-01-27
Old thread closed.

---

