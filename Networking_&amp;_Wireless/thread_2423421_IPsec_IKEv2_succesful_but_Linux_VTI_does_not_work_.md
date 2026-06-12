---
title: "IPsec IKEv2 succesful but Linux VTI does not work with SNAT"
date: 2019-07-23
forum: Networking &amp; Wireless
---

### Post by aminkhoshnood on 2019-07-23
Hi everyone.
If you think troubleshooting IPsec is tedious, please forget about my logs and just let me know the implementation process, I'm still confused and any information is helpful.

I removed SPIs and here is my IP map:
```

Our private IP address:
10.1.1.2
Our S-NAT IP address:
172.16.0.1
Our Pubic/EIP address:
1.1.1.1
CheckPoint GW:
2.2.2.2
Instance behind CheckPoint:
192.168.1.1

```
On the leftside I have StrongSWAN on AWS EC2 instance behind its 1:1 NAT and Elastic IP with this configuration:

/etc/ipsec.conf:
```

config setup
    # strictcrlpolicy=yes
    # uniqueids = no
    charondebug="ike 2, knl 2, cfg 2"

conn %default
    keyexchange=ikev2
    ike=aes256-sha256-modp2048
    ikelifetime=86400s
    esp=aes256-sha256-modp2048
    lifetime=10800s
    keyingtries=%forever
    dpddelay=30s
    dpdtimeout=120s
    dpdaction=restart

conn Tunnel1
    auto=start
    left=10.1.1.2 # Our private IP address
    leftsubnet=172.16.0.1/32 # Our S-NAT IP address
    leftauth=psk
    leftid=1.1.1.1 # Our Pubic/EIP address
    right=2.2.2.2 # CheckPoint GW
    rightsubnet=192.168.1.1/32 # Instance behind CheckPoint 
    rightauth=psk
    rightid=2.2.2.2 # CheckPoint GW
    type=tunnel
    compress=no
    mark=42

```

/etc/ipsec.secrets:
```

1.1.1.1 2.2.2.2 : PSK "OURSECRET"

```

/etc/strongswan.d/charon.conf:
```

install_routes = no
install_virtual_ip = no

```
and on the rightside there is a CheckPoint device that is behind a firewall that accepts policy only if the source of the packet is 172.16.0.1/32 and its destination is 192.168.1.1/32.

But I don't have that IP on my interface and it's a pseudo IP to hide our private range from the rightside (CheckPoint).

This instance should act as a router and pass traffic from other instances through IPsec tunnel but every packet should be SNATed to 172.16.0.1/32.

