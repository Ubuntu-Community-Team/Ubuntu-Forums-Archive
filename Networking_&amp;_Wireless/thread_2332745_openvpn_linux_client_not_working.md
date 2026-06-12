---
title: "openvpn linux client not working"
date: 2016-08-03
forum: Networking &amp; Wireless
---

### Post by jarush on 2016-08-03
I've got an openvpn server that has been working fine with Windows and Android clients.  I recently deployed a new linux server and I'm trying to connect it to the same VPN, however it isn't working.  The connection is established and it looks like the right responses are being sent to the client, but the tap1 interface is never configured.  Both client and server are Ubuntu 15.10.  Syslog and config file below - any help appreciated.

This is what gets dumped in the client's syslog:
```

Aug  3 10:28:28 kesh systemd[1]: Starting OpenVPN service...
Aug  3 10:28:28 kesh systemd[1]: Starting OpenVPN connection to client...
Aug  3 10:28:28 kesh systemd[1]: Started OpenVPN service.
Aug  3 10:28:28 kesh ovpn-client[344]: OpenVPN 2.3.7 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [EPOLL] [PKCS11] [MH] [IPv6] built on Jul  8 2015
Aug  3 10:28:28 kesh ovpn-client[344]: library versions: OpenSSL 1.0.2d 9 Jul 2015, LZO 2.08
Aug  3 10:28:28 kesh systemd[1]: Started OpenVPN connection to client.
Aug  3 10:28:28 kesh ovpn-client[347]: Socket Buffers: R=[212992->131072] S=[212992->131072]
Aug  3 10:28:33 kesh ovpn-client[347]: UDPv4 link local (bound): [undef]
Aug  3 10:28:33 kesh ovpn-client[347]: UDPv4 link remote: [AF_INET]server_ip_address:1194
Aug  3 10:28:33 kesh ovpn-client[347]: TLS: Initial packet from [AF_INET]server_ip_address:1194, sid=a270a384 318ce769
Aug  3 10:28:33 kesh ovpn-client[347]: VERIFY OK: depth=1, C=US, ST=MN, L=City, O=Org IT, OU=Dept, CN=Dept CA, name=Name, emailAddress=admin@home.local
Aug  3 10:28:33 kesh ovpn-client[347]: VERIFY OK: nsCertType=SERVER
Aug  3 10:28:33 kesh ovpn-client[347]: VERIFY OK: depth=0, C=US, ST=MN, L=City, O=Org IT, OU=Dept, CN=vpn02, name=Name, emailAddress=admin@home.local
Aug  3 10:28:34 kesh ovpn-client[347]: Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Aug  3 10:28:34 kesh ovpn-client[347]: Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Aug  3 10:28:34 kesh ovpn-client[347]: Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Aug  3 10:28:34 kesh ovpn-client[347]: Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Aug  3 10:28:34 kesh ovpn-client[347]: Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Aug  3 10:28:34 kesh ovpn-client[347]: [vpn02] Peer Connection Initiated with [AF_INET]server_ip_address:1194
Aug  3 10:28:36 kesh ovpn-client[347]: SENT CONTROL [vpn02]: 'PUSH_REQUEST' (status=1)
Aug  3 10:28:36 kesh ovpn-client[347]: PUSH: Received control message: 'PUSH_REPLY,route 10.168.12.1 255.255.255.0,redirect-gateway def1 bypass-dhcp,dhcp-option DNS 10.168.12.11,dhcp-option DNS 8.8.8.8,route-gateway dhcp,ping 10,ping-restart 120'
Aug  3 10:28:36 kesh ovpn-client[347]: OPTIONS IMPORT: timers and/or timeouts modified
Aug  3 10:28:36 kesh ovpn-client[347]: OPTIONS IMPORT: route options modified
Aug  3 10:28:36 kesh ovpn-client[347]: OPTIONS IMPORT: route-related options modified
Aug  3 10:28:36 kesh ovpn-client[347]: OPTIONS IMPORT: --ip-win32 and/or --dhcp-option options modified
Aug  3 10:28:36 kesh ovpn-client[347]: ROUTE_GATEWAY 192.168.1.1/255.255.255.0 IFACE=br0 HWADDR=00:50:43:01:0d:5b
Aug  3 10:28:36 kesh systemd-udevd[351]: Could not generate persistent MAC address for tap1: No such file or directory
Aug  3 10:28:36 kesh ovpn-client[347]: OpenVPN ROUTE: OpenVPN needs a gateway parameter for a --route option and no default was specified by either --route-gateway or --ifconfig options
Aug  3 10:28:36 kesh ovpn-client[347]: OpenVPN ROUTE: failed to parse/resolve route for host/network: 10.168.12.1
Aug  3 10:28:36 kesh ovpn-client[347]: TUN/TAP device tap1 opened
Aug  3 10:28:36 kesh ovpn-client[347]: TUN/TAP TX queue length set to 100
Aug  3 10:28:36 kesh ovpn-client[347]: NOTE: unable to redirect default gateway -- VPN gateway parameter (--route-gateway or --ifconfig) is missing
Aug  3 10:28:36 kesh ovpn-client[347]: Initialization Sequence Completed

```

