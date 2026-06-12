---
title: "Ubuntu 16.04 LTS 0 New installation with OpenVPnClient - No TRAFFIC"
date: 2018-04-02
forum: Networking &amp; Wireless
---

### Post by ylafont on 2018-04-02
Wondering if anyone can point me in the right direction, as i am not sure if there are additional steps required in order to make a successful client connection.   I have a new installation of Ubuntu 16.04 configured with OpenVPN client connection. A VPN is established, however there is no traffic  across the internet when the connection is made. 


Syslog 
```
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 OpenVPN 2.3.10 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jun 22 2017Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 library versions: OpenSSL 1.0.2g  1 Mar 2016, LZO 2.08
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 WARNING: file 'auth.txt' is group or others accessible
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 Socket Buffers: R=[212992->212992] S=[212992->212992]
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 UDPv4 link local: [undef]
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 UDPv4 link remote: [AF_INET]216.151.180.21:1194
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 TLS: Initial packet from [AF_INET]216.151.180.21:1194, sid=9897aced a5ff0979
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 WARNING: this configuration may cache passwords in memory -- use the auth-nocache option to prevent this
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 VERIFY OK: depth=1, C=US, ST=VPN, L=VPN, O=VPN, OU=VPN, CN=VPN, name=VPN, emailAddress=VPN
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 Validating certificate key usage
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 ++ Certificate has key usage  00a0, expects 00a0
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 VERIFY KU OK
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 Validating certificate extended key usage
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 ++ Certificate has EKU (str) TLS Web Server Authentication, expects TLS Web Server Authentication
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 VERIFY EKU OK
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 VERIFY OK: depth=0, C=US, ST=VPN, L=VPN, O=VPN, OU=VPN, CN=vpn, name=VPN
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 Data Channel Encrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 Data Channel Encrypt: Using 256 bit message hash 'SHA256' for HMAC authentication
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 Data Channel Decrypt: Cipher 'AES-256-CBC' initialized with 256 bit key
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 Data Channel Decrypt: Using 256 bit message hash 'SHA256' for HMAC authentication
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 Control Channel: TLSv1.2, cipher TLSv1/SSLv3 ECDHE-RSA-AES256-GCM-SHA384, 2048 bit RSA
Apr  2 10:30:11 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:11 2018 [vpn] Peer Connection Initiated with [AF_INET]216.151.180.21:1194
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 SENT CONTROL [vpn]: 'PUSH_REQUEST' (status=1)
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 PUSH: Received control message: 'PUSH_REPLY,redirect-gateway def1 bypass-dhcp,dhcp-option DNS 198.18.0.1,dhcp-option DNS 198.18.0.2,rcvbuf 493216,sndbuf 493216,explicit-exit-notify 5,route-gateway 172.21.94.1,topology subnet,ping 20,ping-restart 40,ifconfig 172.21.94.10 255.255.254.0,peer-id 0'
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 OPTIONS IMPORT: timers and/or timeouts modified
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 OPTIONS IMPORT: explicit notify parm(s) modified
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 OPTIONS IMPORT: --sndbuf/--rcvbuf options modified
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 Socket Buffers: R=[212992->425984] S=[212992->425984]
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 OPTIONS IMPORT: --ifconfig/up options modified
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 OPTIONS IMPORT: route options modified
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 OPTIONS IMPORT: route-related options modified
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 OPTIONS IMPORT: peer-id set
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 OPTIONS IMPORT: adjusting link_mtu to 1573
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 ROUTE_GATEWAY 192.168.101.1/255.255.255.0 IFACE=eno1 HWADDR=c0:3f:d5:6f:04:40
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 TUN/TAP device tun0 opened
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 TUN/TAP TX queue length set to 100
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 /sbin/ip link set dev tun0 up mtu 1500
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 /sbin/ip addr add dev tun0 172.21.94.10/23 broadcast 172.21.95.255
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 /sbin/ip route add 216.151.180.21/32 via 192.168.101.1
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 /sbin/ip route add 0.0.0.0/1 via 172.21.94.1
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 /sbin/ip route add 128.0.0.0/1 via 172.21.94.1
Apr  2 10:30:13 Media1 VpnConnection.sh[1043]: Mon Apr  2 10:30:13 2018 Initialization Sequence Completed

```


