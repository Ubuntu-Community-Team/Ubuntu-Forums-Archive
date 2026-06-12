---
title: "&quot;Cable unplugged&quot; error from a machine I'm viewing... ***remotely***."
date: 2019-05-31
forum: Networking &amp; Wireless
---

### Post by Jonathan_Nowacki on 2019-05-31
So I connect to my Ubuntu machine remotely with nomachine and it tells me the internet cable is unplugged.

I'm not sure how to begin to trouble shoot this.  Any help?

I can ping other local computers.
  
"no machine" circled on the top left.

[IMG]https://i.ibb.co/8sYFZTj/No-Machine-Weirdness.jpg[/IMG]

---

### Post by kpatz on 2019-05-31
If you run **ip link show** on the machine, what do you get?

Is there more than one NIC?  Wireless?  Any VPNs?  Maybe one is connected and one isn't, and you're seeing the cable disconnected message on the one that isn't.

Is this machine a VM or a physical box?

How does NoMachine connect through your router or firewall?

---

### Post by Jonathan_Nowacki on 2019-06-03
> **kpatz said:**
> If you run **ip link show** on the machine, what do you get?

results:

```
ip link show
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN mode DEFAULT group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: p1p1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DEFAULT group default qlen 1000
    link/ether 78:ac:c0:3d:48:87 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 78:ac:c0:3d:48:86 brd ff:ff:ff:ff:ff:ff
4: virbr0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default qlen 1000
    link/ether 52:54:00:4d:f2:34 brd ff:ff:ff:ff:ff:ff
5: virbr0-nic: <BROADCAST,MULTICAST> mtu 1500 qdisc fq_codel master virbr0 state DOWN mode DEFAULT group default qlen 1000
    link/ether 52:54:00:4d:f2:34 brd ff:ff:ff:ff:ff:ff
6: docker0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc noqueue state DOWN mode DEFAULT group default 
    link/ether 02:42:7f:5a:32:20 brd ff:ff:ff:ff:ff:ff

```


>  Is there more than one NIC?

The motherboard has two RJ45 female connectors on the back.

>   Wireless?  Any VPNs?

No and no.  It's a Hewlett Packard Z800 workstation with no wifi.

>  Is this machine a VM or a physical box?

Physical box.  HP Z800 sitting right next to me.

>  How does NoMachine connect through your router or firewall?

Windows Laptop -> router -> Ubuntu Server (Hewlett Packard Z800 workstation)

---

### Post by kpatz on 2019-06-03
> **Jonathan_Nowacki said:**
> results:

```

2: p1p1: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc mq state DOWN mode DEFAULT group default qlen 1000
    link/ether 78:ac:c0:3d:48:87 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP mode DEFAULT group default qlen 1000
    link/ether 78:ac:c0:3d:48:86 brd ff:ff:ff:ff:ff:ff

```
...The motherboard has two RJ45 female connectors on the back.
You have 2 Ethernet NICs.  One (named p1p1) is not connected.  The other (eth1) is.  You're probably seeing the cable disconnected on the p1p1 interface.

What version of Ubuntu are you running?  eth1 hasn't been a default interface name since something like 14.04.

---

