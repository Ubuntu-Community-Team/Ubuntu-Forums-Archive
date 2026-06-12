---
title: "Need help configuring two NICs one dynamic and one static using netplan"
date: 2022-02-25
forum: Networking &amp; Wireless
---

### Post by asteway on 2022-02-25
I am running a server in virtualbox with two NICs. 
-enp0s3 configured as NAT
-enp0s8 configured as a host only adapter in the 172.16.0.1 network. 

```

# This is the network config written by 'subiquity'
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: yes
    enp0s8:
      dhcp4: no
      addresses: [172.16.0.112/24]
      gateway4: 172.16.0.1
      nameservers:
              addresses: [8.8.8.8, 8.8.4.4]



```

I can access hosts in the host only network, but not on the DHCP. enp0s3 actually acquires 10.0.2.2 IP. 
Not sure what I am missing.

---

### Post by TheFu on 2022-02-25
Routing table please?
Does the virtualbox manual say that both can be used in a single VM?

---

### Post by asteway on 2022-02-26
@[COLOR=#000000]TheFu, this is the configuration I use all the time on virtualbox. The only thing new is this is an Ubuntu 20.04 server and I have to use netplan.
[/COLOR]
```

ip route show
default via 172.16.0.1 dev enp0s8 proto static 
default via 10.0.2.2 dev enp0s3 proto dhcp src 10.0.2.15 metric 100 
10.0.2.0/24 dev enp0s3 proto kernel scope link src 10.0.2.15 
10.0.2.2 dev enp0s3 proto dhcp scope link src 10.0.2.15 metric 100 
172.16.0.0/24 dev enp0s8 proto kernel scope link src 172.16.0.112 



ip link
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 08:00:27:d0:9e:33 brd ff:ff:ff:ff:ff:ff
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP mode DEFAULT group default qlen 1000
    link/ether 08:00:27:50:d2:fc brd ff:ff:ff:ff:ff:ff

ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host 
       valid_lft forever preferred_lft forever
2: enp0s3: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:d0:9e:33 brd ff:ff:ff:ff:ff:ff
    inet 10.0.2.15/24 brd 10.0.2.255 scope global dynamic enp0s3
       valid_lft 86164sec preferred_lft 86164sec
    inet6 fe80::a00:27ff:fed0:9e33/64 scope link 
       valid_lft forever preferred_lft forever
3: enp0s8: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 08:00:27:50:d2:fc brd ff:ff:ff:ff:ff:ff
    inet 172.16.0.112/24 brd 172.16.0.255 scope global enp0s8
       valid_lft forever preferred_lft forever
    inet6 fe80::a00:27ff:fe50:d2fc/64 scope link 
       valid_lft forever preferred_lft forever

```

---

### Post by TheFu on 2022-02-26
I think the issue is having 2 default routes.  Remove the one you don't want.
BTW, please edit the post above to use 'code tags' so the output lines up correctly.
```
$ ip r |column -t
```
is helpful too. I miss the output from **route -n**. It was so much easier to read. Newer programs should actually BE better.

---

### Post by crackswebs on 2022-02-27
thanks i solved my issue by your post

---

### Post by asteway on 2022-02-27
@theFu, I don't think this is a default route issue. 
1. 172.16.0.1 and 10.0.2.15 are the same machine. 
2. the host only configuration on VirtualBox carries out a static routing to the 172.16.0.1 default route.

Plus, this is a configuration I use all the time.

---

### Post by asteway on 2022-02-28
@TheFu, I guess you were right. gateway4 was the offending line.

Here's my new config that works fine.

```

# This is the network config written by 'subiquity'
network:
  version: 2
  ethernets:
    enp0s3:
      dhcp4: yes
    enp0s8:
      addresses: [172.16.0.112/24]
      nameservers:
        addresses: [4.2.2.2, 8.8.8.8]

ip route show
default via 10.0.2.2 dev enp0s3 proto dhcp src 10.0.2.15 metric 100 
10.0.2.0/24 dev enp0s3 proto kernel scope link src 10.0.2.15 
10.0.2.2 dev enp0s3 proto dhcp scope link src 10.0.2.15 metric 100 
172.16.0.0/24 dev enp0s8 proto kernel scope link src 172.16.0.112 




```

---

### Post by foxsquirrel on 2022-02-28
What version of Ubuntu and Kernel.

Mine has to have routes clearly defined


routes:
   - to: default
    via: 111.111.1.111

I can see in yours it some how it has routes. It must be getting if from the dhcp4: yes ??

---

