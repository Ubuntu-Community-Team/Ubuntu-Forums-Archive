---
title: "HP Proliant G6 and strange behavior..."
date: 2018-08-07
forum: Networking &amp; Wireless
---

### Post by mattiash on 2018-08-07
I got a HP Proliant G6 DL380 and the four NIC are connected to a HP Procurve switch.
I have setup the servers netplan file like this:
--
[COLOR=#F8F8F2][FONT=Menlo][COLOR=#f92672]network[/COLOR]:
    [COLOR=#f92672]version[/COLOR]: [COLOR=#ae81ff]2[/COLOR]
    [COLOR=#f92672]renderer[/COLOR]: [COLOR=#e6db74]networkd[/COLOR]
    [COLOR=#f92672]ethernets[/COLOR]:
        [COLOR=#f92672]enp2s0f0[/COLOR]:
            [COLOR=#f92672]addresses[/COLOR]: [[COLOR=#e6db74]10.10.1.80/24[/COLOR]]
            [COLOR=#f92672]gateway4[/COLOR]:  [COLOR=#ae81ff]10.10.1.1[/COLOR]
            [COLOR=#f92672]nameservers[/COLOR]:
                [COLOR=#f92672]addresses[/COLOR]: [[COLOR=#ae81ff]10.10.1.1[/COLOR]]
            [COLOR=#f92672]dhcp4[/COLOR]: [COLOR=#ae81ff]false[/COLOR]
            [COLOR=#f92672]optional[/COLOR]: [COLOR=#ae81ff]true[/COLOR]
        [COLOR=#f92672]enp2s0f1[/COLOR]:
            [COLOR=#f92672]addresses[/COLOR]: [[COLOR=#e6db74]10.10.1.82/24[/COLOR]]
            [COLOR=#f92672]gateway4[/COLOR]:  [COLOR=#ae81ff]10.10.1.1[/COLOR]
            [COLOR=#f92672]nameservers[/COLOR]:
                [COLOR=#f92672]addresses[/COLOR]: [[COLOR=#ae81ff]10.10.1.1[/COLOR]]
            [COLOR=#f92672]dhcp4[/COLOR]: [COLOR=#ae81ff]false[/COLOR]
            [COLOR=#f92672]optional[/COLOR]: [COLOR=#ae81ff]true[/COLOR]
        [COLOR=#f92672]enp3s0f0[/COLOR]:
            [COLOR=#f92672]addresses[/COLOR]: [[COLOR=#e6db74]10.10.1.84/24[/COLOR]]
            [COLOR=#f92672]gateway4[/COLOR]:  [COLOR=#ae81ff]10.10.1.1[/COLOR]
            [COLOR=#f92672]nameservers[/COLOR]:
                [COLOR=#f92672]addresses[/COLOR]: [[COLOR=#ae81ff]10.10.1.1[/COLOR]]
            [COLOR=#f92672]dhcp4[/COLOR]: [COLOR=#ae81ff]false[/COLOR]
            [COLOR=#f92672]optional[/COLOR]: [COLOR=#ae81ff]true[/COLOR]
        [COLOR=#f92672]enp3s0f1[/COLOR]:
            [COLOR=#f92672]addresses[/COLOR]: [[COLOR=#e6db74]10.10.1.86/24[/COLOR]]
            [COLOR=#f92672]gateway4[/COLOR]:  [COLOR=#ae81ff]10.10.1.1[/COLOR]
            [COLOR=#f92672]nameservers[/COLOR]:
                [COLOR=#f92672]addresses[/COLOR]: [[COLOR=#ae81ff]10.10.1.1[/COLOR]]
            [COLOR=#f92672]dhcp4[/COLOR]: [COLOR=#ae81ff]false[/COLOR]
            [COLOR=#f92672]optional[/COLOR]: [COLOR=#ae81ff]true[/COLOR]
[/FONT][/COLOR]

All is fine and works but when I ifconfig -a I get this:
--
enp2s0f0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.10.1.80  netmask 255.255.255.0  broadcast 10.10.1.255
        inet6 fe80::7ae7:d1ff:fe7c:1c88  prefixlen 64  scopeid 0x20<link>
        ether 78:e7:d1:7c:1c:88  txqueuelen 1000  (Ethernet)
        RX packets 18928  bytes 1684492 (1.6 MB)
        RX errors 0  dropped 7278  overruns 0  frame 0
        TX packets 1665  bytes 214632 (214.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp2s0f1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.10.1.140  netmask 255.255.255.0  broadcast 10.10.1.255
        inet6 fe80::7ae7:d1ff:fe7c:1c8a  prefixlen 64  scopeid 0x20<link>
        ether 78:e7:d1:7c:1c:8a  txqueuelen 1000  (Ethernet)
        RX packets 13887  bytes 1098841 (1.0 MB)
        RX errors 0  dropped 7277  overruns 0  frame 0
        TX packets 39  bytes 4566 (4.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp3s0f0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::7ae7:d1ff:fe7c:1c8c  prefixlen 64  scopeid 0x20<link>
        ether 78:e7:d1:7c:1c:8c  txqueuelen 1000  (Ethernet)
        RX packets 13654  bytes 1020688 (1.0 MB)
        RX errors 0  dropped 7278  overruns 0  frame 0
        TX packets 269  bytes 81102 (81.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp3s0f1: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 10.10.1.138  netmask 255.255.255.0  broadcast 10.10.1.255
        inet6 fe80::7ae7:d1ff:fe7c:1c8e  prefixlen 64  scopeid 0x20<link>
        ether 78:e7:d1:7c:1c:8e  txqueuelen 1000  (Ethernet)
        RX packets 13948  bytes 1113256 (1.1 MB)
        RX errors 0  dropped 7279  overruns 0  frame 0
        TX packets 1667  bytes 266636 (266.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

How can this be?

---

