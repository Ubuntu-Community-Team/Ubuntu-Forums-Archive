---
title: "[OpenVPN - Network Manager] Route only specific routes"
date: 2019-08-19
forum: Networking &amp; Wireless
---

### Post by ronnie.vd.c2 on 2019-08-19
I want to connect with my own VPN server for only a subset of routes (not all traffic).
This is possible when i connect with the openvpn commandline **$ sudo openvpn client.ovpn** and only the routes 192.168.1.0 and 192.168.255.0 are tunneled over VPN.
But when i import the same client.ovpn in Network Manager, ALL traffic is tunneled.

Question:
**How can i configure Network Manager to tunnel only 192.168.1.0 and 192.168.255.0?**

Ubuntu version
```
lsb_release -a
LSB Version:    core-9.20170808ubuntu1-noarch:printing-9.20170808ubuntu1-noarch:security-9.20170808ubuntu1-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.3 LTS
Release:    18.04
Codename:    bionic
```

Openvpn client version
```
openvpn --version
OpenVPN 2.4.4 x86_64-pc-linux-gnu [SSL (OpenSSL)] [LZO] [LZ4] [EPOLL] [PKCS11] [MH/PKTINFO] [AEAD] built on May 14 2019
library versions: OpenSSL 1.1.1  11 Sep 2018, LZO 2.08
Originally developed by James Yonan
Copyright (C) 2002-2017 OpenVPN Technologies, Inc. <sales@openvpn.net>
Compile time defines: enable_async_push=no enable_comp_stub=no enable_crypto=yes enable_crypto_ofb_cfb=yes enable_debug=yes enable_def_auth=yes enable_dependency_tracking=no enable_dlopen=unknown enable_dlopen_self=unknown enable_dlopen_self_static=unknown enable_fast_install=needless enable_fragment=yes enable_iproute2=yes enable_libtool_lock=yes enable_lz4=yes enable_lzo=yes enable_maintainer_mode=no enable_management=yes enable_multihome=yes enable_pam_dlopen=no enable_pedantic=no enable_pf=yes enable_pkcs11=yes enable_plugin_auth_pam=yes enable_plugin_down_root=yes enable_plugins=yes enable_port_share=yes enable_selinux=no enable_server=yes enable_shared=yes enable_shared_with_static_runtimes=no enable_silent_rules=no enable_small=no enable_static=yes enable_strict=no enable_strict_options=no enable_systemd=yes enable_werror=no enable_win32_dll=yes enable_x509_alt_username=yes with_aix_soname=aix with_crypto_library=openssl with_gnu_ld=yes with_mem_check=no with_sysroot=no
```

Server configuration (openvpn.conf)
```
port 443
proto tcp
dev tun

key             /etc/openvpn/pki/private/my.domain.tld.key
ca              /etc/openvpn/pki/ca.crt
cert            /etc/openvpn/pki/issued/my.domain.tld.crt
dh              /etc/openvpn/pki/dh.pem
tls-auth        /etc/openvpn/pki/ta.key 0

server 192.168.255.0 255.255.255.0
ifconfig-pool-persist ipp.txt

push "block-outside-dns"
push "dhcp-option DNS 8.8.8.8"
push "dhcp-option DNS 8.8.4.4"
push "route 192.168.1.0 255.255.255.0"
# push "redirect-gateway def1 bypass-dhcp"

client-to-client
duplicate-cn
keepalive 10 60

cipher AES-256-CBC
comp-lzo
max-clients 10
user nobody
group nogroup
persist-key
persist-tun
status /tmp/openvpn-status.log
verb 3

#fragment 1400
mssfix
```

Client configuration: client.ovpn
```
client
dev                     tun
proto                   tcp
remote                  my.domain.tld 443
connect-retry-max       5
connect-retry           5
resolv-retry            60
nobind
persist-key
persist-tun
key-direction           1
cipher                  AES-256-CBC
comp-lzo
verb                    1
mute                    5

# config options below, override the server options (e.g. everything through vpn)
route                   192.168.1.0   255.255.255.0
route                   192.168.255.0 255.255.255.0
route-nopull

<key>
...
</key>
<cert>
...
</cert>
<ca>
...
</ca>
<tls-auth>
...
</tls-auth>
```

IP Route when
1. Not connected trough VPN
```
ip route
default via 192.168.178.1 dev wlp2s0 proto static metric 600
62.148.177.160 via 192.168.178.1 dev wlp2s0 proto static metric 600
169.254.0.0/16 dev wlp2s0 scope link metric 1000
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown
172.18.0.0/16 dev br-07094665e3e1 proto kernel scope link src 172.18.0.1 linkdown
192.168.178.0/24 dev wlp2s0 proto kernel scope link src 192.168.178.2 metric 600
192.168.178.1 dev wlp2s0 proto static scope link metric 600
```

