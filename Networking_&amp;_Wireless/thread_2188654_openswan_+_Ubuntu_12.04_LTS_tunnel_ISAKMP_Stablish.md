---
title: "openswan + Ubuntu 12.04 LTS tunnel ISAKMP Stablished ( no pings / route )"
date: 2013-11-18
forum: Networking &amp; Wireless
---

### Post by carlos.computadore on 2013-11-18
Hi all.

I´m not exactly a newbie on Linux, but sometimes my bosses want me to do certain things that are far beyond my knowledge. Even so, using google here and there, I manage to achieve some tasks nicely. This time I have a problem I just can´t find a solution. 

I installed Ubuntu 12.04 LTS on a PC, 2 nics, then update && upgrade. Then I install ssh. Finally I installed Openswan, and everything went very well. 

The tunnel looks like works ( net 2 net ) but I cant ping. I can´t also telnet PC´s machines at the other side. "The Other Side" is a company that already have thios working for several other networks, so I dont believe there´s any problems out there. Its my config.

I´m suspecting my iptables rules, or maybe something about routing. I´m under very heavy pressure from bosses to get this working, or I will have serious problems about my job. Normally I would send them to hell, but I really need the job, so, I come here after some help of more experienced users.

I´m posting everything here that I think can be usefull to solve this problem.

Any help is highly appreciated. ( and sorry for my english mistakes if some )

