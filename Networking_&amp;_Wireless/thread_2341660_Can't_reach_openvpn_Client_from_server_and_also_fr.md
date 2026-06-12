---
title: "Can't reach openvpn Client from server and also from other reachable clients"
date: 2016-10-30
forum: Networking &amp; Wireless
---

### Post by mldoscar on 2016-10-30
Hello Everyone!


I'm having troubles stablishing communitacion between a client to another clients through a configurated OpenVPN Server. After months of investigation I've done almost everything to try this to work. I need your help.

Here's the detailed thing:

- I have configurated an OpenVPN Server which is on a VPS I own.
- Every client can get access to the server using the config file [**I've 1 laptop (Ubuntu 16.04), 1 desktop pc (Windows 10), and 1 iPhone (iOS 9.3); both with differents config files**].

The thing is I want to access to any service from any client (a web server, ssh access, any service). I've tried to connect the desktop pc and the iphone to the vpn server, and I can get communication between them two (Ping requests and responses, Web services, anything).
The weird thing is when I connect my laptop (ubuntu) to the vpn server.** It does connect. I can reach the desktop pc and the iphone. BUT THEY CANNOT GET ACCESS TO UBUNTU LAPTOP!**
I've checked ufw, I defenitely disabled it. Then I cleaned up iptables, Ip forwarding from sysctl is enabled.
I've checked ufw, sysctl, iptables, ip_forwarding in the OpenVPN server as well and everything looks ok. (Because I can access between desktop pc and iphone. So, It might work for everything.) Also, i've connected an Android tablet and also is reacheable.
What I want to do is that I can reach my Ubuntu Laptop, thus my other devices can get access to it.
[COLOR=#ff0000]**NOTE: I've ran Wireshark on my Ubuntu Laptop, and I sent ping requests, webpage GET request, and EVERYTHING GOES IN, but it can't send any response. It's like the laptop can't get the way to communicate back to the other devices which are requesting.**[/COLOR]

Here's the scenario:
OpenVPN Server
(Ubuntu 14.04 LTS)    PUBLIC IP: x.x.x.x
OpenVPN network: 10.8.0.0/24
DESKTOP-PC
(Windows)    LAN IP: 192.168.2.2
OpenVPN assigned IP: 10.8.0.2
LAPTOP
(Ubuntu 16.04)    LAN IP: 192.168.2.3
OpenVPN assigned IP: 10.8.0.3
IPHONE
(iOS 9.3)    LAN IP: 192.168.2.4
OpenVPN assigned IP: 10.8.0.4


REQUESTS AND RESPONSE RESULTS:
DESKTOP-PC ----> IPHONE (REACHABLE)
IPHONE -----> DESKTOP-PC (REACHABLE)
LAPTOP -----> DESKTOP-PC (REACHABLE)
LAPTOP -----> IPHONE (REACHABLE)
DESKTOP-PC ----> LAPTOP (UNREACHABLE, laptop gets the request, but it cant send the response)
IPHONE -------> LAPTOP (UNREACHABLE, laptop gets the request, but it cant send the response)
DESKTOP-PC ----> SERVER (REACHABLE)
IPHONE ----> SERVER (REACHABLE)
LAPTOP ----> SERVER (REACHABLE)
SERVER ------> DESKTOP-PC (REACHABLE)
SERVER ------> IPHONE (REACHABLE)
SERVER ------> LAPTOP (UNREACHABLE, laptop gets the request, but it cant send the response)

[B]OpenVPN server config
/etc/openvpn/server.conf[/B]
```

port 1194
proto udp
dev tun
sndbuf 0
rcvbuf 0
ca ca.crt
cert server.crt
key server.key
dh dh.pem
tls-auth ta.key 0
topology subnet
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 208.67.222.222"
push "dhcp-option DNS 208.67.220.220"
keepalive 10 120
cipher AES-128-CBC
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
crl-verify crl.pem

```

[B]
ifconfig (OpenVPN server)[/B]
```

eth0      Link encap:Ethernet  HWaddr 04:01:21:a4:47:01  
          inet addr:192.34.X.X  Bcast:192.34.X.X  Mask:255.255.255.0
          inet6 addr: XXXXXXXXXXXXXXXXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:146527 errors:0 dropped:0 overruns:0 frame:0
          TX packets:142028 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:135270618 (135.2 MB)  TX bytes:132743894 (132.7 MB)


eth1      Link encap:Ethernet  HWaddr 04:01:21:a4:47:02  
          inet6 addr: XXXXXXXXXXXXXXXXXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:242716 (242.7 KB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.1  P-t-P:10.8.0.1  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:44516 errors:0 dropped:0 overruns:0 frame:0
          TX packets:89914 errors:0 dropped:272 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:5198268 (5.1 MB)  TX bytes:117094299 (117.0 MB)

```


**Route (OpenVPN Server)**
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         192.34.X.X     0.0.0.0         UG    0      0        0 eth0
10.8.0.0        *               255.255.255.0   U     0      0        0 tun0
10.10.0.0       *               255.255.0.0     U     0      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
192.34.X.X     *               255.255.255.0   U     0      0        0 eth0

```


**iptables -S (OpenVPN Server)**
```

-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT
-N ufw-after-forward
-N ufw-after-input
-N ufw-after-logging-forward
-N ufw-after-logging-input
-N ufw-after-logging-output
-N ufw-after-output
-N ufw-before-forward
-N ufw-before-input
-N ufw-before-logging-forward
-N ufw-before-logging-input
-N ufw-before-logging-output
-N ufw-before-output
-N ufw-logging-allow
-N ufw-logging-deny
-N ufw-not-local
-N ufw-reject-forward
-N ufw-reject-input
-N ufw-reject-output
-N ufw-skip-to-policy-forward
-N ufw-skip-to-policy-input
-N ufw-skip-to-policy-output
-N ufw-track-forward
-N ufw-track-input
-N ufw-track-output
-N ufw-user-forward
-N ufw-user-input
-N ufw-user-limit
-N ufw-user-limit-accept
-N ufw-user-logging-forward
-N ufw-user-logging-input
-N ufw-user-logging-output
-N ufw-user-output
-A INPUT -j ufw-before-logging-input
-A INPUT -j ufw-before-input
-A INPUT -j ufw-after-input
-A INPUT -j ufw-after-logging-input
-A INPUT -j ufw-reject-input
-A INPUT -j ufw-track-input
-A FORWARD -j ufw-before-logging-forward
-A FORWARD -j ufw-before-forward
-A FORWARD -j ufw-after-forward
-A FORWARD -j ufw-after-logging-forward
-A FORWARD -j ufw-reject-forward
-A FORWARD -j ufw-track-forward
-A OUTPUT -j ufw-before-logging-output
-A OUTPUT -j ufw-before-output
-A OUTPUT -j ufw-after-output
-A OUTPUT -j ufw-after-logging-output
-A OUTPUT -j ufw-reject-output
-A OUTPUT -j ufw-track-output
-A ufw-after-input -p udp -m udp --dport 137 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 138 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp -m tcp --dport 139 -j ufw-skip-to-policy-input
-A ufw-after-input -p tcp -m tcp --dport 445 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 67 -j ufw-skip-to-policy-input
-A ufw-after-input -p udp -m udp --dport 68 -j ufw-skip-to-policy-input
-A ufw-after-input -m addrtype --dst-type BROADCAST -j ufw-skip-to-policy-input
-A ufw-before-forward -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 4 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 12 -j ACCEPT
-A ufw-before-forward -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A ufw-before-forward -j ufw-user-forward
-A ufw-before-input -i lo -j ACCEPT
-A ufw-before-input -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-input -m conntrack --ctstate INVALID -j ufw-logging-deny
-A ufw-before-input -m conntrack --ctstate INVALID -j DROP
-A ufw-before-input -p icmp -m icmp --icmp-type 3 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 4 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 11 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 12 -j ACCEPT
-A ufw-before-input -p icmp -m icmp --icmp-type 8 -j ACCEPT
-A ufw-before-input -p udp -m udp --sport 67 --dport 68 -j ACCEPT
-A ufw-before-input -j ufw-not-local
-A ufw-before-input -d 224.0.0.251/32 -p udp -m udp --dport 5353 -j ACCEPT
-A ufw-before-input -d 239.255.255.250/32 -p udp -m udp --dport 1900 -j ACCEPT
-A ufw-before-input -j ufw-user-input
-A ufw-before-output -o lo -j ACCEPT
-A ufw-before-output -m conntrack --ctstate RELATED,ESTABLISHED -j ACCEPT
-A ufw-before-output -j ufw-user-output
-A ufw-logging-allow -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW ALLOW] "
-A ufw-logging-deny -m conntrack --ctstate INVALID -m limit --limit 3/min --limit-burst 10 -j RETURN
-A ufw-logging-deny -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK] "
-A ufw-not-local -m addrtype --dst-type LOCAL -j RETURN
-A ufw-not-local -m addrtype --dst-type MULTICAST -j RETURN
-A ufw-not-local -m addrtype --dst-type BROADCAST -j RETURN
-A ufw-not-local -m limit --limit 3/min --limit-burst 10 -j ufw-logging-deny
-A ufw-not-local -j DROP
-A ufw-skip-to-policy-forward -j ACCEPT
-A ufw-skip-to-policy-input -j ACCEPT
-A ufw-skip-to-policy-output -j ACCEPT
-A ufw-track-forward -p tcp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-forward -p udp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-input -p tcp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-input -p udp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-output -p tcp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-track-output -p udp -m conntrack --ctstate NEW -j ACCEPT
-A ufw-user-input -p tcp -m tcp --dport 22 -j ACCEPT
-A ufw-user-input -p udp -m udp --dport 22 -j ACCEPT
-A ufw-user-input -p tcp -m tcp --dport 1194 -j ACCEPT
-A ufw-user-input -p udp -m udp --dport 1194 -j ACCEPT
-A ufw-user-input -p tcp -m tcp --dport 80 -j ACCEPT
-A ufw-user-input -p udp -m udp --dport 80 -j ACCEPT
-A ufw-user-input -p tcp -m tcp --dport 3389 -j ACCEPT
-A ufw-user-input -p udp -m udp --dport 3389 -j ACCEPT
-A ufw-user-limit -m limit --limit 3/min -j LOG --log-prefix "[UFW LIMIT BLOCK] "
-A ufw-user-limit -j REJECT --reject-with icmp-port-unreachable
-A ufw-user-limit-accept -j ACCEPT

