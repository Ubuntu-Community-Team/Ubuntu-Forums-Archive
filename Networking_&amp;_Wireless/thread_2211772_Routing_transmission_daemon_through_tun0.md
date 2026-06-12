---
title: "Routing transmission daemon through tun0"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by darthdudey on 2014-03-17
Hi, I've been trying to get this to work for way too long. I set up openvpn on a openvz server, and I'm trying to connect to it with a ubuntu server and have ONLY transmission-daemon use tun0. I tried to configure the iptables on the openvpn server to forward all outgoing traffic from the clients and allow incoming traffic on certian ports, but I'm not sure if I did it correctly. [COLOR=#ff0000]As a note things in all caps are just referring to what is actually entered.[/COLOR]

After installing and configuring the server and client I set up a group called vpnroute, then used iptables to only allow vpnroute to use tun0, then I bound transmission to 10.8.0.6 and ran it with:
```
sudo -g vpnroute transmission-daemon -f -t -u USERNAME -v PASSWORD -w DOWNLOADPATH -g /etc/transmission-daemon/ -i 10.8.0.6 -r 10.8.0.6
```

however it complains with :
```

13:32:41.881] Transmission 2.82 (14160) started (session.c:738)
[13:32:41.882] RPC Server Adding address to whitelist: 127.0.0.1 (rpc-server.c:828)
[13:32:41.882] RPC Server Serving RPC and Web requests on port 127.0.0.1:9091/transmission/ (rpc-server.c:1035)
[13:32:41.882] RPC Server Password required (rpc-server.c:1042)
[13:32:41.882] Port Forwarding Stopped (port-forwarding.c:183)
[13:32:41.882] UDP Failed to set receive buffer: requested 4194304, got 425984 (tr-udp.c:78)
[13:32:41.882] UDP Please add the line "net.core.rmem_max = 4194304" to /etc/sysctl.conf (tr-udp.c:83)
[13:32:41.882] UDP Failed to set send buffer: requested 1048576, got 425984 (tr-udp.c:89)
[13:32:41.882] UDP Please add the line "net.core.wmem_max = 1048576" to /etc/sysctl.conf (tr-udp.c:94)

```

Additionally here are various relevant configuration details:

OpenVPN server.conf:
```

port 1194
proto udp
dev tun0

ca /etc/openvpn/ca.crt
cert /etc/openvpn/osiris.crt
key /etc/openvpn/osiris.key 

dh /etc/openvpn/dh1024.pem

server 10.8.0.0 255.255.255.0

ifconfig-pool-persist ipp.txt

push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"

push "redirect-gateway defi by-pass-dhcp" 
push "dhcp-option DNS 10.8.0.1"

keepalive 10 120

user nobody
group nogroup

persist-key
persist-tun

status openvpn-status.log

verb 3

```





OpenVPN client.conf:
```

remote DOMAINNAME 1194

resolv-retry infinite

nobind

persist-key
persist-tun

ca /etc/openvpn/ca.crt
cert /etc/openvpn/rodney.crt
key /etc/openvpn/rodney.key

ns-cert-type server

verb 3

```

Server IPtables:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  anywhere             anywhere            
ACCEPT     all  --  anywhere             anywhere             state RELATED,ESTABLISHED
ACCEPT     all  --  10.8.0.0/24          anywhere            
REJECT     all  --  anywhere             anywhere             reject-with icmp-port-unreachable

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

root@osiris:~# iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
DNAT       udp  --  anywhere             anywhere             multiport dports 9091 to:10.8.0.6
DNAT       tcp  --  anywhere             anywhere             multiport dports 9091 to:10.8.0.6
DNAT       udp  --  anywhere             anywhere             multiport dports 40001 to:10.8.0.6
DNAT       tcp  --  anywhere             anywhere             multiport dports 40001 to:10.8.0.6

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  anywhere             anywhere            
SNAT       all  --  10.8.0.0/24          anywhere             to:VENET IP
SNAT       all  --  anywhere             anywhere             to:VENET IP
SNAT       all  --  10.8.0.0/24          anywhere             to:VENET IP

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 

