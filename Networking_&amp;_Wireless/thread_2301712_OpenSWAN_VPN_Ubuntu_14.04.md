---
title: "OpenSWAN VPN Ubuntu 14.04"
date: 2015-11-04
forum: Networking &amp; Wireless
---

### Post by victor67 on 2015-11-04
Please help. My openswan configurations are establishing connections between sites, but I am unable to ping the local networks between the sites. So 10.1.1.1 can't ping 10.1.2.1

Local Site (OpenSWAN)

Server: Ubuntu 14.04
Server IP: 10.1.1.1
Subnet:     255.255.255.0
External IP: 159.159.159.159

eth0 is WAN
eth1 is LAN

Remote Site (SonicWall)

Server IP: 10.1.2.1
Subnet:    255.255.255.0
External IP:  174.174.174.174

```

# /etc/ipsec.conf - Openswan IPsec configuration file

# This file:  /usr/share/doc/openswan/ipsec.conf-sample
#
# Manual:     ipsec.conf.5


version 2.0     # conforms to second version of ipsec.conf specification

# basic configuration
config setup
        dumpdir=/var/run/pluto/
        nat_traversal=yes
        virtual_private=%v4:10.0.0.0/8,%v4:192.168.0.0/16,%v4:172.16.0.0/12,%v4:25.0.0.0/8,%v6:fd00::/8,%v6:fe80::/10
        oe=off
        protostack=netkey
        fragicmp=no

conn PTWVPN

        left=159.159.159.159
        leftsourceip=10.1.1.1
        leftsubnet=10.1.1.0/24
        leftid=159.159.159.159
        right=174.174.174.174
        rightid=174.174.174.174
        rightsourceip=10.1.2.1
        rightsubnet=10.1.2.0/24
        type=tunnel
        auth=esp
        authby=secret
        ikelifetime=28800m
        rekeymargin=10m
        rekeyfuzz=0%
        keylife=28800s
        esp=3des-md5
        ike=3des-md5
        keyexchange=ike
        pfs=yes
        auto=start
```

```
159.159.159.159 174.174.174.174: PSK "PASSWORD"
```

```
$ ipsec verify
To check this machine, you need to run "ipsec verify" as root.
fwadmin@LPMs2svpn:~$ sudo ipsec verify
Checking your system to see if IPsec got installed and started correctly:
Version check and ipsec on-path                                 [OK]
Linux Openswan U2.6.38/K3.19.0-25-generic (netkey)
Checking for IPsec support in kernel                            [OK]
 SAref kernel support                                           [N/A]
 NETKEY:  Testing XFRM related proc values                      [OK]
    [OK]
    [OK]
Checking that pluto is running                                  [OK]
 Pluto listening for IKE on udp 500                             [OK]
 Pluto listening for NAT-T on udp 4500                          [OK]
Two or more interfaces found, checking IP forwarding            [FAILED]
Checking NAT and MASQUERADEing                                  [OK]
Checking for 'ip' command                                       [OK]
Checking /bin/sh is not /bin/dash                               [WARNING]
Checking for 'iptables' command                                 [OK]
Opportunistic Encryption Support                                [DISABLED]


```

```
iptables -vL -t nat
Chain PREROUTING (policy ACCEPT 7672 packets, 527K bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain INPUT (policy ACCEPT 935 packets, 95840 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain OUTPUT (policy ACCEPT 372 packets, 26395 bytes)
 pkts bytes target     prot opt in     out     source               destination         

Chain POSTROUTING (policy ACCEPT 321 packets, 22829 bytes)
 pkts bytes target     prot opt in     out     source               destination         
 6788  435K SNAT       all  --  any    eth0    anywhere             anywhere             to:159.159.159.159
```

---

