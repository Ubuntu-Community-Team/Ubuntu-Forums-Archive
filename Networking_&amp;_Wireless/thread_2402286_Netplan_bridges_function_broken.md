---
title: "Netplan bridges function broken"
date: 2018-09-28
forum: Networking &amp; Wireless
---

### Post by prjpet on 2018-09-28
Hi,

I'm using Ubuntu 18.04 server and trying to use the following netplan config based on info from thread: [URL="https://ubuntuforums.org/showthread.php?t=2386080"]https://ubuntuforums.org/showthread.php?t=2386080
[/URL]
```
network:
  version: 2
  renderer: networkd
  ethernets:
    eno1:
      dhcp4: yes
      dhcp6: no
      nameservers:
        addresses: [127.0.0.1]


    eno2:
      dhcp4: no


  bridges:
    xenbr0:
      interfaces: []
      addresses: [10.0.0.1/24]

```

Once I hit "netplan apply", I get the following output if I check my network settings:

```
peter@bordeaux:~$ ip add1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: eno1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether 34:17:eb:ec:20:46 brd ff:ff:ff:ff:ff:ff
    inet *.*.*.*/27 brd 145.100.104.127 scope global dynamic eno1
       valid_lft 86071sec preferred_lft 86071sec
12: vif9.0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 32
    link/ether fe:ff:ff:ff:ff:ff brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fcff:ffff:feff:ffff/64 scope link 
       valid_lft forever preferred_lft forever
16: vif11.0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 32
    link/ether fe:ff:ff:ff:ff:ff brd ff:ff:ff:ff:ff:ff
    inet6 fe80::fcff:ffff:feff:ffff/64 scope link 
       valid_lft forever preferred_lft forever
29: eno2: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN group default qlen 1000
    link/ether 34:17:eb:ec:20:47 brd ff:ff:ff:ff:ff:ff
30: xenbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN group default qlen 1000
    link/ether 7a:60:f2:8a:ba:e7 brd ff:ff:ff:ff:ff:ff



```

Meaning my xenbr0 is **without an address and DOWN state. **

Trying to delete the bridge using brctl provides the following result:

```

sudo brctl delbr xenbr0[sudo] password for peter: 
bridge xenbr0 is still up; can't delete it

```
[B]
Still up? Eh? Never been up!!! 
[/B]
1. The thread above contains false information, please remove. 
2. Netplan and networkd does something really weird with the bridge since it's down, without an address, and can't be controlled.

Please help any support is appreciated.

---