```

Client IPtables:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
fail2ban-ssh  tcp  --  anywhere             anywhere             multiport dports ssh

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
REJECT     all  --  anywhere             anywhere             owner GID match vpnroute reject-with icmp-port-unreachable
REJECT     all  --  anywhere             anywhere             owner GID match vpnroute reject-with icmp-port-unreachable

Chain fail2ban-ssh (1 references)
target     prot opt source               destination         
RETURN     all  --  anywhere             anywhere   

```

Transmission configuration:
```

{
    "alt-speed-down": 1000, 
    "alt-speed-enabled": false, 
    "alt-speed-time-begin": 540, 
    "alt-speed-time-day": 0, 
    "alt-speed-time-enabled": false, 
    "alt-speed-time-end": 0, 
    "alt-speed-up": 50, 
    "bind-address-ipv4": "10.8.0.6", 
    "bind-address-ipv6": "::", 
    "blocklist-enabled": false, 
    "blocklist-url": "http://www.example.com/blocklist", 
    "cache-size-mb": 100, 
    "dht-enabled": false, 
    "download-dir": "/mnt/internal/downloads/", 
    "download-limit": 100, 
    "download-limit-enabled": 0, 
    "download-queue-enabled": false, 
    "download-queue-size": 5, 
    "encryption": 1, 
    "idle-seeding-limit": 30, 
    "idle-seeding-limit-enabled": false, 
    "incomplete-dir": "/home/rodney/Downloads", 
    "incomplete-dir-enabled": false, 
    "lpd-enabled": false, 
    "max-peers-global": 200, 
    "message-level": 2, 
    "peer-congestion-algorithm": "", 
    "peer-id-ttl-hours": 6, 
    "peer-limit-global": 1000, 
    "peer-limit-per-torrent": 100, 
    "peer-port": 40001, 
    "peer-port-random-high": 65535, 
    "peer-port-random-low": 49152, 
    "peer-port-random-on-start": false, 
    "peer-socket-tos": "default", 
    "pex-enabled": false, 
    "port-forwarding-enabled": false, 
    "preallocation": 1, 
    "prefetch-enabled": 1, 
    "queue-stalled-enabled": true, 
    "queue-stalled-minutes": 30, 
    "ratio-limit": 2, 
    "ratio-limit-enabled": false, 
    "rename-partial-files": true, 
    "rpc-authentication-required": true, 
    "rpc-bind-address": "10.8.0.6", 
    "rpc-enabled": true, 
    "rpc-password": "PASSWORD", 
    "rpc-port": 9091, 
    "rpc-url": "/transmission/", 
    "rpc-username": "USERNAME", 
    "rpc-whitelist": "127.0.0.1", 
    "rpc-whitelist-enabled": false, 
    "scrape-paused-torrents-enabled": true, 
    "script-torrent-done-enabled": false, 
    "script-torrent-done-filename": "", 
    "seed-queue-enabled": false, 
    "seed-queue-size": 10, 
    "speed-limit-down": 25000, 
    "speed-limit-down-enabled": false, 
    "speed-limit-up": 25555, 
    "speed-limit-up-enabled": false, 
    "start-added-torrents": true, 
    "trash-original-torrent-files": false, 
    "umask": 18, 
    "upload-limit": 100, 
    "upload-limit-enabled": 0, 
    "upload-slots-per-torrent": 14, 
    "utp-enabled": true
}


```