```
[COLOR=#800000]**/etc/network/interfaces**[/COLOR]
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet static
        address MY_WAN_IP
        netmask 255.255.255.0
        network 201.6.111.0
        broadcast 201.6.111.255
        gateway MY_WAN_GATEWAY
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 8.8.8.8 8.8.4.4
        dns-search static.spo.virtua.com.br

auto eth0
iface eth0 inet dhcp # -> Its receiving always the same IP from my DHCP server

[COLOR=#800000]**ifconfig**[/COLOR]
eth0      Link encap:Ethernet  HWaddr 00:e0:7d:d1:ec:4c
          inet addr:192.168.110.101  Bcast:192.168.110.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:7dff:fed1:ec4c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:256332 errors:0 dropped:0 overruns:0 frame:0
          TX packets:981 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:20749672 (20.7 MB)  TX bytes:107952 (107.9 KB)

eth1      Link encap:Ethernet  HWaddr 00:11:d8:4c:6b:c7
          inet addr: MY_WAN_IP  Bcast:201.6.111.255  Mask:255.255.255.0
          inet6 addr: fe80::211:d8ff:fe4c:6bc7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2026925 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:133354232 (133.3 MB)  TX bytes:7199079 (7.1 MB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:424 (424.0 B)  TX bytes:424 (424.0 B)

[COLOR=#800000]**/etc/rc.local**[/COLOR]
for vpn in /proc/sys/net/ipv4/conf/*; do echo 0 > $vpn/accept_redirects; echo 0 > $vpn/send_redirects; done
#iptables --table nat --append POSTROUTING --jump MASQUERADE
exit 0

**[COLOR=#800000]ipsec.conf[/COLOR]**
# version       2.0     # conforms to second version of ipsec.conf specification
# basic configuration
config setup
        dumpdir=/var/run/pluto/
        nat_traversal=no
        #virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12,%v4:25.0.0.0/8,%v6:fd00::/8,%v6:fe80::/10
        #oe=off
        protostack=auto
        interfaces="ipsec0=eth1"

conn checkexpress
        left=MY_WAN_IP
        leftnexthop=MY_WAN_GATEWAY
        leftid=MY_WAN_IP
        leftsubnet=192.168.110.0/24
        right=OTHER_COMPANY_IP
        rightnexthop=OTHER_COMPANY_GATEWAY
        rightid=Other_Company_IP
        rightsubnet=172.16.22.0/24
        auth=esp
        esp=3des-md5-96
        ikelifetime=28800s
        keylife=3600s
        pfs=no
        compress=no
        authby=secret
        type=tunnel
        auto=add

**[COLOR=#800000]ipsec.secrets[/COLOR]**
MY_WAN_IP OTHER_SIDE_IP : PSK "a shared key identical on both sides"
#include /var/lib/openswan/ipsec.secrets.inc

**[COLOR=#800000]iptables -L -v[/COLOR]**
Chain INPUT (policy ACCEPT 8580 packets, 990K bytes)
 pkts bytes target     prot opt in     out     source               destination
  240 45068 ACCEPT     udp  --  any    any     anywhere             anywhere             udp spt:isakmp dpt:isakmp
    0     0 ACCEPT     esp  --  any    any     anywhere             anywhere
    0     0 ACCEPT     ah   --  any    any     anywhere             anywhere
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp spt:2020 dpt:2020
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp spt:4500 dpt:4500
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp spt:l2f dpt:l2f
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp spt:isakmp dpt:isakmp
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere             udp spt:isakmp dpt:isakmp
    0     0 ACCEPT     icmp --  any    any     192.168.110.0        anywhere             icmp echo-request
 1224  104K ACCEPT     all  --  any    any     anywhere             anywhere             ctstate RELATED,ESTABLISHED
   19   844 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp dpt:ssh
    0     0 ACCEPT     icmp --  any    any     172.16.22.0          anywhere             icmp echo-request

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination
  213 13240            all  --  any    any     192.168.110.0/24     172.16.22.0/24
  209 13000 ACCEPT     all  --  any    any     192.168.110.0/24     172.16.22.0/24

Chain OUTPUT (policy ACCEPT 699 packets, 187K bytes)
 pkts bytes target     prot opt in     out     source               destination
  364  174K ACCEPT     udp  --  any    any     anywhere             anywhere             udp spt:isakmp dpt:isakmp
    0     0 ACCEPT     esp  --  any    any     anywhere             anywhere
    0     0 ACCEPT     ah   --  any    any     anywhere             anywhere
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp spt:2020 dpt:2020
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp spt:4500 dpt:4500
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp spt:l2f dpt:l2f
    0     0 ACCEPT     tcp  --  any    any     anywhere             anywhere             tcp spt:isakmp dpt:isakmp
    0     0 ACCEPT     udp  --  any    any     anywhere             anywhere             udp spt:isakmp dpt:isakmp
    0     0 ACCEPT     icmp --  any    any     192.168.110.0        anywhere             icmp echo-request

[COLOR=#800000]**route -n**[/COLOR]
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0           201.6.111.1     0.0.0.0         UG    100    0           0  eth1
192.168.110.0  0.0.0.0         255.255.255.0   U     0      0         0    eth0
201.6.111.0     0.0.0.0         255.255.255.0   U     0      0          0   eth1

[COLOR=#800000]**ipsec auto --status**[/COLOR]
000 using kernel interface: netkey
000 interface lo/lo ::1
000 interface lo/lo 127.0.0.1
000 interface eth1/eth1 <MY_WAN_IP>
000 interface eth0/eth0 192.168.110.101
000 %myid = (none)
000 debug none
000
000 virtual_private (%priv):
000 - allowed 0 subnets:
000 - disallowed 0 subnets:
000 WARNING: Either virtual_private= is not specified, or there is a syntax
000          error in that line. 'left/rightsubnet=vhost:%priv' will not work!
000 WARNING: Disallowed subnets in virtual_private= is empty. If you have
000          private address space in internal use, it should be excluded!
000
000 algorithm ESP encrypt: id=2, name=ESP_DES, ivlen=8, keysizemin=64, keysizemax=64
000 algorithm ESP encrypt: id=3, name=ESP_3DES, ivlen=8, keysizemin=192, keysizemax=192
000 algorithm ESP encrypt: id=6, name=ESP_CAST, ivlen=8, keysizemin=40, keysizemax=128
000 algorithm ESP encrypt: id=7, name=ESP_BLOWFISH, ivlen=8, keysizemin=40, keysizemax=448
000 algorithm ESP encrypt: id=11, name=ESP_NULL, ivlen=0, keysizemin=0, keysizemax=0
000 algorithm ESP encrypt: id=12, name=ESP_AES, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=13, name=ESP_AES_CTR, ivlen=8, keysizemin=160, keysizemax=288
000 algorithm ESP encrypt: id=14, name=ESP_AES_CCM_A, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=15, name=ESP_AES_CCM_B, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=16, name=ESP_AES_CCM_C, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=18, name=ESP_AES_GCM_A, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=19, name=ESP_AES_GCM_B, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=20, name=ESP_AES_GCM_C, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=22, name=ESP_CAMELLIA, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=252, name=ESP_SERPENT, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP encrypt: id=253, name=ESP_TWOFISH, ivlen=8, keysizemin=128, keysizemax=256
000 algorithm ESP auth attr: id=1, name=AUTH_ALGORITHM_HMAC_MD5, keysizemin=128, keysizemax=128
000 algorithm ESP auth attr: id=2, name=AUTH_ALGORITHM_HMAC_SHA1, keysizemin=160, keysizemax=160
000 algorithm ESP auth attr: id=5, name=AUTH_ALGORITHM_HMAC_SHA2_256, keysizemin=256, keysizemax=256
000 algorithm ESP auth attr: id=6, name=AUTH_ALGORITHM_HMAC_SHA2_384, keysizemin=384, keysizemax=384
000 algorithm ESP auth attr: id=7, name=AUTH_ALGORITHM_HMAC_SHA2_512, keysizemin=512, keysizemax=512
000 algorithm ESP auth attr: id=8, name=AUTH_ALGORITHM_HMAC_RIPEMD, keysizemin=160, keysizemax=160
000 algorithm ESP auth attr: id=9, name=AUTH_ALGORITHM_AES_CBC, keysizemin=128, keysizemax=128
000 algorithm ESP auth attr: id=251, name=(null), keysizemin=0, keysizemax=0
000
000 algorithm IKE encrypt: id=0, name=(null), blocksize=16, keydeflen=131
000 algorithm IKE encrypt: id=5, name=OAKLEY_3DES_CBC, blocksize=8, keydeflen=192
000 algorithm IKE encrypt: id=7, name=OAKLEY_AES_CBC, blocksize=16, keydeflen=128
000 algorithm IKE hash: id=1, name=OAKLEY_MD5, hashsize=16
000 algorithm IKE hash: id=2, name=OAKLEY_SHA1, hashsize=20
000 algorithm IKE dh group: id=2, name=OAKLEY_GROUP_MODP1024, bits=1024
000 algorithm IKE dh group: id=5, name=OAKLEY_GROUP_MODP1536, bits=1536
000 algorithm IKE dh group: id=14, name=OAKLEY_GROUP_MODP2048, bits=2048
000 algorithm IKE dh group: id=15, name=OAKLEY_GROUP_MODP3072, bits=3072
000 algorithm IKE dh group: id=16, name=OAKLEY_GROUP_MODP4096, bits=4096
000 algorithm IKE dh group: id=17, name=OAKLEY_GROUP_MODP6144, bits=6144
000 algorithm IKE dh group: id=18, name=OAKLEY_GROUP_MODP8192, bits=8192
000 algorithm IKE dh group: id=22, name=OAKLEY_GROUP_DH22, bits=1024
000 algorithm IKE dh group: id=23, name=OAKLEY_GROUP_DH23, bits=2048
000 algorithm IKE dh group: id=24, name=OAKLEY_GROUP_DH24, bits=2048
000
000 stats db_ops: {curr_cnt, total_cnt, maxsz} :context={0,0,0} trans={0,0,0} attrs={0,0,0}
000
000 "checkexpress": 192.168.110.0/24===MY_WAN_IP<MY_WAN_IP>[+S=C]---MY_WAN_GATEWAY...OTHER_SIDE_GATEWAY---OTHER_SIDE_IP<OTHER_SIDE_IP>[+S=C]===172.16.2                                           2.0/24; erouted; eroute owner: #20
000 "checkexpress":     myip=unset; hisip=unset;
000 "checkexpress":   ike_life: 28800s; ipsec_life: 3600s; rekey_margin: 540s; rekey_fuzz: 100%; keyingtries: 0
000 "checkexpress":   policy: PSK+ENCRYPT+TUNNEL+IKEv2ALLOW+SAREFTRACK+lKOD+rKOD; prio: 24,24; interface: eth1;
000 "checkexpress":   newest ISAKMP SA: #13; newest IPsec SA: #20;
000 "checkexpress":   IKE algorithm newest: 3DES_CBC_192-MD5-MODP1536
000 "checkexpress":   ESP algorithms wanted: 3DES(3)_000-MD5(1)_096; flags=-strict
000 "checkexpress":   ESP algorithms loaded: 3DES(3)_192-MD5(1)_096
000 "checkexpress":   ESP algorithm newest: 3DES_000-HMAC_MD5; pfsgroup=<N/A>
000
000 #20: "checkexpress":500 STATE_QUICK_R2 (IPsec SA established); EVENT_SA_REPLACE in 2182s; newest IPSEC; eroute owner; isakmp#13; idle; import:not set
000 #20: "checkexpress" esp.10fe3bff@OTHER_SIDE_IP esp.458a01cf@MY_WAN_IP tun.0@OTHER_SIDE_IP tun.0@MY_WAN_IP ref=0 refhim=4294901761
000 #13: "checkexpress":500 STATE_MAIN_R3 (sent MR3, ISAKMP SA established); EVENT_SA_REPLACE in 9512s; newest ISAKMP; nodpd; idle; import:not set

[COLOR=#800000]**ipsec look**[/COLOR]
vpnserver Mon Nov 18 12:23:19 BRST 2013
XFRM state:
src MY_WAN_IP dst OTHER_SIDE_IP
        proto esp spi 0x10fe3c2d reqid 16385 mode tunnel
        replay-window 32 flag af-unspec
        auth-trunc hmac(md5) 0x7177fed3caea04d732ae539f184da95f 96
        enc cbc(des3_ede) 0x6ec0b3797d93e11f6f84d229a4d25bc0f05825b5ea9184bb
src OTHER_SIDE_IP dst MY_WAN_IP
        proto esp spi 0x3545c780 reqid 16385 mode tunnel
        replay-window 32 flag af-unspec
        auth-trunc hmac(md5) 0x5f8413b41bf18d40c84122d10455dc8d 96
        enc cbc(des3_ede) 0xf2ab5430c7ce138f0fd5b91efb00e5c103edda2959de894c
src MY_WAN_IP dst OTHER_SIDE_IP
        proto esp spi 0x10fe3bff reqid 16385 mode tunnel
        replay-window 32 flag af-unspec
        auth-trunc hmac(md5) 0xd7a7dfa0ffaea73e9cf5e37bf0b95732 96
        enc cbc(des3_ede) 0xd7007256c1c82a8653949247e4a4a10f85aacb1d6d0048a6
src OTHER_SIDE_IP dst MY_WAN_IP
        proto esp spi 0x458a01cf reqid 16385 mode tunnel
        replay-window 32 flag af-unspec
        auth-trunc hmac(md5) 0x06f2d26647b9e4a8a54675982c97fdfc 96
        enc cbc(des3_ede) 0x33c299d6958ad9d43d91c4566d7c9a412d1635b858f3b088
XFRM policy:
src 192.168.110.0/24 dst 172.16.22.0/24
        dir out priority 2344
        tmpl src MY_WAN_IP dst OTHER_SIDE_IP
                proto esp reqid 16385 mode tunnel
src 172.16.22.0/24 dst 192.168.110.0/24
        dir fwd priority 2344
        tmpl src OTHER_SIDE_IP dst MY_WAN_IP
                proto esp reqid 16385 mode tunnel
src 172.16.22.0/24 dst 192.168.110.0/24
        dir in priority 2344
        tmpl src OTHER_SIDE_IP dst MY_WAN_IP
                proto esp reqid 16385 mode tunnel
src ::/0 dst ::/0
        socket out priority 0
src ::/0 dst ::/0
        socket in priority 0
src 0.0.0.0/0 dst 0.0.0.0/0
        socket out priority 0
src 0.0.0.0/0 dst 0.0.0.0/0
        socket in priority 0
src 0.0.0.0/0 dst 0.0.0.0/0
        socket out priority 0
src 0.0.0.0/0 dst 0.0.0.0/0
        socket in priority 0
src 0.0.0.0/0 dst 0.0.0.0/0
        socket out priority 0
src 0.0.0.0/0 dst 0.0.0.0/0
        socket in priority 0
XFRM done
IPSEC mangle TABLES
iptables: No chain/target/match by that name.
ip6tables: No chain/target/match by that name.
NEW_IPSEC_CONN mangle TABLES
iptables: No chain/target/match by that name.
ip6tables: No chain/target/match by that name.
ROUTING TABLES
default via 201.6.111.1 dev eth1  metric 100
201.6.111.0/24 dev eth1  proto kernel  scope link  src MY_WAN_IP
fe80::/64 dev eth1  proto kernel  metric 256
```

---

### Post by carlos.computadore on 2013-11-19
Nobody ?

I would even pay ( if reasonable ) to someone that can solve this problem for / with me.

---

### Post by Diego_Ferreira on 2014-02-04
Hello Carlos,

Been working for 4 months with OpenSwan IPSec VPNs and had the same problems, same boat dude! =]

I haven´t found your iptables´ rules for isakmp ports, have you checked those?
Take a look at this link, I guess you´d need only the second configuration 
[http://blog.netnerds.net/2010/01/openwrt-iptables-based-firewall-rules-for-pptp-and-ipsec/](http://blog.netnerds.net/2010/01/openwrt-iptables-based-firewall-rules-for-pptp-and-ipsec/)

Regards,

---

