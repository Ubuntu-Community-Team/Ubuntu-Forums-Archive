---
title: "Strongswan ipsec connection failed"
date: 2016-12-05
forum: Networking &amp; Wireless
---

### Post by zmask37 on 2016-12-05
Hey guys,

I am facing a pretty much hard issue for a week nearly. I had a strongswan vpn setup on my ubuntu and i was able to establish VPN connection between the local and peer once successfully. Then i killed the vpn session and tried establishing the connection again but after that it is unable to establish the connection. I am receiving the below error. Any help would be appreciated.


```
testusr@ubuntu:~$ sudo ipsec up HA-VPN-3
establishing CHILD_SA HA-VPN-3
generating CREATE_CHILD_SA request 2 [ SA No TSi TSr ]
sending packet: from xx.xx.xx.xx[500] to yy.y.y.y[500] (332 bytes)
received packet: from yy.y.y.y[500] to xx.xx.xx.xx[500] (220 bytes)
parsed CREATE_CHILD_SA response 2 [ SA No TSi TSr N(ESP_TFC_PAD_N) N(NON_FIRST_FRAG) ]
received ESP_TFC_PADDING_NOT_SUPPORTED, not using ESPv3 TFC padding
unable to install policy ab.abc.a.a/16 === def.d.dd.d/24 out (mark 0/0x00000000) for reqid 172, the same policy for reqid 1 exists
unable to install policy def.d.dd.d/24 === ab.abc.a.a/16 in (mark 0/0x00000000) for reqid 172, the same policy for reqid 1 exists
unable to install policy def.d.dd.d/24 === ab.abc.a.a/16 fwd (mark 0/0x00000000) for reqid 172, the same policy for reqid 1 exists
unable to install policy ab.abc.a.a/16 === def.d.dd.d/24 out (mark 0/0x00000000) for reqid 172, the same policy for reqid 1 exists
unable to install policy def.d.dd.d/24 === ab.abc.a.a/16 in (mark 0/0x00000000) for reqid 172, the same policy for reqid 1 exists
unable to install policy def.d.dd.d/24 === ab.abc.a.a/16 fwd (mark 0/0x00000000) for reqid 172, the same policy for reqid 1 exists
unable to install IPsec policies (SPD) in kernel
failed to establish CHILD_SA, keeping IKE_SA
sending DELETE for ESP CHILD_SA with SPI cb080796
generating INFORMATIONAL request 3 [ D ]
sending packet: from xx.xx.xx.xx[500] to yy.y.y.y[500] (76 bytes)
received packet: from yy.y.y.y[500] to xx.xx.xx.xx[500] (76 bytes)
parsed INFORMATIONAL response 3 [ D ]
establishing connection 'VPN' failed
```


ipsec.conf


```
config setup
conn %default
     ikelifetime=60m
     keylife=20m
     rekeymargin=3m
     keyingtries=1
     authby=secret
     keyexchange=ikev2
     mobike=no


conn HA-VPN-3
     left=xx.xx.xx.xx
     leftsubnet=ab.abc.a.a/16
     leftid=test1@xxxx.com
     leftfirewall=yes
     right=yy.y.y.y
     rightsubnet=def.d.dd.d/24
     rightid=test2@xxxx.com
     auto=add
```

---