Here are the openvpn logs which seem to connect and function normally:
Server:
```

Mon Mar 17 17:25:29 2014 OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL  (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Jul 12  2013
Mon Mar 17 17:25:29 2014 Diffie-Hellman initialized with 1024 bit key
Mon Mar 17 17:25:29 2014 Socket Buffers: R=[245760->131072] S=[245760->131072]
Mon Mar 17 17:25:29 2014 ROUTE_GATEWAY ON_LINK IFACE=venet0 HWADDR=00:00:00:00:00:00
Mon Mar 17 17:25:29 2014 TUN/TAP device tun0 opened
Mon Mar 17 17:25:29 2014 TUN/TAP TX queue length set to 100
Mon Mar 17 17:25:29 2014 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Mon Mar 17 17:25:29 2014 /sbin/ip link set dev tun0 up mtu 1500
Mon Mar 17 17:25:29 2014 /sbin/ip addr add dev tun0 local 10.8.0.1 peer 10.8.0.2
Mon Mar 17 17:25:29 2014 /sbin/ip route add 10.8.0.0/24 via 10.8.0.2
Mon Mar 17 17:25:29 2014 UDPv4 link local (bound): [undef]
Mon Mar 17 17:25:29 2014 UDPv4 link remote: [undef]
Mon Mar 17 17:25:29 2014 MULTI: multi_init called, r=256 v=256
Mon Mar 17 17:25:29 2014 IFCONFIG POOL: base=10.8.0.4 size=62, ipv6=0
Mon Mar 17 17:25:29 2014 ifconfig_pool_read(), in='rodney,10.8.0.4', TODO: IPv6
Mon Mar 17 17:25:29 2014 succeeded -> ifconfig_pool_set()
Mon Mar 17 17:25:29 2014 IFCONFIG POOL LIST
Mon Mar 17 17:25:29 2014 rodney,10.8.0.4
Mon Mar 17 17:25:29 2014 Initialization Sequence Completed
Mon Mar 17 17:26:00 2014 96.51.61.173:57256 TLS: Initial packet from [AF_INET]IP, sid=5c356959 53d50210
Mon  Mar 17 17:26:01 2014 96.51.61.173:57256 VERIFY OK: depth=1, C=US,  ST=CA, L=SanFrancisco, O=Fort-Funston, OU=osirisVPN, CN=osirisVPN,  name=osirisVPN, emailAddress=EMAIL
Mon Mar 17 17:26:01 2014  96.51.61.173:57256 VERIFY OK: depth=0, C=CA, ST=AB, L=Lethbridge,  O=Fort-Funston, OU=osirisVPN, CN=USER, name=osirisVPN,  emailAddress=EMAIL
Mon Mar 17 17:26:01 2014 96.51.61.173:57256 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Mar 17 17:26:01 2014 96.51.61.173:57256 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar 17 17:26:01 2014 96.51.61.173:57256 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Mar 17 17:26:01 2014 96.51.61.173:57256 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar 17 17:26:01 2014 96.51.61.173:57256 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Mon Mar 17 17:26:01 2014 96.51.61.173:57256 [USER] Peer Connection Initiated with [AF_INET]CLIENTIP
Mon Mar 17 17:26:01 2014 rodney/96.51.61.173:57256 MULTI_sva: pool returned IPv4=10.8.0.6, IPv6=(Not enabled)
Mon Mar 17 17:26:01 2014 rodney/96.51.61.173:57256 MULTI: Learn: 10.8.0.6 -> USER/IP:57256
Mon Mar 17 17:26:01 2014 rodney/96.51.61.173:57256 MULTI: primary virtual IP for USER/IP:57256: 10.8.0.6
Mon Mar 17 17:26:04 2014 rodney/96.51.61.173:57256 PUSH: Received control message: 'PUSH_REQUEST'
Mon Mar 17 17:26:04 2014 rodney/96.51.61.173:57256 send_push_reply(): safe_cap=940
Mon  Mar 17 17:26:04 2014 rodney/96.51.61.173:57256 SENT CONTROL [rodney]:  'PUSH_REPLY,redirect-gateway defi by-pass-dhcp,dhcp-option DNS  10.8.0.1,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig  10.8.0.6 10.8.0.5' (status=1)

```
Client:
```

Mon Mar 17 15:26:25 2014 OpenVPN 2.3.2 x86_64-pc-linux-gnu [SSL  (OpenSSL)] [LZO] [EPOLL] [PKCS11] [eurephia] [MH] [IPv6] built on Jul 12  2013
Mon Mar 17 15:26:25 2014 Socket Buffers: R=[212992->131072] S=[212992->131072]
Mon Mar 17 15:26:30 2014 UDPv4 link local: [undef]
Mon Mar 17 15:26:30 2014 UDPv4 link remote: [AF_INET]SERVERIP:1194
Mon Mar 17 15:26:30 2014 TLS: Initial packet from [AF_INET]SERVERIP:1194, sid=05587d56 605176f0
Mon  Mar 17 15:26:30 2014 VERIFY OK: depth=1, C=US, ST=CA, L=SanFrancisco,  O=Fort-Funston, OU=osirisVPN, CN=osirisVPN, name=osirisVPN,  emailAddress=EMAIL
Mon Mar 17 15:26:30 2014 VERIFY OK: nsCertType=SERVER
Mon  Mar 17 15:26:30 2014 VERIFY OK: depth=0, C=US, ST=CA, L=SanFrancisco,  O=Fort-Funston, OU=osirisVPN, CN=osiris, name=osirisVPN,  emailAddress=EMAIL
Mon Mar 17 15:26:31 2014 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Mar 17 15:26:31 2014 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar 17 15:26:31 2014 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Mon Mar 17 15:26:31 2014 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Mon Mar 17 15:26:31 2014 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 1024 bit RSA
Mon Mar 17 15:26:31 2014 [osiris] Peer Connection Initiated with [AF_INET]108.174.61.187:1194
Mon Mar 17 15:26:34 2014 SENT CONTROL [osiris]: 'PUSH_REQUEST' (status=1)
Mon  Mar 17 15:26:34 2014 PUSH: Received control message:  'PUSH_REPLY,redirect-gateway defi by-pass-dhcp,dhcp-option DNS  10.8.0.1,route 10.8.0.1,topology net30,ping 10,ping-restart 120,ifconfig  10.8.0.6 10.8.0.5'
Mon Mar 17 15:26:34 2014 Options error: unknown --redirect-gateway flag: defi
Mon Mar 17 15:26:34 2014 OPTIONS IMPORT: timers and/or timeouts modified
Mon Mar 17 15:26:34 2014 OPTIONS IMPORT: --ifconfig/up options modified
Mon Mar 17 15:26:34 2014 OPTIONS IMPORT: route options modified
Mon Mar 17 15:26:34 2014 OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Mon Mar 17 15:26:34 2014 ROUTE_GATEWAY 192.168.0.1/255.255.255.0 IFACE=p5p1 HWADDR=bc:5f:f4:32:f7:d8
Mon Mar 17 15:26:34 2014 TUN/TAP device tun0 opened
Mon Mar 17 15:26:34 2014 TUN/TAP TX queue length set to 100
Mon Mar 17 15:26:34 2014 do_ifconfig, tt->ipv6=0, tt->did_ifconfig_ipv6_setup=0
Mon Mar 17 15:26:34 2014 /sbin/ip link set dev tun0 up mtu 1500
Mon Mar 17 15:26:34 2014 /sbin/ip addr add dev tun0 local 10.8.0.6 peer 10.8.0.5
Mon Mar 17 15:26:34 2014 /sbin/ip route add 10.8.0.1/32 via 10.8.0.5
Mon Mar 17 15:26:34 2014 Initialization Sequence Completed

```

If I try to connect to the remote interface on port 9091 it just times out. I'm fairly sure that the problem is in my iptables config because I'm not very experianced with them. If it helps when the vpn is connected I can ssh to the server via 10.8.0.1

If anybody could help with this you would be my hero

P.S. I know there are some similar threads but trust me I have read all of them and tried everything they said.

---

