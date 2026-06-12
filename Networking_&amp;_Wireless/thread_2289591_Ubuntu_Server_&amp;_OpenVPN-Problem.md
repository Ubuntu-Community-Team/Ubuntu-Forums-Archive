---
title: "Ubuntu Server &amp; OpenVPN-Problem"
date: 2015-08-05
forum: Networking &amp; Wireless
---

### Post by mene2 on 2015-08-05
Hey there.

I'm working on this for days without any progress...

My Setup is like this:
* external VPN-Server (vpn1, 192.168.102.1, Ubuntu)
* Firewall (gw1, 192.168.100.1 / 192.168.102.2, pfSense)
* LAN 192.168.100.0/24

gw1 (LAN-Firewall) is connected as a client to vpn1, so am I as road-warrior.
I can perfectly work with all hosts in my LAN, but I cant send Packets >1500.

Unfortunately I need such packets to get the bloody SwyxIT-Client to work properly (can't do anything about this).

I tried udp / tcp connections and about everything that could be done /w mtu-settings.

> 
//When connected to my LAN
$ ping -s 1500 192.168.100.5
PING 192.168.100.5 (192.168.100.5) 1500(1528) bytes of data.
1508 bytes from 192.168.100.5: icmp_req=19 ttl=64 time=1.00 ms
1508 bytes from 192.168.100.5: icmp_req=20 ttl=64 time=1.05 ms
1508 bytes from 192.168.100.5: icmp_req=21 ttl=64 time=1.03 ms

//When connected via VPN
$ ping -s 1500 192.168.100.5
PING 192.168.100.5 (192.168.100.5) 1500(1528) bytes of data.
From 192.168.102.2 icmp_seq=1 Destination Host Unreachable
From 192.168.102.2 icmp_seq=2 Destination Host Unreachable
From 192.168.102.2 icmp_seq=3 Destination Host Unreachable


Server (vpn1):
> dev tun
port 1194
proto tcp-server
mode server
tls-server
topology subnet
ifconfig 192.168.102.1 255.255.255.0
ifconfig-pool 192.168.102.100 192.168.102.199 255.255.255.0
route-gateway 192.168.102.1
route 192.168.100.0 255.255.255.0
ca ca.crt
cert vpn1.crt
key vpn1.key
dh dh2048.pem
cipher AES-256-CBC
client-to-client
keepalive 10 120
comp-lzo
max-clients 100
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
client-config-dir ccd
ifconfig-pool-persist ipp.txt
verb 4
push "topology subnet"
push "route 192.168.100.0 255.255.255.0"
push "route-gateway 192.168.102.1"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
#tun-mtu-extra 32
#fragment 1500
#mssfix 1500
#push "redirect-gateway def1 bypass-dhcp"
tun-mtu 1400
#link-mtu 1400
#fragment 1400


> # cat ccd/gw1 
ifconfig-push 192.168.102.2 255.255.255.0
iroute 192.168.100.0 255.255.255.0


Thanks for your help.

cheers
mene

---

