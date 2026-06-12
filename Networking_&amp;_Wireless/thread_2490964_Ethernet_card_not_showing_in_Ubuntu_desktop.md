---
title: "Ethernet card not showing in Ubuntu desktop"
date: 2023-09-21
forum: Networking &amp; Wireless
---

### Post by bengtfalke on 2023-09-21
I have installed Ubuntu server 22.04 with Nextcloud and Ubuntu-desktop on a Mac Mini from 2012. Everything works fine and I
can use the internet and another computer on the network can access the Nextcloud server.

However I need to setup a static IP address so I with a dyndns can access the server from another location. But the wired network does for some reason not show up in Ubuntu desktop.

If i run ifconfig:
bengt@falkenc:~$ ifconfig
enp1s0f0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.178  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::aa20:66ff:fe45:7f88  prefixlen 64  scopeid 0x20<link>
        ether a8:20:66:45:7f:88  txqueuelen 1000  (Ethernet)
        RX packets 4501  bytes 3657667 (3.6 MB)
        RX errors 0  dropped 375  overruns 0  frame 0
        TX packets 2380  bytes 487521 (487.5 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 16  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 923  bytes 79019 (79.0 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 923  bytes 79019 (79.0 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

And ip a:
bengt@falkenc:~$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp1s0f0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether a8:20:66:45:7f:88 brd ff:ff:ff:ff:ff:ff
    inet 192.168.0.178/24 metric 100 brd 192.168.0.255 scope global dynamic enp1s0f0
       valid_lft 600894sec preferred_lft 600894sec
    inet6 fe80::aa20:66ff:fe45:7f88/64 scope link 
       valid_lft forever preferred_lft forever
3: enx002500ed421e: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 00:25:00:ed:42:1e brd ff:ff:ff:ff:ff:ff

Any advice is appreciated...

---

### Post by chili555 on 2023-09-21
> But the wired network does for some reason not show up in Ubuntu desktop.It's a common issue when you install server and then desktop. Please check:```
cat /etc/netplan/*.yaml
```Perhaps this will be helpful. [https://askubuntu.com/questions/1485311/server-connects-to-wifi-internet-but-theres-no-wifi-adapter-in-the-config-setti/1485327#1485327](https://askubuntu.com/questions/1485311/server-connects-to-wifi-internet-but-theres-no-wifi-adapter-in-the-config-setti/1485327#1485327)

---

### Post by bengtfalke on 2023-09-22
That worked! Thank you so much for your help!

---