I start StongSWAN:
```

systemctl start strongswan && systemctl status -l strongswan

```
```

Loaded: loaded (/lib/systemd/system/strongswan.service; disabled; vendor preset: enabled)
   Active: active (running) since Tue 2019-07-23 10:20:22 EEST; 12s ago
  Process: 2163 ExecStart=/usr/sbin/ipsec start (code=exited, status=0/SUCCESS)
  Process: 2160 ExecStartPre=/bin/mkdir -p /var/lock/subsys (code=exited, status=0/SUCCESS)
 Main PID: 2190 (starter)
    Tasks: 18
   Memory: 12.2M
      CPU: 54ms
   CGroup: /system.slice/strongswan.service
           &#9500;&#9472;2190 /usr/lib/ipsec/starter --daemon charon
           &#9492;&#9472;2191 /usr/lib/ipsec/charon --use-syslog --debug-ike 2 --debug-knl 2 --debug-cfg 2

```
Configure iptables:
```

iptables --append INPUT -s 2.2.2.2 -j ACCEPT
iptables --append INPUT -d 2.2.2.2 -j ACCEPT
iptables --table mangle --append FORWARD -o Tunnel1 -p tcp --tcp-flags SYN,RST SYN -j TCPMSS --clamp-mss-to-pmtu

```
Check IKEv2 is successful:
ipsec statusall
```

Status of IKE charon daemon (strongSwan 5.3.5, Linux 4.4.0-1087-aws, x86_64):
  uptime: 79 seconds, since Jul 23 10:20:22 2019
  malloc: sbrk 1646592, mmap 0, used 568016, free 1078576
  worker threads: 11 of 16 idle, 5/0/0/0 working, job queue: 0/0/0/0, scheduled: 4
  loaded plugins: charon test-vectors aes rc2 sha1 sha2 md4 md5 random nonce x509 revocation constraints pubkey pkcs1 pkcs7 pkcs8 pkcs12 pgp dnskey sshkey pem openssl fips-prf gmp agent xcbc hmac gcm attr kernel-netlink resolve socket-default connmark farp stroke updown eap-identity eap-sim eap-sim-pcsc eap-aka eap-aka-3gpp2 eap-simaka-pseudonym eap-simaka-reauth eap-md5 eap-gtc eap-mschapv2 eap-dynamic eap-radius eap-tls eap-ttls eap-peap eap-tnc xauth-generic xauth-eap xauth-pam xauth-noauth tnc-tnccs tnccs-20 tnccs-11 tnccs-dynamic dhcp lookip error-notify certexpire led addrblock unity
Listening IP addresses:
  10.1.1.2
Connections:
     Tunnel1:  10.1.1.2...2.2.2.2  IKEv2, dpddelay=30s
     Tunnel1:   local:  [1.1.1.1] uses pre-shared key authentication
     Tunnel1:   remote: [2.2.2.2] uses pre-shared key authentication
     Tunnel1:   child:  172.16.0.1/32 === 192.168.1.1/32 TUNNEL, dpdaction=restart
Security Associations (1 up, 0 connecting):
     Tunnel1[1]: ESTABLISHED 79 seconds ago, 10.1.1.2[1.1.1.1]...2.2.2.2[2.2.2.2]
     Tunnel1[1]: IKEv2 SPIs: ##**REMOVED**##* ##**REMOVED**##, pre-shared key reauthentication in 23 hours
     Tunnel1[1]: IKE proposal: AES_CBC_256/HMAC_SHA2_256_128/PRF_HMAC_SHA2_256/MODP_2048
     Tunnel1{1}:  INSTALLED, TUNNEL, reqid 1, ESP in UDP SPIs: c05ce72f_i 35f8fdaa_o
     Tunnel1{1}:  AES_CBC_256/HMAC_SHA2_256_128, 0 bytes_i, 0 bytes_o, rekeying in 2 hours
     Tunnel1{1}:   172.16.0.1/32 === 192.168.1.1/32

```
Check if XFRM policies has been added:
ip -s -s xfrm policy:
```

src 192.168.1.1/32 dst 172.16.0.1/32 uid 0
    dir fwd action allow index 82 priority 2819 share any flag  (0x00000000)
    lifetime config:
      limit: soft (INF)(bytes), hard (INF)(bytes)
      limit: soft (INF)(packets), hard (INF)(packets)
      expire add: soft 0(sec), hard 0(sec)
      expire use: soft 0(sec), hard 0(sec)
    lifetime current:
      0(bytes), 0(packets)
      add 2019-07-23 10:20:22 use -
    mark 0x2a/0xffffffff
    tmpl src 2.2.2.2 dst 10.1.1.2
        proto esp spi 0x00000000(0) reqid 1(0x00000001) mode tunnel
        level required share any
        enc-mask ffffffff auth-mask ffffffff comp-mask ffffffff
src 192.168.1.1/32 dst 172.16.0.1/32 uid 0
    dir in action allow index 72 priority 2819 share any flag  (0x00000000)
    lifetime config:
      limit: soft (INF)(bytes), hard (INF)(bytes)
      limit: soft (INF)(packets), hard (INF)(packets)
      expire add: soft 0(sec), hard 0(sec)
      expire use: soft 0(sec), hard 0(sec)
    lifetime current:
      0(bytes), 0(packets)
      add 2019-07-23 10:20:22 use -
    mark 0x2a/0xffffffff
    tmpl src 2.2.2.2 dst 10.1.1.2
        proto esp spi 0x00000000(0) reqid 1(0x00000001) mode tunnel
        level required share any
        enc-mask ffffffff auth-mask ffffffff comp-mask ffffffff
src 172.16.0.1/32 dst 192.168.1.1/32 uid 0
    dir out action allow index 65 priority 2819 share any flag  (0x00000000)
    lifetime config:
      limit: soft (INF)(bytes), hard (INF)(bytes)
      limit: soft (INF)(packets), hard (INF)(packets)
      expire add: soft 0(sec), hard 0(sec)
      expire use: soft 0(sec), hard 0(sec)
    lifetime current:
      0(bytes), 0(packets)
      add 2019-07-23 10:20:22 use -
    mark 0x2a/0xffffffff
    tmpl src 10.1.1.2 dst 2.2.2.2
        proto esp spi 0x00000000(0) reqid 1(0x00000001) mode tunnel
        level required share any
        enc-mask ffffffff auth-mask ffffffff comp-mask ffffffff

```
ip -s -s xfrm state:
```

src 10.1.1.2 dst 2.2.2.2
    proto esp spi ##**REMOVED**##(##**REMOVED**##) reqid 1(0x00000001) mode tunnel
    replay-window 32 seq 0x00000000 flag af-unspec (0x00100000)
    mark 0x2a/0xffffffff
    auth-trunc hmac(sha256) ##**REMOVED**## (256 bits) 128
    enc cbc(aes) ##**REMOVED**## (256 bits)
    encap type espinudp sport 4500 dport 4500 addr 0.0.0.0
    anti-replay context: seq 0x0, oseq 0x0, bitmap 0x00000000
    lifetime config:
      limit: soft (INF)(bytes), hard (INF)(bytes)
      limit: soft (INF)(packets), hard (INF)(packets)
      expire add: soft 9745(sec), hard 10800(sec)
      expire use: soft 0(sec), hard 0(sec)
    lifetime current:
      0(bytes), 0(packets)
      add 2019-07-23 10:20:22 use -
    stats:
      replay-window 0 replay 0 failed 0
src 2.2.2.2 dst 10.1.1.2
    proto esp spi ##**REMOVED**##(##**REMOVED**##) reqid 1(0x00000001) mode tunnel
    replay-window 32 seq 0x00000000 flag af-unspec (0x00100000)
    mark 0x2a/0xffffffff
    auth-trunc hmac(sha256) ##**REMOVED**## (256 bits) 128
    enc cbc(aes) ##**REMOVED**## (256 bits)
    encap type espinudp sport 4500 dport 4500 addr 0.0.0.0
    anti-replay context: seq 0x0, oseq 0x0, bitmap 0x00000000
    lifetime config:
      limit: soft (INF)(bytes), hard (INF)(bytes)
      limit: soft (INF)(packets), hard (INF)(packets)
      expire add: soft 10057(sec), hard 10800(sec)
      expire use: soft 0(sec), hard 0(sec)
    lifetime current:
      0(bytes), 0(packets)
      add 2019-07-23 10:20:22 use -
    stats:
      replay-window 0 replay 0 failed 0

```
Create VTI device:
```

ip tunnel add Tunnel1 local 10.1.1.2 remote 2.2.2.2 mode vti key 42
ip addr add 172.16.0.1/32 remote 192.168.1.1/32 dev Tunnel1
ip link set Tunnel1 up mtu 1419

```
Disable policy on tunnel and adding iptables TCPMSS:
```

sysctl -w net.ipv4.conf.Tunnel1.disable_policy=1
iptables --table mangle --append FORWARD -m policy --pol ipsec --dir in -p tcp -m tcp --tcp-flags SYN,RST SYN -m tcpmss --mss 1361:1536 -j TCPMSS --set-mss 1360
iptables --table mangle --append FORWARD -m policy --pol ipsec --dir out -p tcp -m tcp --tcp-flags SYN,RST SYN -m tcpmss --mss 1361:1536 -j TCPMSS --set-mss 1360

```
but when I ping 192.168.1.1 with source 172.16.0.1, I get Destination Host Unreachable.
```

ping 192.168.1.1 OR ping -I 172.16.0.1 192.168.1.1 OR ping -I Tunnel1 192.168.1.1

```
```

ping -c 3 -I 172.16.0.1 192.168.1.1
PING 192.168.1.1 (192.168.1.1) from 172.16.0.1 Tunnel1: 56(84) bytes of data.
From 172.16.0.1 icmp_seq=1 Destination Host Unreachable
From 172.16.0.1 icmp_seq=2 Destination Host Unreachable
From 172.16.0.1 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 0 received, +3 errors, 100% packet loss, time 1998ms

```
here are some other logs:
ip address show:
```

3: ip_vti0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN group default qlen 1
    link/ipip 0.0.0.0 brd 0.0.0.0
4: Tunnel1@NONE: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1419 qdisc noqueue state UNKNOWN group default qlen 1
    link/ipip 10.1.1.2 peer 2.2.2.2
    inet 172.16.0.1 peer 192.168.1.1/32 scope global Tunnel1
       valid_lft forever preferred_lft forever

```
ip -s -s link show:
```

3: ip_vti0@NONE: <NOARP> mtu 1480 qdisc noop state DOWN mode DEFAULT group default qlen 1
    link/ipip 0.0.0.0 brd 0.0.0.0
    RX: bytes  packets  errors  dropped overrun mcast
    0          0        0       0       0       0
    RX errors: length   crc     frame   fifo    missed
               0        0       0       0       0
    TX: bytes  packets  errors  dropped carrier collsns
    0          0        0       0       0       0
    TX errors: aborted  fifo   window heartbeat transns
               0        0       0       0       0
4: Tunnel1@NONE: <POINTOPOINT,NOARP,UP,LOWER_UP> mtu 1419 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1
    link/ipip 10.1.1.2 peer 2.2.2.2
    RX: bytes  packets  errors  dropped overrun mcast
    0          0        0       0       0       0
    RX errors: length   crc     frame   fifo    missed
               0        0       0       0       0
    TX: bytes  packets  errors  dropped carrier collsns
    0          0        14      0       14      0
    TX errors: aborted  fifo   window heartbeat transns
               0        0       0       0       0

```
ip -s tunnel show Tunnel1:
```

Tunnel1: ip/ip  remote 2.2.2.2  local 10.1.1.2  ttl inherit  key 42
RX: Packets    Bytes        Errors CsumErrs OutOfSeq Mcasts
    0          0            0      0        0        0
TX: Packets    Bytes        Errors DeadLoop NoRoute  NoBufs
    0          0            14     0        14       0

```
ifconfig -a:
```

Tunnel1   Link encap:IPIP Tunnel  HWaddr
          inet addr:172.16.0.1  P-t-P:192.168.1.1  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP  MTU:1419  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:14 dropped:0 overruns:0 carrier:14
          collisions:0 txqueuelen:1
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
ip_vti0   Link encap:IPIP Tunnel  HWaddr
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```
I disabled source and destination check on AWS EC2 and I whitelisted the rightside (Checkpoint) IP addess for all traffic in AWS security groups, I'm sure NAT-Traversal is supported and I can see it's traffic with tcpdump:
tcpdump -i any -nnnNq host 2.2.2.2
```

10:32:02.983136 IP 10.1.1.2.500 > 2.2.2.2.500: UDP, length 1084
10:32:03.035572 IP 2.2.2.2.500 > 10.1.1.2.500: UDP, length 708
10:32:03.044827 IP 10.1.1.2.4500 > 2.2.2.2.4500: UDP, length 372
10:32:03.108335 IP 2.2.2.2.4500 > 10.1.1.2.4500: UDP, length 276
10:32:27.042735 IP 10.1.1.2.4500 > 2.2.2.2.4500: UDP, length 1
10:32:33.110661 IP 10.1.1.2.4500 > 2.2.2.2.4500: UDP, length 84
10:32:33.159623 IP 2.2.2.2.4500 > 10.1.1.2.4500: UDP, length 84
10:32:57.043342 IP 10.1.1.2.4500 > 2.2.2.2.4500: UDP, length 1
10:33:03.110977 IP 10.1.1.2.4500 > 2.2.2.2.4500: UDP, length 84

```
CheckPoint shows the tunnel has been established but I don't get any tcpdump when I send ping packets.
journalctl -fu strongswan is available from here:

