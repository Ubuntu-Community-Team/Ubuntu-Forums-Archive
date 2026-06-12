---
title: "LAN to LAN routing via OpenVPN broken in 14.04 (vs. 12.04)"
date: 2014-09-07
forum: Networking &amp; Wireless
---

### Post by Hammi on 2014-09-07
Hi,

I have a working(!) setup under Ubuntu 12.04.5:

```
Internet                           Internet
    |                                  |
192.168.1.* <-> OpenVPN Tunnel <-> 192.168.2.*
```

OpenVPN-Server: 192.168.1.100
OpenVPN-Client: 192.168.2.30

These two machines act as gateways for their respective nets, also to the internet.

Now, I've setup a new OpenVPN server under 14.04.1 with the same configuration - and suddenly machines behind the 192.168.1-OpenVPN Server cannot be accessed anymore from 192.168.2:

```
user@client:~$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_req=1 ttl=64 time=156 ms
64 bytes from 192.168.1.100: icmp_req=2 ttl=64 time=57.2 ms
64 bytes from 192.168.1.100: icmp_req=3 ttl=64 time=140 ms
^C
--- 192.168.1.100 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 57.267/117.826/156.152/43.324 ms

client$ user@client:~$ ping 192.168.1.24
PING 192.168.1.24 (192.168.1.24) 56(84) bytes of data.
^C
--- 192.168.1.24 ping statistics ---
2 packets transmitted, 0 received, 100% packet loss, time 999ms
```

If I boot the 12.04.5 machine again (with the same OpenVPN config), everything is  working again as it's supposed to be. 

```
user@client:~$ ping 192.168.1.100
PING 192.168.1.100 (192.168.1.100) 56(84) bytes of data.
64 bytes from 192.168.1.100: icmp_req=1 ttl=64 time=124 ms
64 bytes from 192.168.1.100: icmp_req=2 ttl=64 time=62.9 ms
64 bytes from 192.168.1.100: icmp_req=3 ttl=64 time=57.2 ms
^C
--- 192.168.1.100 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 57.229/81.562/124.492/30.446 ms
user@client:~$ ping 192.168.1.24
PING 192.168.1.24 (192.168.1.24) 56(84) bytes of data.
64 bytes from 192.168.1.24: icmp_req=1 ttl=63 time=187 ms
64 bytes from 192.168.1.24: icmp_req=2 ttl=63 time=57.8 ms
64 bytes from 192.168.1.24: icmp_req=3 ttl=63 time=71.3 ms
^C
--- 192.168.1.24 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 57.819/105.661/187.788/58.336 ms
```

So I must have missed some piece  of configuration on the 14.04.1 machine, or a substantial change from 12.04 to 14.04. But I don't know which.

** Config OpenVPN server (192.168.1.100, new):**

```
$ route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
default         192.168.1.1 0.0.0.0         UG    0      0        0 eth0
10.8.0.0        10.8.0.2        255.255.255.0   UG    0      0        0 tun0
10.8.0.2        *               255.255.255.255 UH    0      0        0 tun0
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.2.0     10.8.0.2        255.255.255.0   UG    0      0        0 tun0
```

```
$ cat server.conf | grep -v ^# | grep -v ^\;
port 1194
proto tcp
dev tun
ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/server.crt
key /etc/openvpn/keys/server.key
dh /etc/openvpn/keys/dh1024.pem
server 10.8.0.0 255.255.255.0
ifconfig-pool-persist ipp.txt
push "route 192.168.1.0 255.255.255.0"
push "route 192.168.2.0 255.255.255.0"
client-config-dir ccd
route 192.168.2.0 255.255.255.0
push "dhcp-option DNS 192.168.1.100"
push "dhcp-option DNS 192.168.1.104"
client-to-client
keepalive 10 30
cipher AES-192-CBC # AES
comp-lzo
max-clients 3
user nobody
group nogroup
persist-key
persist-tun
status /var/log/openvpn-status.log
log         /var/log/openvpn.log
verb 6
mute 20
```

```
$ sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 1
```

** Config OpenVPN client (192.168.2.30, unchanged):**

```
$ route
Kernel-IP-Routentabelle
Ziel            Router          Genmask         Flags Metric Ref    Use Iface
default         *               0.0.0.0         U     0      0        0 ppp0
default         192.168.178.1   0.0.0.0         UG    0      0        0 eth1
10.8.0.0        10.8.0.5        255.255.255.0   UG    0      0        0 tun0
10.8.0.5        *               255.255.255.255 UH    0      0        0 tun0
87.186.224.111  *               255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     *               255.255.0.0     U     1000   0        0 eth0
192.168.1.0     10.8.0.5        255.255.255.0   UG    0      0        0 tun0
localnet        *               255.255.255.0   U     0      0        0 eth0
192.168.178.0   *               255.255.255.0   U     1      0        0 eth1
```

```
$  cat /etc/openvpn/client.conf | grep -v ^# | grep -v ^\;
client
dev tun
proto tcp
remote vpn.sample.com 1194
resolv-retry infinite
nobind
persist-key
persist-tun
ca /etc/openvpn/keys/ca.crt
cert /etc/openvpn/keys/client1.crt
key /etc/openvpn/keys/client1.key
remote-cert-tls server
cipher AES-192-CBC # AES
comp-lzo
log /var/log/openvpn.log
status openvpn-status.log
verb 5
mute 20

```

```
$ sysctl net.ipv4.ip_forward
net.ipv4.ip_forward = 1
```

---