```




[B]LAPTOP (OpenVPN Client)
~/laptop-client-config.conf[/B]
```

client
dev tun
proto udp
sndbuf 0
rcvbuf 0
remote 192.34.X.X 1194
resolv-retry infinite
nobind
persist-key
persist-tun
remote-cert-tls server
cipher AES-128-CBC
comp-lzo
setenv opt block-outside-dns
key-direction 1
verb 3
<ca>
-----BEGIN CERTIFICATE-----
BLA BLA BLA
-----END CERTIFICATE-----
</ca>
<cert>
Certificate:
BLA BLA BLA
-----BEGIN CERTIFICATE-----
BLA BLA BLA
-----END CERTIFICATE-----
</cert>
<key>
-----BEGIN PRIVATE KEY-----
BLA BLA BLA
-----END PRIVATE KEY-----
</key>
<tls-auth>
#
# 2048 bit OpenVPN static key
#
-----BEGIN OpenVPN Static key V1-----
BLA BLA BLA
-----END OpenVPN Static key V1-----
</tls-auth>

```


[B]LAPTOP (OpenVPN Client)
ifconfig[/B]
```

enp1s0    Link encap:Ethernet  HWaddr 00:8c:fa:30:d3:bd  
          inet addr:192.168.2.3  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::ab33:7878:9d2:2df/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:1135 errors:0 dropped:0 overruns:0 frame:0
          TX packets:755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114173 (114.1 KB)  TX bytes:112740 (112.7 KB)
          Interrupt:16 


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:10.8.0.3  P-t-P:10.8.0.3  Mask:255.255.255.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:29 errors:0 dropped:0 overruns:0 frame:0
          TX packets:50 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:2781 (2.7 KB)  TX bytes:4078 (4.0 KB)