This is the output from the server's syslog:
```

Aug  3 15:28:33 vpn02 ovpn-server[1758]: client_ip_address:1194 TLS: Initial packet from [AF_INET]client_ip_address:1194, sid=81e30849 e07df5f2
Aug  3 15:28:33 vpn02 ovpn-server[1758]: client_ip_address:1194 VERIFY OK: depth=1, C=US, ST=MN, L=City, O=Dept IT, OU=Dept, CN=Dept IT CA, name=Name, emailAddress=admin@home.local
Aug  3 15:28:33 vpn02 ovpn-server[1758]: client_ip_address:1194 VERIFY OK: depth=0, C=US, ST=MN, L=City, O=Dept IT, OU=Dept, CN=kesh, name=Name, emailAddress=admin@home.local
Aug  3 15:28:34 vpn02 ovpn-server[1758]: client_ip_address:1194 Data Channel Encrypt: Cipher 'BF-CBC' initialized with 128 bit key
Aug  3 15:28:34 vpn02 ovpn-server[1758]: client_ip_address:1194 Data Channel Encrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Aug  3 15:28:34 vpn02 ovpn-server[1758]: client_ip_address:1194 Data Channel Decrypt: Cipher 'BF-CBC' initialized with 128 bit key
Aug  3 15:28:34 vpn02 ovpn-server[1758]: client_ip_address:1194 Data Channel Decrypt: Using 160 bit message hash 'SHA1' for HMAC authentication
Aug  3 15:28:34 vpn02 ovpn-server[1758]: client_ip_address:1194 Control Channel: TLSv1, cipher TLSv1/SSLv3 DHE-RSA-AES256-SHA, 2048 bit RSA
Aug  3 15:28:34 vpn02 ovpn-server[1758]: client_ip_address:1194 [kesh] Peer Connection Initiated with [AF_INET]client_ip_address:1194
Aug  3 15:28:34 vpn02 ovpn-server[1758]: MULTI: new connection by client 'kesh' will cause previous active sessions by this client to be dropped.  Remember to use the --duplicate-cn option if you want multiple clients using the same certificate or username to concurrently connect.
Aug  3 15:28:34 vpn02 ovpn-server[1758]: MULTI: no dynamic or static remote --ifconfig address is available for kesh/client_ip_address:1194
Aug  3 15:28:36 vpn02 ovpn-server[1758]: kesh/client_ip_address:1194 PUSH: Received control message: 'PUSH_REQUEST'
Aug  3 15:28:36 vpn02 ovpn-server[1758]: kesh/client_ip_address:1194 send_push_reply(): safe_cap=940
Aug  3 15:28:36 vpn02 ovpn-server[1758]: kesh/client_ip_address:1194 SENT CONTROL [kesh]: 'PUSH_REPLY,route 10.168.12.1 255.255.255.0,redirect-gateway def1 bypass-dhcp,dhcp-option DNS 10.168.12.11,dhcp-option DNS 8.8.8.8,route-gateway dhcp,ping 10,ping-restart 120' (status=1)

```

This is the client config file:
```

client
remote my_vpn_server
port 1194
proto udp
dev tap
dev-type tap
ns-cert-type server
reneg-sec 86400
comp-lzo yes
verb 3
ca /etc/openvpn/ca.crt
cert /etc/openvpn/kesh.crt
key /etc/openvpn/kesh.key

```

This is a working Windows config file connecting to the same vpn server:
```

client
remote my_vpn_server
port 1194
proto udp
dev tap
dev-type tap
ns-cert-type server
reneg-sec 86400
comp-lzo yes
verb 3
ca ca.crt
cert "C:\\Users\\me\\My Documents\\openvpn\\yoga2.crt"
key "C:\\Users\\me\\My Documents\\openvpn\\yoga2.key"
; Set the name of the Windows TAP network interface device here
dev-node "Ethernet 7"

```

This is the server config:
```

port 1194
proto udp
dev tap0
ca ca.crt
cert vpn02.crt
key vpn02.key  # This file should be kept secret
dh dh2048.pem
server-bridge
push "route 10.168.12.1 255.255.255.0"
push "redirect-gateway def1 bypass-dhcp"
push "dhcp-option DNS 10.168.12.11"
push "dhcp-option DNS 8.8.8.8"
keepalive 10 120
comp-lzo
user nobody
group nogroup
persist-key
persist-tun
status openvpn-status.log
verb 3
up "/etc/openvpn/up.sh br0"
down "/etc/openvpn/down.sh br0"
script-security 3

```

---

### Post by jarush on 2016-08-03
I can set the IP address manually on tap1, so i'm guessing this something wrong in the client.conf

```

ifconfig tap1 10.168.12.253 netmask 255.255.255.0 broadcast 10.168.12.255

```

---

