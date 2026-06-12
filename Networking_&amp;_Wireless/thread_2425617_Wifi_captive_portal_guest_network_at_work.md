---
title: "Wifi captive portal guest network at work"
date: 2019-08-28
forum: Networking &amp; Wireless
---

### Post by darshue on 2019-08-28
```

[COLOR=#242729][FONT=Arial]I am trying to log into guest network at work. Wifi icon had no question mark but the captive portal page is not reachable. It seemed there's some communication established but Ubuntu just can't open the address.
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]is there any information extracted from the http below that can be used to set network setting?
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks for the help
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My work wifi returns and address for ubuntu to open as below: 

[https://securelogin.amat.com/upload/custom/rainbow/login.htm?cmd=login&mac=98:3b:8f:31:89:a9&ip=172.16.86.232&essid=rainbow&apname=scla81w2_o25&apgroup=SCLA-B81&url=http%3A%2F%2Fwww%2Egstatic%2Ecom%2Fgenerate%5F204](https://securelogin.amat.com/upload/custom/rainbow/login.htm?cmd=login&mac=98:3b:8f:31:89:a9&ip=172.16.86.232&essid=rainbow&apname=scla81w2_o25&apgroup=SCLA-B81&url=http%3A%2F%2Fwww%2Egstatic%2Ecom%2Fgenerate%5F204)
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]it seems there's some setting included in the web address but I don't understand it. I am a new linux user. My ubuntu version is 18.04.3LTS
[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]My network setting is:[/FONT][/COLOR]
enp0s31f6: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 48:2a:e3:22:82:39  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  memory 0xee300000-ee320000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 944  bytes 96414 (96.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 944  bytes 96414 (96.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

wlp2s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.105  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::fa5f:f019:8f4d:d4d4  prefixlen 64  scopeid 0x20<link>
        ether 98:3b:8f:31:89:a9  txqueuelen 1000  (Ethernet)
        RX packets 32376  bytes 28960359 (28.9 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 17199  bytes 4607132 (4.6 MB) [COLOR=#242729][FONT=Consolas]        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0[/FONT][/COLOR]
```

---

