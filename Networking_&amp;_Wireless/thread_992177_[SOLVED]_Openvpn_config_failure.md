---
title: "[SOLVED] Openvpn config failure"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by s3gfault on 2008-11-24
Hello, i'm setting up openvpn and there seems to be a problem with the configuration i have made.  I'm following the [Excellent "concise" OpenVPN setup steps]("http://ubuntuforums.org/showthread.php?t=812065") posted earlier this year by SpaceTeddy.

Everything connects up ok, but the server is pushing the wrong route to the client when it connects.  The server gets IP address 10.20.30.1 and it assigns 10.20.30.6 to the client when it connects, but it pushes a point-to-point connection for the client to 10.20.30.5 and also pushes a route to that .5 address for the default gateway.  There is no such .5 ip address though, and so the routing of traffic is not performed correctly.

Any advice greatly appreciated!

Here is my server config file:
```
daemon
port 2607
proto tcp
dev tun0

ca /etc/openvpn/easy-rsa/2.0/keys/ca.crt
cert /etc/openvpn/easy-rsa/2.0/keys/lixxxxxx.crt
key /etc/openvpn/easy-rsa/2.0/keys/lixxxxxx.key
dh /etc/openvpn/easy-rsa/2.0/keys/dh1024.pem

server 10.20.30.0 255.255.255.0
ifconfig-pool-persist openvpn.dhcp

keepalive 10 120
comp-lzo
user nobody
group nogroup

persist-key
persist-tun
status /var/log/openvpn/openvpn-status.log
log-append  /var/log/openvpn/openvpn.log
verb 4
mute 20
client-to-client

plugin /usr/lib/openvpn/openvpn-auth-pam.so common-auth
client-cert-not-required
username-as-common-name

```
My client config file:
```
float
client
dev tun
proto tcp
port 2607

remote xxxx.server.com
redirect-gateway def1

resolv-retry infinite
nobind
persist-key
persist-tun
ca ca.crt
ns-cert-type server
comp-lzo
verb 3

auth-user-pass

http-proxy 192.168.1.5 8080 stdin ntlm

```

And here is an excerpt from the logfile:
```

Mon Nov 24 17:04:47 2008 us=49529 OpenVPN 2.1_rc11 i486-pc-linux-gnu [SSL] [LZO2] [EPOLL] [PKCS11] built on Oct 15 2008
Mon Nov 24 17:04:47 2008 us=565373 TUN/TAP device tun0 opened
Mon Nov 24 17:04:47 2008 us=565395 TUN/TAP TX queue length set to 100
Mon Nov 24 17:04:47 2008 us=565433 /sbin/ifconfig tun0 10.20.30.1 pointopoint 10.20.30.2 mtu 1500
Mon Nov 24 17:04:47 2008 us=567498 /sbin/route add -net 10.20.30.0 netmask 255.255.255.0 gw 10.20.30.2
Mon Nov 24 17:04:47 2008 us=569828 TCPv4_SERVER link local (bound): [undef]:2607
Mon Nov 24 17:04:47 2008 us=569840 TCPv4_SERVER link remote: [undef]
Mon Nov 24 17:04:47 2008 us=569945 IFCONFIG POOL: base=10.20.30.4 size=62

Mon Nov 24 17:34:36 2008 us=308465 Re-using SSL/TLS context
Mon Nov 24 17:34:36 2008 us=308529 LZO compression initialized
Mon Nov 24 17:34:36 2008 us=308891 Local Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_SERVER,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,key-method 2,tls-server'
Mon Nov 24 17:34:36 2008 us=308904 Expected Remote Options String: 'V4,dev-type tun,link-mtu 1544,tun-mtu 1500,proto TCPv4_CLIENT,comp-lzo,cipher BF-CBC,auth SHA1,keysize 128,key-method 2,tls-client'
Mon Nov 24 17:34:40 2008 us=192702 david/w.x.y.z:53395 MULTI: Learn: 10.20.30.6 -> david/w.x.y.z:53395
Mon Nov 24 17:34:40 2008 us=192717 david/w.x.y.z:53395 MULTI: primary virtual IP for david/w.x.y.z:53395: 10.20.30.6
Mon Nov 24 17:34:41 2008 us=125986 david/w.x.y.z:53395 PUSH: Received control message: 'PUSH_REQUEST'
Mon Nov 24 17:34:41 2008 us=126121 david/w.x.y.z:53395 SENT CONTROL [david]: 'PUSH_REPLY,route 10.20.30.0 255.255.255.0,topology net30,ping 10,ping-restart 120,ifconfig 10.20.30.6 10.20.30.5' (status=1)
Mon Nov 24 17:34:41 2008 us=453138 david/w.x.y.z:53395 Connection reset, restarting [0]
Mon Nov 24 17:34:41 2008 us=453177 david/w.x.y.z:53395 SIGUSR1[soft,connection-reset] received, client-instance restarting
Mon Nov 24 17:34:41 2008 us=453504 TCP/UDP: Closing socket

```


