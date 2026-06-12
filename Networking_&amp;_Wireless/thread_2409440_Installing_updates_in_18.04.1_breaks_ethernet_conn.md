---
title: "Installing updates in 18.04.1 breaks ethernet connection"
date: 2019-01-02
forum: Networking &amp; Wireless
---

### Post by lostsoul1987 on 2019-01-02
Hi all-

I'm running 18.04.1 on a Desktop with only an ethernet connection to the internet.
Everything was working swell I updated my system via apt-get update && upgrade.

Now, the wired connection won't connect and I get a popup saying that the connection
couldn't be activated.

NetworkManager is managing this connection and I have it set all default settings. 

The output of ifconfig is below. Happy to provide output of anymore commands to help diagnose.

```

docker0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet 10.1.10.1  netmask 255.255.255.0  broadcast 10.1.10.255
        ether 02:42:a2:fe:3b:37  txqueuelen 0  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


enp0s25: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet6 fe80::a260:eb73:d6ba:43b2  prefixlen 64  scopeid 0x20<link>
        ether 34:17:eb:ae:af:a1  txqueuelen 1000  (Ethernet)
        RX packets 3431  bytes 747646 (747.6 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 354  bytes 76518 (76.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 20  memory 0xf9100000-f9120000


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 2223  bytes 170143 (170.1 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 2223  bytes 170143 (170.1 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


```

---

### Post by lostsoul1987 on 2019-01-02
This is resolved. I had inadvertently removed a library symlink and it was causing all kinds of havoc.

---

