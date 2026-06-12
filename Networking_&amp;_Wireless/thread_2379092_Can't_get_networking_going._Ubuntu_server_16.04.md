---
title: "Can't get networking going. Ubuntu server 16.04"
date: 2017-11-30
forum: Networking &amp; Wireless
---

### Post by gbritton on 2017-11-30
After startup, I have (screen capture to text,  some errors in conversion):

ip addr
1: lo: <LOOPBACK,UP,LOUER_UP> ntu 65536 qdisc noqueue state UNKNOWN group default qlen 1 link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00 inet 127.0.0.1/8 scope host lo
ualid_lft foreuer preferred_lft foreuer inet6 ::1/128 scope host
ualid_lft foreuer preferred_lft foreuer
2: eth0: <N0-CARRIER,BROADCAST,NULTICAST,UP> ntu 1500 qdisc nq state DOWN group default qlen 1000 link/ether 00:15:5d:00:64:02 brd ff:ff:ff:ff:ff :ff inet 192.168.86.100/24 brd 192.168.86.255 scope global eth0 ualid_lft foreuer preferred_lft foreuer jerrybOubuntu:

sudo ifconfig eth0 

eth0 Link encap:Ethernet HWaddr 00:15:5d:00:64:02
inet addr:192.168.86.100 Beast:192.168.86.255 Nask:255.255.255.0
UP BROADCAST NULTICAST NTU:1500 Netric:l
RX packets:0 errors:0 dropped:0 ouerruns:0 frane:0
TX packets:0 errors:0 dropped:0 ouerruns:0 carrier:0
col1 isions:0 txqueuelen:1000
RX bytes:0 CO.O B) TX bytes:0 (0.0 B)

jerryb@ubuntu:~$ sudo ifup eth0 
Unknown interface eth0

How can eth0 be both DOWN (ip command) and UP (ifconfig command), and  known (ip, ifconfig) and unknown (ifup)?

---

### Post by powersj on 2017-12-01
How are you configuring your network?

The ifup command attempts to read /etc/network/interfaces for the eth0 interface and uses the definition it finds there to bring the device up. However, in your case it is showing up as unknown, because there is no configuration for eth0 there so to it, it is unknown.

Based on the packet count of the ifconfig output it also appears that no traffic or packets were sent at all.

---

### Post by gbritton on 2017-12-01
> **powersj said:**
> How are you configuring your network?

The ifup command attempts to read /etc/network/interfaces for the eth0 interface and uses the definition it finds there to bring the device up. However, in your case it is showing up as unknown, because there is no configuration for eth0 there so to it, it is unknown.

Based on the packet count of the ifconfig output it also appears that no traffic or packets were sent at all.

I'm configuring it manually, from the command line to get it going.  No luck so far.

---

### Post by powersj on 2017-12-01
> **gbritton said:**
> I'm configuring it manually, from the command line to get it going.  No luck so far.

From the output above it looks as if you are trying to assign a static IP address to the device. If that is the case then I would suggest the following:

1. Edit /etc/network/interfaces with the following information:

```

auto eth0
iface eth0 inet static
    address 192.168.86.100
    netmask 255.255.255.0
    gateway 192.168.86.1 # or whatever this actually is on your network

```

2. Run `sudo ifup -a` and see if that gets your networking going

---

