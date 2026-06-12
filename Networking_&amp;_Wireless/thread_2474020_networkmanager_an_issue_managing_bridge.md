---
title: "networkmanager an issue managing bridge"
date: 2022-04-20
forum: Networking &amp; Wireless
---

### Post by r00ty2 on 2022-04-20
Hey, I'm currently have this:

```
br0: connected to bridge-br0        "br0"
        bridge, 02:81:A4:CF:CE:9F, sw, mtu 1500
        ip4 default
        inet4 192.168.1.10/24
        route4 192.168.1.0/24
        route4 0.0.0.0/0
        inet6 fe80::b274:abc7:1ff9:ecc5/64
        route6 fe80::/64
        route6 ff00::/8


eth0: connected to bridge-slave-eth0
        "eth0"
        ethernet (dwmac-sun8i), 02:81:A4:CF:CE:9F, hw, mtu 1500
        master br0
        route6 ff00::/8


lo: unmanaged
        "lo"
        loopback (unknown), 00:00:00:00:00:00, sw, mtu 65536


DNS configuration:
        servers: 1.1.1.1
        domains: o
        interface: br0



```



I'm trying to create a tap interface and add it to br0

```
&#10140;  ~ sudo -sE&#10140;  ~ nmcli con add type tun ifname tap0 mode tap ip4 10.10.10.10/24
Connection 'tun-tap0' (02a77364-3dc1-4bed-8b46-e8be91fcbb93) successfully added.
&#10140;  ~ nmcli con add type bridge-slave ifname tap0 master br0
Connection 'bridge-slave-tap0' (831d750b-3d86-40dd-8ab5-da4bdccc5f9e) successfully added.
&#10140;  ~ nmcli c
NAME               UUID                                  TYPE      DEVICE
bridge-br0         4dfb2c88-b861-49c4-aee0-9449a9b33b9d  bridge    br0
tun-tap0           02a77364-3dc1-4bed-8b46-e8be91fcbb93  tun       tap0
bridge-slave-eth0  e0a65d4f-d062-4959-8343-1aa11a72dff8  ethernet  eth0
bridge-slave-tap0  831d750b-3d86-40dd-8ab5-da4bdccc5f9e  ethernet  --
wire               a4c2b672-2617-3f07-bc25-53b3e415dba5  ethernet  --
```

I'm getting an error when trying to enable it
```
&#10140;  ~ nmcli con up bridge-slave-tap0
Error: Connection activation failed: No suitable device found for this connection (device eth0 not available because profile is not compatible with device (mismatching interface name)).
```

Am I doing something wrong?

---

### Post by r00ty2 on 2022-04-21
ok, spent like 2 days and was about to give up on NetworkManager


The following command is redundant 
```
nmcli con add type tun ifname tap0 mode tap ip4 10.10.10.10/24
```


Then instead of ```
nmcli con add type bridge-slave ifname tap0 master br0
``` it should be ```
nmcli con add type tun mode tap ifname tap0 master br0
``` since [FONT=arial black]bridge-slave[/FONT] is an alias to [FONT=arial black]ethernet[/FONT] profile

---