EDIT Update:
I added this line to my client config files
route-gateway 10.20.30.1
and this error message appeared in the connection output
```

Mon Nov 24 14:32:45 2008 /sbin/route add -net 0.0.0.0 netmask 128.0.0.0 gw 10.20.30.1
SIOCADDRT: No such process
Mon Nov 24 14:32:45 2008 ERROR: Linux route add command failed: external program exited with error status: 7
Mon Nov 24 14:32:45 2008 /sbin/route add -net 128.0.0.0 netmask 128.0.0.0 gw 10.20.30.1
SIOCADDRT: No such process
Mon Nov 24 14:32:45 2008 ERROR: Linux route add command failed: external program exited with error status: 7
Mon Nov 24 14:32:45 2008 /sbin/route add -net 10.20.30.0 netmask 255.255.255.0 gw 10.20.30.1
SIOCADDRT: No such process
Mon Nov 24 14:32:45 2008 ERROR: Linux route add command failed: external program exited with error status: 7
Mon Nov 24 14:32:45 2008 Initialization Sequence Completed

```
hmm? Why does that command fail? it looks fine to me.

---

### Post by s3gfault on 2008-11-25
This is the output i get from my client when it attempts to connect, with the directive 
route-gateway 10.20.30.1

The error is in the PUSH_REPLY from the server, it should have the end part of that string as "10.20.30.6 10.20.30.1" instead of that 10.20.30.5 garbage.
```
Tue Nov 25 08:09:57 2008 SENT CONTROL : 'PUSH_REQUEST' (status=1)
Tue Nov 25 08:09:57 2008 PUSH: Received control message: 'PUSH_REPLY,route 10.20.30.0 255.255.255.0,topology net30,ping 10,ping-restart 120,ifconfig 10.20.30.6 10.20.30.5'
Tue Nov 25 08:09:57 2008 OPTIONS IMPORT: timers and/or timeouts modified
Tue Nov 25 08:09:57 2008 OPTIONS IMPORT: --ifconfig/up options modified
Tue Nov 25 08:09:57 2008 OPTIONS IMPORT: route options modified
Tue Nov 25 08:09:57 2008 TUN/TAP device tun0 opened
Tue Nov 25 08:09:57 2008 TUN/TAP TX queue length set to 100
Tue Nov 25 08:09:57 2008 /sbin/ifconfig tun0 10.20.30.6 pointopoint 10.20.30.5 mtu 1500
Tue Nov 25 08:09:57 2008 /sbin/route del -net 0.0.0.0 netmask 0.0.0.0
Tue Nov 25 08:09:57 2008 /sbin/route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.20.30.1
SIOCADDRT: No such process
Tue Nov 25 08:09:57 2008 ERROR: Linux route add command failed: external program exited with error status: 7
Tue Nov 25 08:09:57 2008 /sbin/route add -net 10.20.30.0 netmask 255.255.255.0 gw 10.20.30.1
SIOCADDRT: No such process
Tue Nov 25 08:09:57 2008 ERROR: Linux route add command failed: external program exited with error status: 7
Tue Nov 25 08:09:57 2008 Initialization Sequence Completed

```

