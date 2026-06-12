---
title: "no result when ping-ing a openvpn interface"
date: 2015-10-05
forum: Networking &amp; Wireless
---

### Post by esolve on 2015-10-05
I'm following the tutorial to learn openvpn
[http://backreference.org/2010/03/26/tuntap-interface-tutorial/](http://backreference.org/2010/03/26/tuntap-interface-tutorial/)


by following the steps of the part: `let's try it`
I use openvpn to create an interface tun2, and assign an IP to it


    sudo openvpn --mktun --dev tun
    sudo ip link set tun2 up
    sudo ip addr add 10.0.0.1/24 dev tun2


then I use tcpdump to monitor the packets flowing through `tun2`


    sudo tcpdump -i tun2 




and I input `ping 10.0.0.2` on terminal, but I see nothing on tcpdump output, also the `ping` is stuck without outputing anything. 


in the tutorial, it says since the tun2 interface is assinged an IP 10.0.0.1/24, then the ping packet with 10.0.0.2 should pass through `tun2` coz there will be a default route. But this doesn't happen in my case. 


    #sudo route -n
    Kernel IP routing table
    Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
    0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
    10.0.0.0        0.0.0.0         255.255.255.0   U     0      0        0 tun2
    192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0




And it is also strange that the ping is stuck without outputing anything. In the tutorial, the results should be like:


    # ping 10.0.0.2
    PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
    From 10.0.0.1 icmp_seq=2 Destination Host Unreachable
    From 10.0.0.1 icmp_seq=3 Destination Host Unreachable

---

