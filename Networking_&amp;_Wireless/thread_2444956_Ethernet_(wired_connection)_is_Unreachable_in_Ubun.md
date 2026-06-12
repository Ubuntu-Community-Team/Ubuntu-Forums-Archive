---
title: "Ethernet (wired connection) is Unreachable in Ubuntu 16.04"
date: 2020-06-06
forum: Networking &amp; Wireless
---

### Post by jackee1234 on 2020-06-06
I have a system dual boot with Windows 10 and Ubuntu 16.04. 
Windows 10 can access the internet, but Ubuntu 16.04 can't.
I have checked in Windows 10 where WOL is not enabled on the ethernet.
And you can see that the ethernet status (eno1) is up in Ubuntu 16.04.

Below are some results
```
```
$ ping 8.8.8.8
connect: Network is unreachable
```
```
From above you can see it's not domain server problem (Indeed, before that I have tried changing `/etc/resolv.conf` to include line `nameserver 8.8.8.8` and it does not work and I found out that it's not domain server problem)


   ```
 $ ip link
    1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
        link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00 2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc pfifo_fast state UP mode DEFAULT group default qlen 1000
        link/ether 18:31:bf:ce:35:39 brd ff:ff:ff:ff:ff:ff 3: enp14s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DEFAULT group default qlen 1000
        link/ether 18:31:bf:ce:35:3a brd ff:ff:ff:ff:ff:ff 5: br-e5e68b901b8d: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
        link/ether 02:42:bc:39:1c:1b brd ff:ff:ff:ff:ff:ff 6: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
        link/ether 02:42:90:09:22:e9 brd ff:ff:ff:ff:ff:ff


```
$ ifconfig -a
br-e5e68b901b8d Link encap:Ethernet  HWaddr 02:42:bc:39:1c:1c  
          inet addr:172.18.0.1  Bcast:172.18.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


docker0   Link encap:Ethernet  HWaddr 02:42:90:09:22:ec  
          inet addr:172.17.0.1  Bcast:172.17.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


eno1      Link encap:Ethernet  HWaddr 18:31:bf:ce:35:3c  
          inet6 addr: fe80::fd89:7b2:8432:3e66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50635 (50.6 KB)  TX bytes:10704 (10.7 KB)
          Interrupt:20 Memory:fb600000-fb620000 


enp14s0   Link encap:Ethernet  HWaddr 18:31:bf:ce:35:3c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Memory:fb300000-fb37ffff 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:37180 errors:0 dropped:0 overruns:0 frame:0
          TX packets:37180 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14199410 (14.1 MB)  TX bytes:14199410 (14.1 MB)
```
```
Any comments is welcome and highly appreciated!

---

### Post by wildmanne39 on 2020-06-06
Hello and welcome to the forum.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by jackee1234 on 2020-06-07
I solve through this method:
	Assume the interface is called eno1 (found from command `ifconfig`)


>     - sudo service network-manager stop
>     - sudo ifconfig eno1 up
>     - sudo dhclient eno1
>     - sudo service network-manager start




from: [https://askubuntu.com/a/1010564/78528](https://askubuntu.com/a/1010564/78528)

---

