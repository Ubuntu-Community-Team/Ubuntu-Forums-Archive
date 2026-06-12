---
title: "Managing routes with VPN and Network Manager"
date: 2016-10-20
forum: Networking &amp; Wireless
---

### Post by spacexion on 2016-10-20
I have an OpenVPN server which I'm very satisfied of.
I usually connect the clients to the server simply opening a terminal and running "openvpn" followed by the ovpn file with appropriate configuration, certificates and key. Everything works fine this way.


Anyway, there is something I don't understand and I require some little help about it.


I never got the VPN to work from Network Manager (with VPN plugin already installed).
Once the client is configured in Network Manager, the connexion between client and server will go up but it seems as there isn't any traffic going through the VPN. I can't even ping the client from the server.
I suspect it's a routing problem, but I'm not comfortable enough with network management to fix it on my own.


This is the client configuration contained in my conf.ovpn file which works 100% fine:

```

    client
    proto udp
    remote myown.domain.com
    port 1194
    dev tun
    nobind
    comp-lzo yes
    push "comp-lzo yes"
    redirect-gateway def1
    verb 3
    key-direction 1
```



This is my routing table, VPN disconnected:

    [HTML]Kernel IP routing table
    Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
    0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan5
    192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan5
[/HTML]


My routing table with OpenVpn client started from terminal and "conf.ovpn" file:

    ```
Kernel IP routing table
    Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
    0.0.0.0         10.8.0.13       128.0.0.0       UG        0 0          0 tun0
    0.0.0.0         192.168.1.1     0.0.0.0         UG        0 0          0 wlan5
    10.8.0.1        10.8.0.13       255.255.255.255 UGH       0 0          0 tun0
    10.8.0.13       0.0.0.0         255.255.255.255 UH        0 0          0 tun0
    95.110.xxx.xxx  192.168.1.1     255.255.255.255 UGH       0 0          0 wlan5
    128.0.0.0       10.8.0.13       128.0.0.0       UG        0 0          0 tun0
    192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan5

```


And finally my routing table with VPN client configured in Network Manager:

```
Kernel IP routing table
    Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
    0.0.0.0         10.8.0.13       0.0.0.0         UG        0 0          0 tun0
    10.8.0.13       0.0.0.0         255.255.255.255 UH        0 0          0 tun0
    95.110.xxx.xxx  192.168.1.1     255.255.255.255 UGH       0 0          0 wlan5
    192.168.1.0     0.0.0.0         255.255.255.0   U         0 0          0 wlan5
```




Did anyone can help me understand what I should change in Network Manager to get VPN client working the same way as when I start Openvpn in CLI?
Tx!

---