[https://pastebin.com/AuephC04](https://pastebin.com/AuephC04)

I tried VTI endpoint this way too but it did not make any changes:
```

ip tunnel add Tunnel1 local 10.1.1.2 remote 2.2.2.2 mode vti key 42
ip addr add 172.16.0.1/32 remote 0.0.0.0/0 dev Tunnel1
ip link set Tunnel1 up mtu 1419

```

Am I implementing this structure correctly? Should I set the pseudo IP on the VTI device? Should I add another iptables rule to apply MARK something like this?
```

iptables -t mangle -A INPUT -p esp -s 2.2.2.2 -d 1.1.1.1 -j MARK --set-xmark 42

```
Versions:

ipsec --version:
```

Linux strongSwan U5.3.5/K4.4.0-1087-aws

```
lsb_release -a:
```

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.6 LTS
Release:    16.04
Codename:    xenial

```
dpkg -l | grep -i strongswan:
```

ii  libcharon-extra-plugins          5.3.5-1ubuntu3.8                           amd64        strongSwan charon library (extra plugins)
ii  libstrongswan                    5.3.5-1ubuntu3.8                           amd64        strongSwan utility and crypto library
ii  libstrongswan-standard-plugins   5.3.5-1ubuntu3.8                           amd64        strongSwan utility and crypto library (standard plugins)
ii  strongswan                       5.3.5-1ubuntu3.8                           all          IPsec VPN solution metapackage
ii  strongswan-charon                5.3.5-1ubuntu3.8                           amd64        strongSwan Internet Key Exchange daemon
ii  strongswan-libcharon             5.3.5-1ubuntu3.8                           amd64        strongSwan charon library
ii  strongswan-starter               5.3.5-1ubuntu3.8                           amd64        strongSwan daemon starter and configuration file parser
ii  strongswan-tnc-base              5.3.5-1ubuntu3.8                           amd64        strongSwan Trusted Network Connect's (TNC) - base files

```
Thanks in advance for your help.

---