2. Connected with commandline
```
ip route
default via 192.168.178.1 dev wlp2s0 proto static metric 600
62.148.177.160 via 192.168.178.1 dev wlp2s0 proto static metric 600
169.254.0.0/16 dev wlp2s0 scope link metric 1000
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown
172.18.0.0/16 dev br-07094665e3e1 proto kernel scope link src 172.18.0.1 linkdown
192.168.1.0/24 via 192.168.255.5 dev tun0
192.168.178.0/24 dev wlp2s0 proto kernel scope link src 192.168.178.2 metric 600
192.168.178.1 dev wlp2s0 proto static scope link metric 600
192.168.255.0/24 via 192.168.255.5 dev tun0
192.168.255.5 dev tun0 proto kernel scope link src 192.168.255.6
```

3. Connected with network manager
```
ip route
default via 192.168.255.5 dev tun0 proto static metric 50
default via 192.168.178.1 dev wlp2s0 proto static metric 600
62.148.177.160 via 192.168.178.1 dev wlp2s0 proto static metric 600
169.254.0.0/16 dev wlp2s0 scope link metric 1000
172.17.0.0/16 dev docker0 proto kernel scope link src 172.17.0.1 linkdown
172.18.0.0/16 dev br-07094665e3e1 proto kernel scope link src 172.18.0.1 linkdown
192.168.1.0/24 dev tun0 proto static scope link metric 50
192.168.1.0/24 via 192.168.255.5 dev tun0 proto static metric 50
192.168.178.0/24 dev wlp2s0 proto kernel scope link src 192.168.178.2 metric 600
192.168.178.1 dev wlp2s0 proto static scope link metric 600
192.168.255.0/24 dev tun0 proto static scope link metric 50
192.168.255.0/24 via 192.168.255.5 dev tun0 proto static metric 50
192.168.255.5 dev tun0 proto kernel scope link src 192.168.255.6 metric 50
```

Kernel IP routing table when 
1. Not connected trough VPN
```
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG        0 0          0 wlp2s0
62.148.177.160  192.168.178.1   255.255.255.255 UGH       0 0          0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlp2s0
172.17.0.0      0.0.0.0         255.255.0.0     U         0 0          0 docker0
172.18.0.0      0.0.0.0         255.255.0.0     U         0 0          0 br-07094665e3e1
192.168.178.0   0.0.0.0         255.255.255.0   U         0 0          0 wlp2s0
192.168.178.1   0.0.0.0         255.255.255.255 UH        0 0          0 wlp2s0
```

2. Connected with commandline
```
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.178.1   0.0.0.0         UG        0 0          0 wlp2s0
62.148.177.160  192.168.178.1   255.255.255.255 UGH       0 0          0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlp2s0
172.17.0.0      0.0.0.0         255.255.0.0     U         0 0          0 docker0
172.18.0.0      0.0.0.0         255.255.0.0     U         0 0          0 br-07094665e3e1
192.168.1.0     192.168.255.5   255.255.255.0   UG        0 0          0 tun0
192.168.178.0   0.0.0.0         255.255.255.0   U         0 0          0 wlp2s0
192.168.178.1   0.0.0.0         255.255.255.255 UH        0 0          0 wlp2s0
192.168.255.0   192.168.255.5   255.255.255.0   UG        0 0          0 tun0
192.168.255.5   0.0.0.0         255.255.255.255 UH        0 0          0 tun0
```

3. Connected with network-manager
```
netstat -rn
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
0.0.0.0         192.168.255.5   0.0.0.0         UG        0 0          0 tun0
0.0.0.0         192.168.178.1   0.0.0.0         UG        0 0          0 wlp2s0
62.148.177.160  192.168.178.1   255.255.255.255 UGH       0 0          0 wlp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U         0 0          0 wlp2s0
172.17.0.0      0.0.0.0         255.255.0.0     U         0 0          0 docker0
172.18.0.0      0.0.0.0         255.255.0.0     U         0 0          0 br-07094665e3e1
192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 tun0
192.168.1.0     192.168.255.5   255.255.255.0   UG        0 0          0 tun0
192.168.178.0   0.0.0.0         255.255.255.0   U         0 0          0 wlp2s0
192.168.178.1   0.0.0.0         255.255.255.255 UH        0 0          0 wlp2s0
192.168.255.0   0.0.0.0         255.255.255.0   U         0 0          0 tun0
192.168.255.0   192.168.255.5   255.255.255.0   UG        0 0          0 tun0
192.168.255.5   0.0.0.0         255.255.255.255 UH        0 0          0 tun0
```

---