```

[B]LAPTOP (OpenVPN Client)
route[/B]
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         10.8.0.1        128.0.0.0       UG    0      0        0 tun0
default         192.168.2.254   0.0.0.0         UG    100    0        0 enp1s0
10.8.0.0        *               255.255.255.0   U     0      0        0 tun0
128.0.0.0       10.8.0.1        128.0.0.0       UG    0      0        0 tun0
link-local      *               255.255.0.0     U     1000   0        0 enp1s0
nicacode-vpn.tk 192.168.2.254   255.255.255.255 UGH   0      0        0 enp1s0
192.168.2.0     *               255.255.255.0   U     100    0        0 enp1s0

```


[B]LAPTOP (OpenVPN Client)
iptables -S[/B]
```

-P INPUT ACCEPT
-P FORWARD ACCEPT
-P OUTPUT ACCEPT

```

[B]LAPTOP (OpenVPN Client)
sysctl -a[/B]
```

net.ipv4.conf.all.accept_local = 0
net.ipv4.conf.all.accept_redirects = 1
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.conf.all.arp_accept = 0
net.ipv4.conf.all.arp_announce = 0
net.ipv4.conf.all.arp_filter = 0
net.ipv4.conf.all.arp_ignore = 0
net.ipv4.conf.all.arp_notify = 0
net.ipv4.conf.all.bootp_relay = 0
net.ipv4.conf.all.disable_policy = 0
net.ipv4.conf.all.disable_xfrm = 0
net.ipv4.conf.all.force_igmp_version = 0
net.ipv4.conf.all.forwarding = 0
net.ipv4.conf.all.igmpv2_unsolicited_report_interval = 10000
net.ipv4.conf.all.igmpv3_unsolicited_report_interval = 1000
net.ipv4.conf.all.ignore_routes_with_linkdown = 0
net.ipv4.conf.all.log_martians = 0
net.ipv4.conf.all.mc_forwarding = 0
net.ipv4.conf.all.medium_id = 0
net.ipv4.conf.all.promote_secondaries = 0
net.ipv4.conf.all.proxy_arp = 0
net.ipv4.conf.all.proxy_arp_pvlan = 0
net.ipv4.conf.all.route_localnet = 0
net.ipv4.conf.all.rp_filter = 1
net.ipv4.conf.all.secure_redirects = 1
net.ipv4.conf.all.send_redirects = 1
net.ipv4.conf.all.shared_media = 1
net.ipv4.conf.all.src_valid_mark = 0
net.ipv4.conf.all.tag = 0
net.ipv4.conf.default.accept_local = 0
net.ipv4.conf.default.accept_redirects = 1
net.ipv4.conf.default.accept_source_route = 1
net.ipv4.conf.default.arp_accept = 0
net.ipv4.conf.default.arp_announce = 0
net.ipv4.conf.default.arp_filter = 0
net.ipv4.conf.default.arp_ignore = 0
net.ipv4.conf.default.arp_notify = 0
net.ipv4.conf.default.bootp_relay = 0
net.ipv4.conf.default.disable_policy = 0
net.ipv4.conf.default.disable_xfrm = 0
net.ipv4.conf.default.force_igmp_version = 0
net.ipv4.conf.default.forwarding = 0
net.ipv4.conf.default.igmpv2_unsolicited_report_interval = 10000
net.ipv4.conf.default.igmpv3_unsolicited_report_interval = 1000
net.ipv4.conf.default.ignore_routes_with_linkdown = 0
net.ipv4.conf.default.log_martians = 0
net.ipv4.conf.default.mc_forwarding = 0
net.ipv4.conf.default.medium_id = 0
net.ipv4.conf.default.promote_secondaries = 0
net.ipv4.conf.default.proxy_arp = 0
net.ipv4.conf.default.proxy_arp_pvlan = 0
net.ipv4.conf.default.route_localnet = 0
net.ipv4.conf.default.rp_filter = 1
net.ipv4.conf.default.secure_redirects = 1
net.ipv4.conf.default.send_redirects = 1
net.ipv4.conf.default.shared_media = 1
net.ipv4.conf.default.src_valid_mark = 0
net.ipv4.conf.default.tag = 0
net.ipv4.conf.enp1s0.accept_local = 0
net.ipv4.conf.enp1s0.accept_redirects = 1
net.ipv4.conf.enp1s0.accept_source_route = 1
net.ipv4.conf.enp1s0.arp_accept = 0
net.ipv4.conf.enp1s0.arp_announce = 0
net.ipv4.conf.enp1s0.arp_filter = 0
net.ipv4.conf.enp1s0.arp_ignore = 0
net.ipv4.conf.enp1s0.arp_notify = 0
net.ipv4.conf.enp1s0.bootp_relay = 0
net.ipv4.conf.enp1s0.disable_policy = 0
net.ipv4.conf.enp1s0.disable_xfrm = 0
net.ipv4.conf.enp1s0.force_igmp_version = 0
net.ipv4.conf.enp1s0.forwarding = 0
net.ipv4.conf.enp1s0.igmpv2_unsolicited_report_interval = 10000
net.ipv4.conf.enp1s0.igmpv3_unsolicited_report_interval = 1000
net.ipv4.conf.enp1s0.ignore_routes_with_linkdown = 0
net.ipv4.conf.enp1s0.log_martians = 0
net.ipv4.conf.enp1s0.mc_forwarding = 0
net.ipv4.conf.enp1s0.medium_id = 0
net.ipv4.conf.enp1s0.promote_secondaries = 0
net.ipv4.conf.enp1s0.proxy_arp = 0
net.ipv4.conf.enp1s0.proxy_arp_pvlan = 0
net.ipv4.conf.enp1s0.route_localnet = 0
net.ipv4.conf.enp1s0.rp_filter = 1
net.ipv4.conf.enp1s0.secure_redirects = 1
net.ipv4.conf.enp1s0.send_redirects = 1
net.ipv4.conf.enp1s0.shared_media = 1
net.ipv4.conf.enp1s0.src_valid_mark = 0
net.ipv4.conf.enp1s0.tag = 0
net.ipv4.conf.lo.accept_local = 0
net.ipv4.conf.lo.accept_redirects = 1
net.ipv4.conf.lo.accept_source_route = 1
net.ipv4.conf.lo.arp_accept = 0
net.ipv4.conf.lo.arp_announce = 0
net.ipv4.conf.lo.arp_filter = 0
net.ipv4.conf.lo.arp_ignore = 0
net.ipv4.conf.lo.arp_notify = 0
net.ipv4.conf.lo.bootp_relay = 0
net.ipv4.conf.lo.disable_policy = 1
net.ipv4.conf.lo.disable_xfrm = 1
net.ipv4.conf.lo.force_igmp_version = 0
net.ipv4.conf.lo.forwarding = 0
net.ipv4.conf.lo.igmpv2_unsolicited_report_interval = 10000
net.ipv4.conf.lo.igmpv3_unsolicited_report_interval = 1000
net.ipv4.conf.lo.ignore_routes_with_linkdown = 0
net.ipv4.conf.lo.log_martians = 0
net.ipv4.conf.lo.mc_forwarding = 0
net.ipv4.conf.lo.medium_id = 0
net.ipv4.conf.lo.promote_secondaries = 0
net.ipv4.conf.lo.proxy_arp = 0
net.ipv4.conf.lo.proxy_arp_pvlan = 0
net.ipv4.conf.lo.route_localnet = 0
net.ipv4.conf.lo.rp_filter = 0
net.ipv4.conf.lo.secure_redirects = 1
net.ipv4.conf.lo.send_redirects = 1
net.ipv4.conf.lo.shared_media = 1
net.ipv4.conf.lo.src_valid_mark = 0
net.ipv4.conf.lo.tag = 0
net.ipv4.conf.tun0.accept_local = 0
net.ipv4.conf.tun0.accept_redirects = 1
net.ipv4.conf.tun0.accept_source_route = 1
net.ipv4.conf.tun0.arp_accept = 0
net.ipv4.conf.tun0.arp_announce = 0
net.ipv4.conf.tun0.arp_filter = 0
net.ipv4.conf.tun0.arp_ignore = 0
net.ipv4.conf.tun0.arp_notify = 0
net.ipv4.conf.tun0.bootp_relay = 0
net.ipv4.conf.tun0.disable_policy = 0
net.ipv4.conf.tun0.disable_xfrm = 0
net.ipv4.conf.tun0.force_igmp_version = 0
net.ipv4.conf.tun0.forwarding = 0
net.ipv4.conf.tun0.igmpv2_unsolicited_report_interval = 10000
net.ipv4.conf.tun0.igmpv3_unsolicited_report_interval = 1000
net.ipv4.conf.tun0.ignore_routes_with_linkdown = 0
net.ipv4.conf.tun0.log_martians = 0
net.ipv4.conf.tun0.mc_forwarding = 0
net.ipv4.conf.tun0.medium_id = 0
net.ipv4.conf.tun0.promote_secondaries = 0
net.ipv4.conf.tun0.proxy_arp = 0
net.ipv4.conf.tun0.proxy_arp_pvlan = 0
net.ipv4.conf.tun0.route_localnet = 0
net.ipv4.conf.tun0.rp_filter = 1
net.ipv4.conf.tun0.secure_redirects = 1
net.ipv4.conf.tun0.send_redirects = 1
net.ipv4.conf.tun0.shared_media = 1
net.ipv4.conf.tun0.src_valid_mark = 0
net.ipv4.conf.tun0.tag = 0
net.ipv4.conf.wlp2s0.accept_local = 0
net.ipv4.conf.wlp2s0.accept_redirects = 1
net.ipv4.conf.wlp2s0.accept_source_route = 1
net.ipv4.conf.wlp2s0.arp_accept = 0
net.ipv4.conf.wlp2s0.arp_announce = 0
net.ipv4.conf.wlp2s0.arp_filter = 0
net.ipv4.conf.wlp2s0.arp_ignore = 0
net.ipv4.conf.wlp2s0.arp_notify = 0
net.ipv4.conf.wlp2s0.bootp_relay = 0
net.ipv4.conf.wlp2s0.disable_policy = 0
net.ipv4.conf.wlp2s0.disable_xfrm = 0
net.ipv4.conf.wlp2s0.force_igmp_version = 0
net.ipv4.conf.wlp2s0.forwarding = 0
net.ipv4.conf.wlp2s0.igmpv2_unsolicited_report_interval = 10000
net.ipv4.conf.wlp2s0.igmpv3_unsolicited_report_interval = 1000
net.ipv4.conf.wlp2s0.ignore_routes_with_linkdown = 0
net.ipv4.conf.wlp2s0.log_martians = 0
net.ipv4.conf.wlp2s0.mc_forwarding = 0
net.ipv4.conf.wlp2s0.medium_id = 0
net.ipv4.conf.wlp2s0.promote_secondaries = 0
net.ipv4.conf.wlp2s0.proxy_arp = 0
net.ipv4.conf.wlp2s0.proxy_arp_pvlan = 0
net.ipv4.conf.wlp2s0.route_localnet = 0
net.ipv4.conf.wlp2s0.rp_filter = 1
net.ipv4.conf.wlp2s0.secure_redirects = 1
net.ipv4.conf.wlp2s0.send_redirects = 1
net.ipv4.conf.wlp2s0.shared_media = 1
net.ipv4.conf.wlp2s0.src_valid_mark = 0
net.ipv4.conf.wlp2s0.tag = 0
net.ipv4.fwmark_reflect = 0
net.ipv4.icmp_echo_ignore_all = 0
net.ipv4.icmp_echo_ignore_broadcasts = 1
net.ipv4.icmp_errors_use_inbound_ifaddr = 0
net.ipv4.icmp_ignore_bogus_error_responses = 1
net.ipv4.icmp_msgs_burst = 50
net.ipv4.icmp_msgs_per_sec = 1000
net.ipv4.icmp_ratelimit = 1000
net.ipv4.icmp_ratemask = 6168
net.ipv4.igmp_link_local_mcast_reports = 1
net.ipv4.igmp_max_memberships = 20
net.ipv4.igmp_max_msf = 10
net.ipv4.igmp_qrv = 2
net.ipv4.inet_peer_maxttl = 600
net.ipv4.inet_peer_minttl = 120
net.ipv4.inet_peer_threshold = 65664
net.ipv4.ip_default_ttl = 64
net.ipv4.ip_dynaddr = 0
net.ipv4.ip_early_demux = 1
net.ipv4.ip_forward = 0
net.ipv4.ip_forward_use_pmtu = 0
net.ipv4.ip_local_port_range = 32768    60999
net.ipv4.ip_local_reserved_ports = 
net.ipv4.ip_no_pmtu_disc = 0
net.ipv4.ip_nonlocal_bind = 0
net.ipv4.ipfrag_high_thresh = 4194304
net.ipv4.ipfrag_low_thresh = 3145728
net.ipv4.ipfrag_max_dist = 64
net.ipv4.ipfrag_secret_interval = 0
net.ipv4.ipfrag_time = 30
net.ipv4.neigh.default.anycast_delay = 100
net.ipv4.neigh.default.app_solicit = 0
net.ipv4.neigh.default.base_reachable_time_ms = 30000
net.ipv4.neigh.default.delay_first_probe_time = 5
net.ipv4.neigh.default.gc_interval = 30
net.ipv4.neigh.default.gc_stale_time = 60
net.ipv4.neigh.default.gc_thresh1 = 128
net.ipv4.neigh.default.gc_thresh2 = 512
net.ipv4.neigh.default.gc_thresh3 = 1024
net.ipv4.neigh.default.locktime = 100
net.ipv4.neigh.default.mcast_resolicit = 0
net.ipv4.neigh.default.mcast_solicit = 3
net.ipv4.neigh.default.proxy_delay = 80
net.ipv4.neigh.default.proxy_qlen = 64
net.ipv4.neigh.default.retrans_time_ms = 1000
net.ipv4.neigh.default.ucast_solicit = 3
net.ipv4.neigh.default.unres_qlen = 31
net.ipv4.neigh.default.unres_qlen_bytes = 65536
net.ipv4.neigh.enp1s0.anycast_delay = 100
net.ipv4.neigh.enp1s0.app_solicit = 0
net.ipv4.neigh.enp1s0.base_reachable_time_ms = 30000
net.ipv4.neigh.enp1s0.delay_first_probe_time = 5
net.ipv4.neigh.enp1s0.gc_stale_time = 60
net.ipv4.neigh.enp1s0.locktime = 100
net.ipv4.neigh.enp1s0.mcast_resolicit = 0
net.ipv4.neigh.enp1s0.mcast_solicit = 3
net.ipv4.neigh.enp1s0.proxy_delay = 80
net.ipv4.neigh.enp1s0.proxy_qlen = 64
net.ipv4.neigh.enp1s0.retrans_time_ms = 1000
net.ipv4.neigh.enp1s0.ucast_solicit = 3
net.ipv4.neigh.enp1s0.unres_qlen = 31
net.ipv4.neigh.enp1s0.unres_qlen_bytes = 65536
net.ipv4.neigh.lo.anycast_delay = 100
net.ipv4.neigh.lo.app_solicit = 0
net.ipv4.neigh.lo.base_reachable_time_ms = 30000
net.ipv4.neigh.lo.delay_first_probe_time = 5
net.ipv4.neigh.lo.gc_stale_time = 60
net.ipv4.neigh.lo.locktime = 100
net.ipv4.neigh.lo.mcast_resolicit = 0
net.ipv4.neigh.lo.mcast_solicit = 3
net.ipv4.neigh.lo.proxy_delay = 80
net.ipv4.neigh.lo.proxy_qlen = 64
net.ipv4.neigh.lo.retrans_time_ms = 1000
net.ipv4.neigh.lo.ucast_solicit = 3
net.ipv4.neigh.lo.unres_qlen = 31
net.ipv4.neigh.lo.unres_qlen_bytes = 65536
net.ipv4.neigh.tun0.anycast_delay = 100
net.ipv4.neigh.tun0.app_solicit = 0
net.ipv4.neigh.tun0.base_reachable_time_ms = 30000
net.ipv4.neigh.tun0.delay_first_probe_time = 5
net.ipv4.neigh.tun0.gc_stale_time = 60
net.ipv4.neigh.tun0.locktime = 100
net.ipv4.neigh.tun0.mcast_resolicit = 0
net.ipv4.neigh.tun0.mcast_solicit = 3
net.ipv4.neigh.tun0.proxy_delay = 80
net.ipv4.neigh.tun0.proxy_qlen = 64
net.ipv4.neigh.tun0.retrans_time_ms = 1000
net.ipv4.neigh.tun0.ucast_solicit = 3
net.ipv4.neigh.tun0.unres_qlen = 31
net.ipv4.neigh.tun0.unres_qlen_bytes = 65536
net.ipv4.ping_group_range = 1    0
net.ipv4.route.error_burst = 1250
net.ipv4.route.error_cost = 250
net.ipv4.route.gc_elasticity = 8
net.ipv4.route.gc_interval = 60
net.ipv4.route.gc_min_interval = 0
net.ipv4.route.gc_min_interval_ms = 500
net.ipv4.route.gc_thresh = -1
net.ipv4.route.gc_timeout = 300
net.ipv4.route.max_size = 2147483647
net.ipv4.route.min_adv_mss = 256
net.ipv4.route.min_pmtu = 552
net.ipv4.route.mtu_expires = 600
net.ipv4.route.redirect_load = 5
net.ipv4.route.redirect_number = 9
net.ipv4.route.redirect_silence = 5120
net.ipv4.tcp_abort_on_overflow = 0
net.ipv4.tcp_adv_win_scale = 1
net.ipv4.tcp_allowed_congestion_control = cubic reno
net.ipv4.tcp_app_win = 31
net.ipv4.tcp_autocorking = 1
net.ipv4.tcp_available_congestion_control = cubic reno
net.ipv4.tcp_base_mss = 1024
net.ipv4.tcp_challenge_ack_limit = 1000
net.ipv4.tcp_congestion_control = cubic
net.ipv4.tcp_dsack = 1
net.ipv4.tcp_early_retrans = 3
net.ipv4.tcp_ecn = 2
net.ipv4.tcp_ecn_fallback = 1
net.ipv4.tcp_fack = 1
net.ipv4.tcp_fastopen = 1
net.ipv4.tcp_fastopen_key = 00000000-00000000-00000000-00000000
net.ipv4.tcp_fin_timeout = 60
net.ipv4.tcp_frto = 2
net.ipv4.tcp_fwmark_accept = 0
net.ipv4.tcp_invalid_ratelimit = 500
net.ipv4.tcp_keepalive_intvl = 75
net.ipv4.tcp_keepalive_probes = 9
net.ipv4.tcp_keepalive_time = 7200
net.ipv4.tcp_limit_output_bytes = 262144
net.ipv4.tcp_low_latency = 0
net.ipv4.tcp_max_orphans = 32768
net.ipv4.tcp_max_reordering = 300
net.ipv4.tcp_max_syn_backlog = 256
net.ipv4.tcp_max_tw_buckets = 32768
net.ipv4.tcp_mem = 51420    68563    102840
net.ipv4.tcp_min_rtt_wlen = 300
net.ipv4.tcp_min_tso_segs = 2
net.ipv4.tcp_moderate_rcvbuf = 1
net.ipv4.tcp_mtu_probing = 0
net.ipv4.tcp_no_metrics_save = 0
net.ipv4.tcp_notsent_lowat = -1
net.ipv4.tcp_orphan_retries = 0
net.ipv4.tcp_pacing_ca_ratio = 120
net.ipv4.tcp_pacing_ss_ratio = 200
net.ipv4.tcp_probe_interval = 600
net.ipv4.tcp_probe_threshold = 8
net.ipv4.tcp_recovery = 1
net.ipv4.tcp_reordering = 3
net.ipv4.tcp_retrans_collapse = 1
net.ipv4.tcp_retries1 = 3
net.ipv4.tcp_retries2 = 15
net.ipv4.tcp_rfc1337 = 0
net.ipv4.tcp_rmem = 4096    87380    6291456
net.ipv4.tcp_sack = 1
net.ipv4.tcp_slow_start_after_idle = 1
net.ipv4.tcp_stdurg = 0
net.ipv4.tcp_syn_retries = 6
net.ipv4.tcp_synack_retries = 5
net.ipv4.tcp_syncookies = 1
net.ipv4.tcp_thin_dupack = 0
net.ipv4.tcp_thin_linear_timeouts = 0
net.ipv4.tcp_timestamps = 1
net.ipv4.tcp_tso_win_divisor = 3
net.ipv4.tcp_tw_recycle = 0
net.ipv4.tcp_tw_reuse = 0
net.ipv4.tcp_window_scaling = 1
net.ipv4.tcp_wmem = 4096    16384    4194304
net.ipv4.tcp_workaround_signed_windows = 0
net.ipv4.udp_mem = 102843    137127    205686
net.ipv4.udp_rmem_min = 4096
net.ipv4.udp_wmem_min = 4096
net.ipv4.xfrm4_gc_thresh = 2147483647

```
[B]
LAPTOP (OpenVPN Client)
openvpn --config my-config-file.conf[/B]
```

Sun Oct 30 01:34:20 2016 Unrecognized option or missing parameter(s) in oscar-w10.ovpn:14: block-outside-dns (2.3.10)
Sun Oct 30 01:34:20 2016 OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Feb  2 2016
Sun Oct 30 01:34:20 2016 library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Sun Oct 30 01:34:20 2016 Control Channel Authentication: tls-auth using INLINE static key file
Sun Oct 30 01:34:20 2016 Outgoing Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Oct 30 01:34:20 2016 Incoming Control Channel Authentication: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Oct 30 01:34:20 2016 Socket Buffers: R=[212992->212992] S=[212992->212992]
Sun Oct 30 01:34:20 2016 UDPv4 link local: [undef]
Sun Oct 30 01:34:20 2016 UDPv4 link remote: [AF_INET]192.34.X.X:1194
Sun Oct 30 01:34:20 2016 TLS: Initial packet from [AF_INET]192.34.X.X:1194, sid=75e1a3f1 cb41c25d
Sun Oct 30 01:34:21 2016 VERIFY OK: depth=1, CN=ChangeMe
Sun Oct 30 01:34:21 2016 Validating certificate key usage
Sun Oct 30 01:34:21 2016 ++ Certificate has key usage  00a0, expects 00a0
Sun Oct 30 01:34:21 2016 VERIFY KU OK
Sun Oct 30 01:34:21 2016 Validating certificate extended key usage
Sun Oct 30 01:34:21 2016 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Sun Oct 30 01:34:21 2016 VERIFY EKU OK
Sun Oct 30 01:34:21 2016 VERIFY OK: depth=0, CN=server
Sun Oct 30 01:34:22 2016 Data Channel Encrypt: Cipher 'AES-128-CBC' initialized with 128 bit key
Sun Oct 30 01:34:22 2016 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Oct 30 01:34:22 2016 Data Channel Decrypt: Cipher 'AES-128-CBC' initialized with 128 bit key
Sun Oct 30 01:34:22 2016 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Sun Oct 30 01:34:22 2016 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Sun Oct 30 01:34:22 2016 [server] Peer Connection Initiated with [AF_INET]192.34.X.X:1194
Sun Oct 30 01:34:24 2016 SENT CONTROL [server]: 'PUSH_REQUEST' (status=1)
Sun Oct 30 01:34:24 2016 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1 bypass-dhcp,dhcp-option DNS 208.67.222.222,dhcp-option DNS 208.67.220.220,route-gateway 10.8.0.1,topology subnet,ping 10,ping-restart 120,ifconfig 10.8.0.3 255.255.255.0'
Sun Oct 30 01:34:24 2016 OPTIONS IMPORT: timers and/or timeouts modified
Sun Oct 30 01:34:24 2016 OPTIONS IMPORT: --ifconfig/up options modified
Sun Oct 30 01:34:24 2016 OPTIONS IMPORT: route options modified
Sun Oct 30 01:34:24 2016 OPTIONS IMPORT: route-related options modified
Sun Oct 30 01:34:24 2016 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Sun Oct 30 01:34:24 2016 ROUTE_GATEWAY 192.168.2.254/255.255.255.0 IFACE=enp1s0 HWADDR=00:8c:fa:30:d3:bd
Sun Oct 30 01:34:24 2016 TUN/TAP device tun0 opened
Sun Oct 30 01:34:24 2016 TUN/TAP TX queue length set to 100
Sun Oct 30 01:34:24 2016 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Sun Oct 30 01:34:24 2016 /sbin/ip link set dev tun0 up mtu 1500
Sun Oct 30 01:34:24 2016 /sbin/ip addr add dev tun0 10.8.0.3/24 broadcast 10.8.0.255
Sun Oct 30 01:34:24 2016 /sbin/ip route add XXX.XXX.XXX.XXX/32 via 192.168.2.254
Sun Oct 30 01:34:24 2016 /sbin/ip route add 0.0.0.0/1 via 10.8.0.1
Sun Oct 30 01:34:24 2016 /sbin/ip route add 128.0.0.0/1 via 10.8.0.1
Sun Oct 30 01:34:24 2016 Initialization Sequence Completed

```

[B]I will appreciate your help,
Regards[/B]

---

### Post by mldoscar on 2017-01-01
any solution? :(

---

### Post by gordintoronto on 2017-01-02
VPN is a 1-to-1, server-client protocol. If you want to access your laptop, you need to install VPN server on it.

---

