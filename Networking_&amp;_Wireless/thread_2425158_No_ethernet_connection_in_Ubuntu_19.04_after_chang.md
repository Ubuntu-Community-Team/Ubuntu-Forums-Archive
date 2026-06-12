---
title: "No ethernet connection in Ubuntu 19.04 after changing motherboard"
date: 2019-08-21
forum: Networking &amp; Wireless
---

### Post by darky1337 on 2019-08-21
[SIZE=6][COLOR=#ff0000]This was fixed, here's how[/COLOR] ->  [https://askubuntu.com/questions/1167334/no-ethernet-connection-in-ubuntu-19-04-after-changing-motherboard](https://askubuntu.com/questions/1167334/no-ethernet-connection-in-ubuntu-19-04-after-changing-motherboard)[/SIZE]



so I've recently built a new PC and kept my SSD/HDD, so everything except my disk drive which has ubuntu installed on it changed. The ethernet connection doesn't work (it used to work on old PC on same ubuntu install), Wi-Fi still works through an USB adapter. Ethernet Connection works on another drive with Windows install so I know the port is working fine, it's only on Ubuntu. I'm looking for a way to get ethernet working without reinstalling ubuntu

**my ifconfig:**

    ```
r0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        inet6 fe80::3c60:9eff:fe5b:8d94  prefixlen 64  scopeid 0x20<link>
        ether 3e:60:9e:5b:8d:94  txqueuelen 1000  (Ethernet)
        RX packets 40313  bytes 5565185 (5.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 1515  bytes 472236 (472.2 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

    lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
            inet 127.0.0.1  netmask 255.0.0.0
            inet6 ::1  prefixlen 128  scopeid 0x10<host>
            loop  txqueuelen 1000  (Local Loopback)
            RX packets 78701  bytes 6556181 (6.5 MB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 78701  bytes 6556181 (6.5 MB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    virbr0: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
            inet 192.168.122.1  netmask 255.255.255.0  broadcast 192.168.122.255
            ether 52:54:00:71:a9:c1  txqueuelen 1000  (Ethernet)
            RX packets 0  bytes 0 (0.0 B)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 0  bytes 0 (0.0 B)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
    
    wlx0024010c2ae6: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
            inet 192.168.1.41  netmask 255.255.255.0  broadcast 192.168.1.255
            inet6 fe80::bf4c:1503:726:f000  prefixlen 64  scopeid 0x20<link>
            ether 00:24:01:0c:2a:e6  txqueuelen 1000  (Ethernet)
            RX packets 73240  bytes 82584023 (82.5 MB)
            RX errors 0  dropped 0  overruns 0  frame 0
            TX packets 51703  bytes 7315654 (7.3 MB)
            TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

as you can see there's no eth0 or eth1 in ifconfig, maybe that has something to do with the problem?

**my /etc/NetworkManager/NetworkManager.conf:**

    ```

    [main]
    plugins=ifupdown,keyfile
    
    [ifupdown]
    managed=false
    
    [device]
    wifi.scan-rand-mac-address=no

```

also, it says 'Ethernet Network device not managed' when I click on the network icon on top right
[B]
SPECS:[/B]

    ```

   ASUS Maximus XI Hero (No Wi-Fi)
   Intel Core i9 9900k @ 3.6Ghz
   MSI GEFORCE RTX 2080 Ti
   32GB DDR4 Ram @ 2666MHz
```

---

### Post by guiverc on 2019-08-21
Also posted on [https://askubuntu.com/questions/1167334/no-ethernet-connection-in-ubuntu-19-04-after-changing-motherboard](https://askubuntu.com/questions/1167334/no-ethernet-connection-in-ubuntu-19-04-after-changing-motherboard)

---

### Post by praseodym on 2019-08-21
Please show the outputs of
```

lspci -nnk
lsmod
```

---

### Post by deadflowr on 2019-08-21
> This was fixed, <snip>
Then please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

It would also be nice to repost the solution here as well.

---

