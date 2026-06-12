---
title: "Ubuntu 17.10 IPSec VPN traffic route problem"
date: 2018-09-04
forum: Networking &amp; Wireless
---

### Post by pstef on 2018-09-04
Hello everyone
I have a scheme

VPS(172.16.1.4) -- VPS Gate(External IP Gate) --- CiscoASA(External IP ASA) -- MyNet (192.168.126.0/24)

I want to route some trafick from MyNet to VPS through IPSec tunnel, and reach internet through VPS.

For first step (for test) I created Loopback 1 interface on VPS and I trying to reach Loopback 1 from MyNet. But I have no connectivity

I used [http://resources.intenseschool.com/ipsec-site-to-site-vpn-between-cisco-asa-and-ubuntu-14-04/](http://resources.intenseschool.com/ipsec-site-to-site-vpn-between-cisco-asa-and-ubuntu-14-04/)

If I do ping From MyNet to Lo1

```
@Ekahau-Gate:~$ **sudo tcpdump -i ip_vti0 -Q inout**
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on ip_vti0, link-type RAW (Raw IP), capture size 262144 bytes
15:53:53.461242 IP 192.168.126.17 > Ekahau-Gate: ICMP echo request, id 1, seq 3246, length 40
15:53:58.452572 IP 192.168.126.17 > Ekahau-Gate: ICMP echo request, id@Ekahau-Gate:~$ **sudo tcpdump -i ip_vti0 -Q inout**
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on ip_vti0, link-type RAW (Raw IP), capture size 262144 bytes
15:53:53.461242 IP 192.168.126.17 > Ekahau-Gate: ICMP echo request, id 1, seq 3246, length 40
15:53:58.452572 IP 192.168.126.17 > Ekahau-Gate: ICMP echo request, id 1, seq 3247, length 40
15:54:03.461346 IP 192.168.126.17 > Ekahau-Gate: ICMP echo request, id 1, seq 3248, length 40
15:54:08.452417 IP 192.168.126.17 > Ekahau-Gate: ICMP echo request, id 1, seq 3249, length 40
```

```
@Ekahau-Gate:~$ **tail /var/log/syslog**
Sep  4 15:53:38 Ekahau-Gate kernel: [22334.295860] ***IMPUT Ping detected***: IN=ip_vti0 OUT= MAC=00:0d:3a:b4:ce:6d:12:34:56:78:9a:bc:08:00:45:00:00:3c:19:18:00:00:7f:01:6a:11:c0:a8:7e:11:0a:6f:6f:6f:08:00:40:b0:00:01:0c:ab:61:62:63:64:65:66:67:68:69:6a:6b:6c:6d:6e:6f:70:71:72:73:74:75:76:77:61:62:63:64:65:66:67:68:69:01:02:02:04:66:08:3a:21:f9:8d:d8:05:7d:d8:75:e6:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:01:00:00:00:6a:d0:aa:5a:0c:16:80:10:20:13:cd:2c:00:00:01:01:08:0a:9f:6e:a6:09:f0:2a:00:00:00:00:00:00:00:00 SRC=192.168.126.17 DST=10.111.111.111 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=6424 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=3243
Sep  4 15:53:43 Ekahau-Gate kernel: [22339.303340] ***IMPUT Ping detected***: IN=ip_vti0 OUT= MAC=00:0d:3a:b4:ce:6d:12:34:56:78:9a:bc:08:00:45:00:00:3c:19:19:00:00:7f:01:6a:10:c0:a8:7e:11:0a:6f:6f:6f:08:00:40:af:00:01:0c:ac:61:62:63:64:65:66:67:68:69:6a:6b:6c:6d:6e:6f:70:71:72:73:74:75:76:77:61:62:63:64:65:66:67:68:69:01:02:02:04:f4:64:00:15:2f:f6:fd:5d:72:bd:83:4d:b8:82:b3:6c:2a:f9:4f:ff:ea:ff:1c:21:08:a2:be:f4:b4:45:f2:80:a8:f1:c3:88:70:20:32:30:31:38:20:31:35:3a:35:33:3a:31:30:20:47:4d:54:0d:0a:43:6f:6e:6e:65:00:00:00:00:00:00:00:00 SRC=192.168.126.17 DST=10.111.111.111 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=6425 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=3244
Sep  4 15:53:48 Ekahau-Gate kernel: [22344.295567] IMPUT Ping detected: IN=ip_vti0 OUT= 
```

If I do ping From Lo1 to MyNet 

```
@Ekahau-Gate:~$ **ping 192.168.127.17**
PING 192.168.127.17 (192.168.127.17) 56(84) bytes of data.
^C
--- 192.168.127.17 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9212ms
```

```
@Ekahau-Gate:~$ **sudo tcpdump -i ip_vti0 -Q inout *- NO packets***

```
```
@Ekahau-Gate:~$ **tail /var/log/syslog**
Sep  4 15:57:29 Ekahau-Gate kernel: [22564.928066] ***OUTPUD Ping detected***: IN= OUT=eth0 SRC=172.16.1.4 DST=192.168.127.17 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=236 DF PROTO=ICMP TYPE=8 CODE=0 ID=37042 SEQ=2
Sep  4 15:57:30 Ekahau-Gate kernel: [22565.952110] [B][I]OUTPUD Ping  1, seq 3247, length 40
15:54:03.461346 IP 192.168.126.17 > Ekahau-Gate: ICMP echo request, id 1, seq 3248, length 40
15:54:08.452417 IP 192.168.126.17 > Ekahau-Gate: ICMP echo request, id 1, seq 3249, length 40
```

```
@Ekahau-Gate:~$ **tail /var/log/syslog**
Sep  4 15:53:38 Ekahau-Gate kernel: [22334.295860] ***IMPUT Ping detected***: IN=ip_vti0 OUT= MAC=00:0d:3a:b4:ce:6d:12:34:56:78:9a:bc:08:00:45:00:00:3c:19:18:00:00:7f:01:6a:11:c0:a8:7e:11:0a:6f:6f:6f:08:00:40:b0:00:01:0c:ab:61:62:63:64:65:66:67:68:69:6a:6b:6c:6d:6e:6f:70:71:72:73:74:75:76:77:61:62:63:64:65:66:67:68:69:01:02:02:04:66:08:3a:21:f9:8d:d8:05:7d:d8:75:e6:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:00:01:00:00:00:6a:d0:aa:5a:0c:16:80:10:20:13:cd:2c:00:00:01:01:08:0a:9f:6e:a6:09:f0:2a:00:00:00:00:00:00:00:00 SRC=192.168.126.17 DST=10.111.111.111 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=6424 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=3243
Sep  4 15:53:43 Ekahau-Gate kernel: [22339.303340] ***IMPUT Ping detected***: IN=ip_vti0 OUT= MAC=00:0d:3a:b4:ce:6d:12:34:56:78:9a:bc:08:00:45:00:00:3c:19:19:00:00:7f:01:6a:10:c0:a8:7e:11:0a:6f:6f:6f:08:00:40:af:00:01:0c:ac:61:62:63:64:65:66:67:68:69:6a:6b:6c:6d:6e:6f:70:71:72:73:74:75:76:77:61:62:63:64:65:66:67:68:69:01:02:02:04:f4:64:00:15:2f:f6:fd:5d:72:bd:83:4d:b8:82:b3:6c:2a:f9:4f:ff:ea:ff:1c:21:08:a2:be:f4:b4:45:f2:80:a8:f1:c3:88:70:20:32:30:31:38:20:31:35:3a:35:33:3a:31:30:20:47:4d:54:0d:0a:43:6f:6e:6e:65:00:00:00:00:00:00:00:00 SRC=192.168.126.17 DST=10.111.111.111 LEN=60 TOS=0x00 PREC=0x00 TTL=127 ID=6425 PROTO=ICMP TYPE=8 CODE=0 ID=1 SEQ=3244
Sep  4 15:53:48 Ekahau-Gate kernel: [22344.295567] IMPUT Ping detected: IN=ip_vti0 OUT= 
```

If I do ping From Lo1 to MyNet 

```
@Ekahau-Gate:~$ **ping 192.168.127.17**
PING 192.168.127.17 (192.168.127.17) 56(84) bytes of data.
^C
--- 192.168.127.17 ping statistics ---
10 packets transmitted, 0 received, 100% packet loss, time 9212ms
```

```
@Ekahau-Gate:~$ **sudo tcpdump -i ip_vti0 -Q inout *- NO packets***
```

```
@Ekahau-Gate:~$ **tail /var/log/syslog**
Sep  4 15:57:29 Ekahau-Gate kernel: [22564.928066] ***OUTPUD Ping detected***: IN= OUT=eth0 SRC=172.16.1.4 DST=192.168.127.17 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=236 DF PROTO=ICMP TYPE=8 CODE=0 ID=37042 SEQ=2
Sep  4 15:57:30 Ekahau-Gate kernel: [22565.952110] ***OUTPUD Ping detected***: IN= OUT=eth0 SRC=172.16.1.4 DST=192.168.127.17 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=485 DF PROTO=ICMP TYPE=8 CODE=0 ID=37042 SEQ=3

```

```
@Ekahau-Gate:~$ **ping 192.168.127.17 -I ip_vti0**
ping: Warning: source address might be selected on device other than ip_vti0.
PING 192.168.127.17 (192.168.127.17) from 10.111.111.111 ip_vti0: 56(84) bytes of data.
^C
--- 192.168.127.17 ping statistics ---
19 packets transmitted, 0 received, 100% packet loss, time 18413ms
```

```
@Ekahau-Gate:~$ **sudo tcpdump -i ip_vti0 -Q inout**
tcpdump: verbose output suppressed, use -v or -vv for full protocol decode
listening on ip_vti0, link-type RAW (Raw IP), capture size 262144 bytes
16:00:02.301453 IP Ekahau-Gate > 192.168.127.17: ICMP echo request, id 37246, seq 8, length 64
16:00:03.325473 IP Ekahau-Gate > 192.168.127.17: ICMP echo request, id 37246, seq 9, length 64
16:00:04.349492 IP Ekahau-Gate > 192.168.127.17: ICMP echo request, id 37246, seq 10, length 64
16:00:05.373408 IP Ekahau-Gate > 192.168.127.17: ICMP echo request, id 37246, seq 11, length 64


```
```
stefanenko@Ekahau-Gate:~$ **tail /var/log/syslog**
Sep  4 16:00:05 Ekahau-Gate kernel: [22721.216093]*** OUTPUD Ping detected***: IN= OUT=ip_vti0 SRC=10.111.111.111 DST=192.168.127.17 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=7622 DF PROTO=ICMP TYPE=8 CODE=0 ID=37246 SEQ=11
Sep  4 16:00:06 Ekahau-Gate kernel: [22722.240095] ***OUTPUD Ping detected***: IN= OUT=ip_vti0 SRC=10.111.111.111 DST=192.168.127.17 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=7792 DF PROTO=ICMP TYPE=8 CODE=0 ID=37246 SEQ=12
Sep  4 16:00:07 Ekahau-Gate kernel: [22723.264086] OUTPUD Ping detected: IN= OUT=ip_vti0 SRC=10.111.111.111 DST=192.168.127.17 LEN=84 TOS=0x00 PREC=0x00 TTL=64 ID=7973 DF PROTO=ICMP TYPE=8 CODE=0 ID=37246 SEQ=13


```
***Please help me to understand what is I do wrong***


**My configs:**

```
@Ekahau-Gate:~$ **sudo uname -a**
Linux Ekahau-Gate 4.13.0-46-generic #51-Ubuntu SMP Tue Jun 12 12:36:29 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```
Openswan
```
@Ekahau-Gate:~$   **cat /etc/ipsec.conf**
version 2.0

config setup
  virtual-private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12
  protostack=auto
  interfaces=%defaultroute
  uniqueids=no
  #nat_traversal=yes
  plutodebug=all
  plutostderrlog=/var/log/pluto.log
  #oe=off

conn ASA
  authby=secret
  auto=start

 ## phase 1 ##
  ike=aes256-sha1;modp1024

  ## phase 2 ##
  phase2alg=aes256-sha1
  pfs=no

  #type=tunnel
  left=172.16.1.4
  leftsourceip=External IP Gate
leftsubnet=10.111.111.111/32
  leftnexthop=%defaultroute

  right=External IP ASA
  rightsubnet=192.168.126.0/24
```

```
@Ekahau-Gate:~$ **sudo cat /etc/ipsec.secrets**
%any %any : PSK "Hf...<PSK>"


```
```
@Ekahau-Gate:~$ **ifconfig -a**
eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 172.16.1.4  netmask 255.255.255.0  broadcast 172.16.1.255
        inet6 fe80::20d:3aff:feb4:ce6d  prefixlen 64  scopeid 0x20<link>
        ether 00:0d:3a:b4:ce:6d  txqueuelen 1000  (Ethernet)
        RX packets 145251  bytes 42875427 (42.8 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 170182  bytes 37051015 (37.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

ip_vti0: flags=193<UP,RUNNING,NOARP>  mtu 1332
        tunnel   txqueuelen 1000  (IPIP Tunnel)
        RX packets 324  bytes 19440 (19.4 KB)
        **RX errors 2292**  **dropped 2292**  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        **TX errors 169**  dropped 0 overruns 0  **carrier 169**  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 541  bytes 57004 (57.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 541  bytes 57004 (57.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo:1: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 10.111.111.111  netmask 255.255.255.255
        loop  txqueuelen 1000  (Local Loopback)

```
```
@Ekahau-Gate:~$ **ip route**
default via 172.16.1.1 dev eth0 proto dhcp src 172.16.1.4 metric 100
default via 172.16.1.1 dev eth0 proto dhcp metric 100
10.111.111.111 dev lo scope link src 10.111.111.111
172.16.1.0/24 dev eth0 proto kernel scope link src 172.16.1.4
172.16.1.1 dev eth0 proto dhcp scope link src 172.16.1.4 metric 100
192.168.126.0/24 via 172.16.1.1 dev eth0 src <External IP Gate>
192.168.126.17 dev ip_vti0 scope link** - added manually**


```
```
@Ekahau-Gate:~$ **sudo cat /etc/sysctl.conf**

# Added by hwdsl2 VPN script
kernel.msgmnb = 65536
kernel.msgmax = 65536
kernel.shmmax = 68719476736
kernel.shmall = 4294967296

net.ipv4.ip_forward = 1
net.ipv4.conf.all.accept_source_route = 0
net.ipv4.conf.all.accept_redirects = 0
net.ipv4.conf.all.send_redirects = 0
net.ipv4.conf.all.rp_filter = 0
net.ipv4.conf.default.accept_source_route = 0
net.ipv4.conf.default.accept_redirects = 0
net.ipv4.conf.default.send_redirects = 0
net.ipv4.conf.default.rp_filter = 0
net.ipv4.conf.eth0.send_redirects = 0
net.ipv4.conf.eth0.rp_filter = 0

net.core.wmem_max = 12582912
net.core.rmem_max = 12582912
net.ipv4.tcp_rmem = 10240 87380 12582912
net.ipv4.tcp_wmem = 10240 87380 12582912
```


```
@Ekahau-Gate:~$ **sudo ipsec status**
000 using kernel interface: netkey
000 interface lo/lo ::1@500
000 interface lo/lo 127.0.0.1@4500
000 interface lo/lo 127.0.0.1@500
000 interface lo:1/lo:1 10.111.111.111@4500
000 interface lo:1/lo:1 10.111.111.111@500
000 interface eth0/eth0 172.16.1.4@4500
000 interface eth0/eth0 172.16.1.4@500
000
000
000 fips mode=disabled;
000 SElinux=disabled
000 seccomp=unsupported
000
000 config setup options:
000
000 configdir=/etc, configfile=/etc/ipsec.conf, secrets=/etc/ipsec.secrets, ipsecdir=/etc/ipsec.d
000 nssdir=/etc/ipsec.d, dumpdir=/run/pluto/, statsbin=unset
000 sbindir=/usr/local/sbin, libexecdir=/usr/local/libexec/ipsec
000 pluto_version=3.22, pluto_vendorid=OE-Libreswan-3.22
000 nhelpers=-1, uniqueids=no, perpeerlog=no, logappend=yes, logip=yes, shuntlifetime=900s, xfrmlifetime=300s
000 ddos-cookies-threshold=50000, ddos-max-halfopen=25000, ddos-mode=auto
000 ikeport=500, ikebuf=0, msg_errqueue=yes, strictcrlpolicy=no, crlcheckinterval=0, listen=<any>, nflog-all=0
000 ocsp-enable=no, ocsp-strict=no, ocsp-timeout=2, ocsp-uri=<unset>
000 ocsp-trust-name=<unset>
000 ocsp-cache-size=1000, ocsp-cache-min-age=3600, ocsp-cache-max-age=86400, ocsp-method=get
000 secctx-attr-type=32001
000 myid = (none)
000 debug raw+crypt+parsing+emitting+control+lifecycle+kernel+dns+oppo+controlmore+pfkey+nattraversal+x509+dpd+oppoinfo
000
000 nat-traversal=yes, keep-alive=20, nat-ikeport=4500
000 virtual-private (%priv):
000 - allowed subnets: 10.0.0.0/8, 192.168.0.0/16, 172.16.0.0/12
000
000 ESP algorithms supported:
000
000 algorithm ESP encrypt: id=3, name=ESP_3DES, ivlen=8, keysizemin=192, keysizemax=192
000 algorithm ESP encrypt: id=6, name=ESP_CAST, ivlen=8, keysizemin=128, keysizemax=128
000 algorithm ESP encrypt: id=11, name=ESP_NULL, ivlen=0, keysizemin=0, keysizemax=0
000 algorithm ESP encrypt: id=12, name=ESP_AES, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=13, name=ESP_AES_CTR, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=14, name=ESP_AES_CCM_A, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=15, name=ESP_AES_CCM_B, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=16, name=ESP_AES_CCM_C, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=18, name=ESP_AES_GCM_A, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=19, name=ESP_AES_GCM_B, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=20, name=ESP_AES_GCM_C, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=22, name=ESP_CAMELLIA, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=23, name=ESP_NULL_AUTH_AES_GMAC, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=252, name=ESP_SERPENT, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=253, name=ESP_TWOFISH, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm AH/ESP auth: id=1, name=AUTH_ALGORITHM_HMAC_MD5, keysizemin=128, keysizemax=128
000 algorithm AH/ESP auth: id=2, name=AUTH_ALGORITHM_HMAC_SHA1, keysizemin=160, keysizemax=160
000 algorithm AH/ESP auth: id=5, name=AUTH_ALGORITHM_HMAC_SHA2_256, keysizemin=256, keysizemax=256
000 algorithm AH/ESP auth: id=6, name=AUTH_ALGORITHM_HMAC_SHA2_384, keysizemin=384, keysizemax=384
000 algorithm AH/ESP auth: id=7, name=AUTH_ALGORITHM_HMAC_SHA2_512, keysizemin=512, keysizemax=512
000 algorithm AH/ESP auth: id=8, name=AUTH_ALGORITHM_HMAC_RIPEMD, keysizemin=160, keysizemax=160
000 algorithm AH/ESP auth: id=9, name=AUTH_ALGORITHM_AES_XCBC, keysizemin=128, keysizemax=128
000 algorithm AH/ESP auth: id=250, name=AUTH_ALGORITHM_AES_CMAC_96, keysizemin=128, keysizemax=128
000 algorithm AH/ESP auth: id=251, name=AUTH_ALGORITHM_NULL_KAME, keysizemin=0, keysizemax=0
000
000 IKE algorithms supported:
000
000 algorithm IKE encrypt: v1id=5, v1name=OAKLEY_3DES_CBC, v2id=3, v2name=3DES, blocksize=8, keydeflen=192
000 algorithm IKE encrypt: v1id=8, v1name=OAKLEY_CAMELLIA_CBC, v2id=23, v2name=CAMELLIA_CBC, blocksize=16, keydeflen=128
000 algorithm IKE encrypt: v1id=-1, v1name=n/a, v2id=20, v2name=AES_GCM_C, blocksize=16, keydeflen=128
000 algorithm IKE encrypt: v1id=-1, v1name=n/a, v2id=19, v2name=AES_GCM_B, blocksize=16, keydeflen=128
000 algorithm IKE encrypt: v1id=-1, v1name=n/a, v2id=18, v2name=AES_GCM_A, blocksize=16, keydeflen=128
000 algorithm IKE encrypt: v1id=13, v1name=OAKLEY_AES_CTR, v2id=13, v2name=AES_CTR, blocksize=16, keydeflen=128
000 algorithm IKE encrypt: v1id=7, v1name=OAKLEY_AES_CBC, v2id=12, v2name=AES_CBC, blocksize=16, keydeflen=128
000 algorithm IKE encrypt: v1id=65004, v1name=OAKLEY_SERPENT_CBC, v2id=65004, v2name=SERPENT_CBC, blocksize=16, keydeflen=128
000 algorithm IKE encrypt: v1id=65005, v1name=OAKLEY_TWOFISH_CBC, v2id=65005, v2name=TWOFISH_CBC, blocksize=16, keydeflen=128
000 algorithm IKE encrypt: v1id=65289, v1name=OAKLEY_TWOFISH_CBC_SSH, v2id=65289, v2name=TWOFISH_CBC_SSH, blocksize=16, keydeflen=128
000 algorithm IKE hash: id=1, name=OAKLEY_MD5, hashlen=16
000 algorithm IKE hash: id=2, name=OAKLEY_SHA1, hashlen=20
000 algorithm IKE hash: id=4, name=OAKLEY_SHA2_256, hashlen=32
000 algorithm IKE hash: id=5, name=OAKLEY_SHA2_384, hashlen=48
000 algorithm IKE hash: id=6, name=OAKLEY_SHA2_512, hashlen=64
000 algorithm IKE DH Key Exchange: name=MODP1024, bits=1024
000 algorithm IKE DH Key Exchange: name=MODP1536, bits=1536
000 algorithm IKE DH Key Exchange: name=MODP2048, bits=2048
000 algorithm IKE DH Key Exchange: name=MODP3072, bits=3072
000 algorithm IKE DH Key Exchange: name=MODP4096, bits=4096
000 algorithm IKE DH Key Exchange: name=MODP6144, bits=6144
000 algorithm IKE DH Key Exchange: name=MODP8192, bits=8192
000 algorithm IKE DH Key Exchange: name=DH19, bits=512
000 algorithm IKE DH Key Exchange: name=DH20, bits=768
000 algorithm IKE DH Key Exchange: name=DH21, bits=1056
000 algorithm IKE DH Key Exchange: name=DH23, bits=2048
000 algorithm IKE DH Key Exchange: name=DH24, bits=2048
000
000 stats db_ops: {curr_cnt, total_cnt, maxsz} :context={0,2,64} trans={0,2,6936} attrs={0,2,4624}
000
000 Connection list:
000
000 "ASA": 10.111.111.111/32===172.16.1.4<172.16.1.4>---172.16.1.1...External IP ASA<External IP ASA>===192.168.126.0/24; erouted; eroute owner: #6
000 "ASA":     oriented; my_ip=13.69.128.48; their_ip=unset; my_updown=ipsec _updown;
000 "ASA":   xauth us:none, xauth them:none,  my_username=[any]; their_username=[any]
000 "ASA":   our auth:secret, their auth:secret
000 "ASA":   modecfg info: us:none, them:none, modecfg policy:push, dns1:unset, dns2:unset, domain:unset, banner:unset, cat:unset;
000 "ASA":   labeled_ipsec:no;
000 "ASA":   policy_label:unset;
000 "ASA":   ike_life: 3600s; ipsec_life: 28800s; replay_window: 32; rekey_margin: 540s; rekey_fuzz: 100%; keyingtries: 0;
000 "ASA":   retransmit-interval: 500ms; retransmit-timeout: 60s;
000 "ASA":   sha2-truncbug:no; initial-contact:no; cisco-unity:no; fake-strongswan:no; send-vendorid:no; send-no-esp-tfc:no;
000 "ASA":   policy: PSK+ENCRYPT+TUNNEL+UP+IKEV1_ALLOW+IKEV2_ALLOW+SAREF_TRACK+IKE_FRAG_ALLOW+ESN_NO;
000 "ASA":   conn_prio: 32,24; interface: eth0; metric: 0; mtu: unset; sa_prio:auto; sa_tfc:none;
000 "ASA":   nflog-group: unset; mark: unset; vti-iface:unset; vti-routing:no; vti-shared:no; nic-offload:auto;
000 "ASA":   our idtype: ID_IPV4_ADDR; our id=172.16.1.4; their idtype: ID_IPV4_ADDR; their id=External IP ASA
000 "ASA":   dpd: action:hold; delay:0; timeout:0; nat-t: encaps:auto; nat_keepalive:yes; ikev1_natt:both
000 "ASA":   newest ISAKMP SA: #8; newest IPsec SA: #6;
000 "ASA":   IKE algorithms: AES_CBC_256-HMAC_SHA1-MODP1024
000 "ASA":   IKE algorithm newest: AES_CBC_256-HMAC_SHA1-MODP1024
000 "ASA":   ESP algorithms: AES_CBC_256-HMAC_SHA1_96
000 "ASA":   ESP algorithm newest: AES_CBC_256-HMAC_SHA1_96; pfsgroup=<N/A>
000
000 Total IPsec connections: loaded 1, active 1
000
000 State Information: DDoS cookies not required, Accepting new IKE connections
000 IKE SAs: total(1), half-open(0), open(0), authenticated(1), anonymous(0)
000 IPsec SAs: total(2), authenticated(2), anonymous(0)
000
000 #4: "ASA":4500 STATE_QUICK_R2 **(IPsec SA established)**; EVENT_SA_REPLACE in 18785s; isakmp#3; idle; import:not set
000 #4: "ASA" esp.18aeb089@195.5.131.110 esp.2d6a1d8a@172.16.1.4 tun.0@External IP ASA tun.0@172.16.1.4 ref=0 refhim=0 Traffic: ESPin=8KB ESPout=1KB! ESPmax=4500B
000 #8: "ASA":4500 STATE_MAIN_R3 **(sent MR3, ISAKMP SA established)**; EVENT_SA_REPLACE in 1679s; newest ISAKMP; lastdpd=2s(seq in:0 out:0); idle; import:not set
000 #6: "ASA":4500 STATE_QUICK_R2 (IPsec SA established); EVENT_SA_REPLACE in 22393s; newest IPSEC; eroute owner; isakmp#5; idle; import:not set
000 #6: "ASA" esp.91f7672f@195.5.131.110 esp.7ae54258@172.16.1.4 tun.0@External IP ASA tun.0@172.16.1.4 ref=0 refhim=0 Traffic: ESPin=11KB ESPout=0B! ESPmax=4500B
000
000 Bare Shunt list:
000
```

```
@Ekahau-Gate:~$ **sudo iptables -nL**
Chain INPUT (policy ACCEPT)
target     prot opt source               destination
f2b-sshd   tcp  --  0.0.0.0/0            0.0.0.0/0            multiport dports 22
LOG        icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8 LOG flags 0 level 4 prefix "IMPUT Ping detected: "
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination
LOG        icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8 LOG flags 0 level 4 prefix "FORWARD Ping detected: "
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
LOG        icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8 LOG flags 0 level 4 prefix "OUTPUD Ping detected: "
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8

Chain f2b-sshd (1 references)
target     prot opt source               destination
REJECT     all  --  202.46.1.230         0.0.0.0/0            reject-with icmp-port-unreachable
RETURN     all  --  0.0.0.0/0            0.0.0.0/0
LOG        icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8 LOG flags 0 level 4 prefix "f2b-sshd Ping detected: "
ACCEPT     icmp --  0.0.0.0/0            0.0.0.0/0            icmptype 8

```

```
@Ekahau-Gate:~$ **sudo ip -statistics xfrm state**
src External IP ASA dst 172.16.1.4
        proto esp spi 0x7ae54258(2061845080) reqid 16389(0x00004005) mode tunnel
        replay-window 32 seq 0x00000000 flag af-unspec (0x00100000)
        auth-trunc hmac(sha1) 0xae7fa2a8b0ebf27cccc4c57782603eebd6605be3 (160 bits) 96
        enc cbc(aes) 0xd55699e019d565fb4420b2ca1ba171b1ffce2be968676ef7496ed5d9cbffcf18 (256 bits)
        encap type espinudp sport 4500 dport 4500 addr 0.0.0.0
        anti-replay context: seq 0xf1, oseq 0x0, bitmap 0xffffffff
        lifetime config:
          limit: soft (INF)(bytes), hard (INF)(bytes)
          limit: soft (INF)(packets), hard (INF)(packets)
          expire add: soft 0(sec), hard 0(sec)
          expire use: soft 0(sec), hard 0(sec)
        lifetime current:
          12208(bytes), 241(packets)
          add 2018-09-04 13:58:15 use 2018-09-04 13:58:18
        stats:
          replay-window 0 replay 0 failed 0
src 172.16.1.4 dst External IP ASA
        proto esp spi 0x91f7672f(2448910127) reqid 16389(0x00004005) mode tunnel
        replay-window 32 seq 0x00000000 flag af-unspec (0x00100000)
        auth-trunc hmac(sha1) 0x682748141ff4466094d29de3c110d31059f81f7e (160 bits) 96
        enc cbc(aes) 0x3664464e19b181f8da941a15b81a647428a7c48053327f40afb04cabf9c05822 (256 bits)
        encap type espinudp sport 4500 dport 4500 addr 0.0.0.0
        anti-replay context: seq 0x0, oseq 0x0, bitmap 0x00000000
        lifetime config:
          limit: soft (INF)(bytes), hard (INF)(bytes)
          limit: soft (INF)(packets), hard (INF)(packets)
          expire add: soft 0(sec), hard 0(sec)
          expire use: soft 0(sec), hard 0(sec)
        lifetime current:
          0(bytes), 0(packets)
          add 2018-09-04 13:58:15 use -
        stats:
          replay-window 0 replay 0 failed 0
src External IP ASA dst 172.16.1.4
        proto esp spi 0x2d6a1d8a(761929098) reqid 16389(0x00004005) mode tunnel
        replay-window 32 seq 0x00000000 flag af-unspec (0x00100000)
        auth-trunc hmac(sha1) 0x2b75382431111651dd7876844302b1542f3ca51c (160 bits) 96
        enc cbc(aes) 0x2c8f0c0fcd74447c7122b3894c8afbaba0652e5b0d8e0bf2af85568a8c0cc6ca (256 bits)
        encap type espinudp sport 4500 dport 4500 addr 0.0.0.0
        anti-replay context: seq 0xa2, oseq 0x0, bitmap 0xffffffff
        lifetime config:
          limit: soft (INF)(bytes), hard (INF)(bytes)
          limit: soft (INF)(packets), hard (INF)(packets)
          expire add: soft 0(sec), hard 0(sec)
          expire use: soft 0(sec), hard 0(sec)
        lifetime current:
          8208(bytes), 162(packets)
          add 2018-09-04 12:58:08 use 2018-09-04 12:58:18
        stats:
          replay-window 0 replay 0 failed 0
src 172.16.1.4 dst External IP ASA
        proto esp spi 0x18aeb089(414101641) reqid 16389(0x00004005) mode tunnel
        replay-window 32 seq 0x00000000 flag af-unspec (0x00100000)
        auth-trunc hmac(sha1) 0x6970a8a51b8bfdd6fd3347ed3cb5e00092505ce4 (160 bits) 96
        enc cbc(aes) 0x463a1abaaec51f073d5f680e4e602c400c80ee60afed6f48e9e0ded4076d6ecb (256 bits)
        encap type espinudp sport 4500 dport 4500 addr 0.0.0.0
        anti-replay context: seq 0x0, oseq 0x15, bitmap 0x00000000
        lifetime config:
          limit: soft (INF)(bytes), hard (INF)(bytes)
          limit: soft (INF)(packets), hard (INF)(packets)
          expire add: soft 0(sec), hard 0(sec)
          expire use: soft 0(sec), hard 0(sec)
        lifetime current:
          1764(bytes), 21(packets)
          add 2018-09-04 12:58:08 use 2018-09-04 13:25:02
        stats:
          replay-window 0 replay 0 failed 0
```

---

### Post by deadflowr on 2018-09-04
Please use code tags when posting terminal command outputs, as it will retain the proper formatting.
And make it easier to read.

**EDIT**: Also 17.10 is no longer supported.
Upgrade to 18.04.
(By upgrade I mean install a clean install of 18.04)

---