Ping long for each address
```
PING 216.151.180.21 (216.151.180.21) 56(84) bytes of data.
64 bytes from 216.151.180.21: icmp_seq=1 ttl=52 time=16.9 ms
64 bytes from 216.151.180.21: icmp_seq=2 ttl=52 time=20.4 ms
64 bytes from 216.151.180.21: icmp_seq=3 ttl=52 time=20.5 ms
64 bytes from 216.151.180.21: icmp_seq=4 ttl=52 time=20.4 ms
64 bytes from 216.151.180.21: icmp_seq=5 ttl=52 time=15.7 ms
64 bytes from 216.151.180.21: icmp_seq=6 ttl=52 time=18.7 ms
64 bytes from 216.151.180.21: icmp_seq=7 ttl=52 time=18.5 ms


--- 216.151.180.21 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6010ms
rtt min/avg/max/mdev = 15.768/18.776/20.506/1.723 ms
PING 172.21.94.1 (172.21.94.1) 56(84) bytes of data.
64 bytes from 172.21.94.1: icmp_seq=1 ttl=64 time=15.3 ms
64 bytes from 172.21.94.1: icmp_seq=2 ttl=64 time=33.1 ms
64 bytes from 172.21.94.1: icmp_seq=3 ttl=64 time=27.6 ms
64 bytes from 172.21.94.1: icmp_seq=4 ttl=64 time=16.6 ms
64 bytes from 172.21.94.1: icmp_seq=5 ttl=64 time=21.9 ms
64 bytes from 172.21.94.1: icmp_seq=6 ttl=64 time=27.6 ms
64 bytes from 172.21.94.1: icmp_seq=7 ttl=64 time=22.8 ms


--- 172.21.94.1 ping statistics ---
7 packets transmitted, 7 received, 0% packet loss, time 6009ms
rtt min/avg/max/mdev = 15.325/23.608/33.168/5.908 ms
PING 172.21.94.10 (172.21.94.10) 56(84) bytes of data.
64 bytes from 172.21.94.10: icmp_seq=1 ttl=64 time=0.036 ms
64 bytes from 172.21.94.10: icmp_seq=2 ttl=64 time=0.044 ms
64 bytes from 172.21.94.10: icmp_seq=3 ttl=64 time=0.051 ms
64 bytes from 172.21.94.10: icmp_seq=4 ttl=64 time=0.051 ms
64 bytes from 172.21.94.10: icmp_seq=5 ttl=64 time=0.053 ms
64 bytes from 172.21.94.10: icmp_seq=6 ttl=64 time=0.049 ms
```

ifConfig
```
eno1      Link encap:Ethernet  HWaddr c0:3f:d5:6f:04:40  
          inet addr:192.168.101.149  Bcast:192.168.101.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3512 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2954 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1448722 (1.4 MB)  TX bytes:458662 (458.6 KB)
          Interrupt:20 Memory:f7c00000-f7c20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:190 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:13984 (13.9 KB)  TX bytes:13984 (13.9 KB)


tun0      Link encap:UNSPEC  HWaddr 00-00-00-00-00-00-00-00-00-00-00-00-00-00-00-00  
          inet addr:172.21.94.10  P-t-P:172.21.94.10  Mask:255.255.254.0
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:751 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:588 (588.0 B)  TX bytes:49420 (49.4 KB)
```

Any assistance is greatly appreciated, thank you in advance.

---

### Post by TheFu on 2018-04-02
I would contact the openvpn server admin for a valid .ovpn client file.

If you are running the server, please post the vpnserver.conf file without comments and explain how the client and server are connected.  Main thing is they can't be on the same subnet.  The client-side startup script and .ovpn file (without any certs) would be helpful too.

---

### Post by ylafont on 2018-04-02
No server config, just a client connection with another simple startup script. nothing fancy.


Startup Script
```
#!/bin/bash
cd /etc/openvpn
sudo openvpn --config vpnfile.ovpn

```


Client .ovpn
```
client
dev tun
proto udp
remote nyc-a38.wlvpn.com 1194
resolv-retry infinite
nobind
persist-key
persist-tun
persist-remote-ip
#ca vpn.crt


tls-client
remote-cert-tls server
auth-user-pass
comp-lzo
verb 3


auth SHA256
cipher AES-256-CBC


<ca>
-----BEGIN CERTIFICATE-----


-----END CERTIFICATE-----
</ca>

```


Thanks for the assistance.

---

### Post by TheFu on 2018-04-02
Someone is running the openvpn server.  

They have a server.conf file and should provide the correct client.ovpn file for you. There are settings in the server-side which cannot be ignored or overridden by the client settings.