---

### Post by SpaceTeddy on 2008-11-25
the configration of the interfaces is correct. In server mode, openvn only uses every 4rth IP, starting with x.y.z.6... so, the ip's are x.y.z.6, x.y.z.10, x.y.z.14, etc... 
The def gateway is set correctly too - it is always (!) the ip one below ! the ip two blow the assigned one is the ptp partner on openvpn side. The reason this is done is because there is no direct route between two clients on the VPN - everything needs to be routed over the VPN server. So the server creates a point-to-point connection with the client and routes the entire subnet via this one ip. To acctally be able to use this you need to specify the client-to-client option in the server.

the question is - what are you trying to accomplish, as your configuration seems to be correct to me...

---

### Post by s3gfault on 2008-11-25
oh, I'd like to tunnel all network traffic for the client through the vpn to the vpn server.  The reason i thought it was wrong is that the redirect-gateway directive pushes 10.20.30.5 as the default gateway for the client, but there is no machine with that ip address and traffic destined for it is dropped.  The server has 10.20.30.1 and it seemed to me that the make it route the packets, (masquerade them out to the internet) that the server should be the default gateway.
```

david@DC78000eval:~/vpnclient$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.1.69.170     10.1.128.1      255.255.255.255 UGH   0      0        0 eth0
10.20.30.5      *               255.255.255.255 UH    0      0        0 tun0
10.20.30.0      10.20.30.5      255.255.255.0   UG    0      0        0 tun0
10.1.128.0      *               255.255.240.0   U     1      0        0 eth0
default         10.20.30.5      0.0.0.0         UG    0      0        0 tun0

```

---

### Post by SpaceTeddy on 2008-11-25
the server is their default gateway - but it handles these IPs internally without you seeing them. The IP you do see (10.20.30.1) is the interface that is exposed to the world so that connection can enter the openvpn network from the outside. acctually, when you send a packet to 10.20.30.6 it would go to to 10.20.30.1 and then the openvpn handles the traffic internal to 10.20.30.5 which sends it to 10.20.30.6. This is all correct.

since you want to tunnel everything - add 
```
push "redirect-gateway"
```
to your server configuration. that should do the trick (if you have ip_forwarding set up and either masquerading or proper routes set)...

---

### Post by s3gfault on 2008-11-25
Thanks SpaceTeddy, it didn't occur to me to think of IP addresses not associated with any device.  I suppose the problem must be in my iptables or other component.  I'm looking into this.

Mind looking at my iptables script?
```

/sbin/iptables -A INPUT -p tcp -i eth0 --dport 2607 -j ACCEPT
/sbin/iptables -A FORWARD -i tun0 -j ACCEPT
/sbin/iptables -A INPUT -i tun0 -j ACCEPT
/sbin/iptables -A POSTROUTING --table nat -s 10.20.30.0/24 -o eth0 -j MASQUERADE
/sbin/iptables -A OUTPUT -j ACCEPT

```

---

### Post by SpaceTeddy on 2008-11-25
if your default action is DROP in FORWARD this does not work. 

You are allowing packets to flow from the vpn to eth0 - but you are not allowing any backchannel ! any answer that comes back is being blocked (if you default DROP or REJECT)

either Add this line
```
/sbin/iptables -A FORWARD -o tun0 -j ACCEPT
```
to allow traffic in both directions, or change your firewalling to statefull by removing the FORWARD statement you have and adding these two lines:

```
/sbin/iptables -A FORWARD -m state --state ESTABLISHED,RELATED -j ACCEPT
/sbin/iptables -A FORWARD -i tun0 -o eth0 -m state --state NEW -j ACCEPT
```

the second approach is stateful and will only allow connections from the vpn into the web and not vice versa... 
I know i am being very short in my answer and not very explaining... but time is limited at the moment

---

### Post by s3gfault on 2008-11-25
Thanks, that was it indeed.  Cheers * 100.

---

