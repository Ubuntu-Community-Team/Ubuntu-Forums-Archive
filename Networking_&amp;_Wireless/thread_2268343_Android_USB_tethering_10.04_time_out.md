---
title: "Android USB tethering 10.04 time out"
date: 2015-03-08
forum: Networking &amp; Wireless
---

### Post by thombark2 on 2015-03-08
I am trying to use usb tethering from an android phone to a 10.04 Ubuntu laptop.

The phone is recognised as a disconnected wired network.

ip link   gives me

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 16436 qdisc noqueue state UNKNOWN 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:e0:91:3a:9c:53 brd ff:ff:ff:ff:ff:ff
3: wlan0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 00:22:43:07:55:64 brd ff:ff:ff:ff:ff:ff
4: pan0: <BROADCAST,MULTICAST> mtu 1500 qdisc noop state DOWN 
    link/ether 46:cf:fb:8e:79:d3 brd ff:ff:ff:ff:ff:ff
7: usb0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN qlen 1000
    link/ether 02:00:31:56:4d:54 brd ff:ff:ff:ff:ff:ff

then

 sudo dhcpcd usb0

err, usb0: timed out
warn, usb0: using IPV4LL address xxxxx
r@r-laptop:~$ dhcpcd.sh: interface usb0 has been configured with new IP= xxxxx

The phone is running 4.1.2 and the physical cable charges and transfers files between the PC and the phone.

Please tell me what other information to supply in this thread.

TIA

---