You can add  **--verb 4** to the openvpn command to see more details.
I have some more client-side settings for the openvpn server that I run:
```
user nobody
group nogroup

# force tun up/dn to update the resolv.conf
up /etc/openvpn/update-resolv-conf
down /etc/openvpn/update-resolv-conf

# point to the DNS you want
dhcp-option DNS 172.22.22.1

```

Seeing the **route -n** would be helpful.  Thanks for the code-tags!

For a commercial VPN connection, I have some other things:
```
reneg-sec 0
crl-verify crl.rsa.4096.pem
ca ca.rsa.4096.crt
disable-occ

``` These were provided by the vendor.  The vendor should provide a correct .ovpn file.

---

### Post by ylafont on 2018-04-02
Actually i reached out to them and they insists it is a configuration issue on my end.  I am going to see if a test on a machine with a gui, (that should tell me) 

Table 
```
Kernel IP routing tableDestination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.21.90.1     128.0.0.0       UG    0      0        0 tun0
0.0.0.0         192.168.101.1   0.0.0.0         UG    0      0        0 eno1
128.0.0.0       172.21.90.1     128.0.0.0       UG    0      0        0 tun0
172.21.90.0     0.0.0.0         255.255.254.0   U     0      0        0 tun0
192.168.101.0   0.0.0.0         255.255.255.0   U     0      0        0 eno1
216.151.180.23  192.168.101.1   255.255.255.255 UGH   0      0        0 eno1



```

The other item i have found is this thread
[https://forums.openvpn.net/viewtopic.php?t=22103](https://forums.openvpn.net/viewtopic.php?t=22103)

pointing to to here
[https://openvpn.net/index.php/open-source/documentation/howto.html#redirect](https://openvpn.net/index.php/open-source/documentation/howto.html#redirect)

makes me think  this is was is needed

```
**iptables -t nat -A POSTROUTING -s 10.8.0.0/24 -o eth0 -j MASQUERADE**
```

question is what IP should be used?

---

### Post by TheFu on 2018-04-02
Where did you get the client .ovpn file?  Link please.

On Linux, a GUI seldom provides any more details for problem solving.  Definitely will not for openvpn.

---

### Post by ylafont on 2018-04-02
config files are located at the link below.


[https://www.usenetserver.com/vpn/software/configs/](https://www.usenetserver.com/vpn/software/configs/)


Thank you for the assistance TheFu

---

### Post by TheFu on 2018-04-03
Appears to me that a tunnel is missing in the routing tables.
On mine, it is this:```

10.12.11.1      10.12.11.5      255.255.255.255 UGH   0      0        0 tun0
```

But on mine, I don't have this route:```

172.21.90.0     0.0.0.0         255.255.254.0   U     0      0        0 tun0
```

```
$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface 
0.0.0.0         10.12.11.5      128.0.0.0       UG    0      0        0 tun0
0.0.0.0         172.22.22.1     0.0.0.0         UG    0      0        0 enx000ec
10.12.11.1      10.12.11.5      255.255.255.255 UGH   0      0        0 tun0
10.12.11.5      0.0.0.0         255.255.255.255 UH    0      0        0 tun0
128.0.0.0       10.12.11.5      128.0.0.0       UG    0      0        0 tun0
172.22.22.0     0.0.0.0         255.255.255.0   U     0      0        0 enx000ec
172.98.67.74    172.22.22.1     255.255.255.255 UGH   0      0        0 enx000ec
```
Is a working, active, routing.
172.22.22.1 is my internal router IP.
10.12.11.5 is the on the same subnet as the IP tun0 gets (10.12.11.6)
172.98.67.74 is the public IP in Canada provided by the service today.
The 10.x.x.x are all VPN stuff. Not part of my network.
Every time I connect, a different 10.x.x.x network is selected. Guess that is a server-side thing.  The public IP changes too.

I've not needed to do any firewall rules.

---

### Post by ylafont on 2018-04-03
Thank you for all the assistance and follow-up.  I finally got to the bottom of it. it turns out routing was working, but DNS was not being updated when the VPN was activated. 

I followed these two guides. 

[http://www.softwarepassion.com/solving-dns-problems-with-openvpn-on-ubuntu-box/](http://www.softwarepassion.com/solving-dns-problems-with-openvpn-on-ubuntu-box/)

[COLOR=#333333][FONT=Arial]https://github.com/masterkorp/openvpn-update-resolv-conf


Up and running now!

Thank you again.[/FONT][/COLOR]

---

