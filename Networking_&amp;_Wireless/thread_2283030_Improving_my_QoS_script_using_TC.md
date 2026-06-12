---
title: "Improving my QoS script using TC"
date: 2015-06-18
forum: Networking &amp; Wireless
---

### Post by rpugsley on 2015-06-18
Hi there,

after finally make a script that works on my network, now I'm looking for improvement.

-Is it possible to assign one IP to bypass this QoS(i.e another server)? How can I do that? And what about LAN traffic?
-What changes I need to do on script to set a limit per IP and per Network? Now is only for network (adapter).

Thanks!

```

# Download limit (in mega bits)
DNLD1=45mbit          # DOWNLOAD limit eth1
DNLD2=40mbit          # DOWNLOAD limit eth2

# Upload limit (in mega bits)
UPLD=80mbit          # UPLOAD Limit

# IP address of the machine we are controlling
IP=192.168.1.250     # Host eth1
IP=192.168.0.250     # Host eth2
IP=192.168.4.250     # Host eth4

    tc qdisc del dev eth1 root
    tc qdisc del dev eth4 root
    tc qdisc del dev eth2 root

    tc qdisc add dev eth4 root handle 1: htb default 30
    tc qdisc add dev eth1 root handle 2: htb default 30
    tc qdisc add dev eth2 root handle 3: htb default 30

    tc class add dev eth4 parent 1: classid 1:30 htb rate 1gbit
    tc class add dev eth1 parent 2: classid 2:30 htb rate 1gbit
    tc class add dev eth2 parent 3: classid 3:30 htb rate 1gbit

    tc class add dev eth4 parent 1: classid 1:11 htb rate $UPLD  burst 15k
    tc class add dev eth1 parent 2: classid 2:12 htb rate $DNLD1 burst 15k
    tc class add dev eth2 parent 3: classid 3:13 htb rate $DNLD2 burst 15k

###############
#   iptables  #
###############
# -A POSTROUTING -d 0.0.0.0/0 -j CLASSIFY  --set-class 1:11
# -A POSTROUTING -s 192.168.0.0/24 -j CLASSIFY  --set-class 3:13
# -A POSTROUTING -s 192.168.1.0/24 -j CLASSIFY --set-class 2:12
```

---

