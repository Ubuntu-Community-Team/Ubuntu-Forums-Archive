---
title: "Stuck with bridging two networks"
date: 2018-02-17
forum: Networking &amp; Wireless
---

### Post by abdulsattar86 on 2018-02-17
My /etc/network/interfaces file looks as follows




    # interfaces(5) file used by ifup(8) and ifdown(8)
    auto lo
    iface lo inet loopback
    
    auto enp0s3
     iface enp0s3 inet dhcp 
    
    auto enp0s8
    iface enp0s8 inet static
      address 172.16.3.1
      netmask 255.255.255.0
      network 172.16.3.0
      broadcast 172.16.3.255
    
    auto br0
    iface br0 inet static
      address 172.16.3.1
      network 172.16.3.0
      netmask 255.255.255.0
      broadcast 172.16.3.255
      bridge-ports enp0s3 enp0s8




Also here is my `ifconfig -a` output


    br0       Link encap:Ethernet  HWaddr 08:00:27:8c:24:a6  
              inet addr:172.16.3.1  Bcast:172.16.3.255  Mask:255.255.255.0
              inet6 addr: fd00:1cab:c070:ac02:a1de:6a17:c002:5915/64 Scope:Global
              inet6 addr: 2607:fea8:5df:fc3d:a00:27ff:fe8c:24a6/64 Scope:Global
              inet6 addr: fe80::a00:27ff:fe8c:24a6/64 Scope:Link
              inet6 addr: fd00:1cab:c070:ac02:a00:27ff:fe8c:24a6/64 Scope:Global
              inet6 addr: 2607:fea8:5df:fc3d:a1de:6a17:c002:5915/64 Scope:Global
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:348 errors:0 dropped:0 overruns:0 frame:0
              TX packets:234 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:29858 (29.8 KB)  TX bytes:30385 (30.3 KB)
    
    enp0s3    Link encap:Ethernet  HWaddr 08:00:27:8c:24:a6  
              inet addr:192.168.0.27  Bcast:192.168.0.255  Mask:255.255.255.0
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:9490 errors:0 dropped:0 overruns:0 frame:0
              TX packets:12650 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:4736518 (4.7 MB)  TX bytes:1455119 (1.4 MB)
    
    enp0s8    Link encap:Ethernet  HWaddr 08:00:27:97:d3:2c  
              inet addr:172.16.3.1  Bcast:172.16.3.255  Mask:255.255.255.0
              UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
              RX packets:7839 errors:0 dropped:0 overruns:0 frame:0
              TX packets:2292 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:545550 (545.5 KB)  TX bytes:250033 (250.0 KB)
    
    lo        Link encap:Local Loopback  
              inet addr:127.0.0.1  Mask:255.0.0.0
              inet6 addr: ::1/128 Scope:Host
              UP LOOPBACK RUNNING  MTU:65536  Metric:1
              RX packets:2069 errors:0 dropped:0 overruns:0 frame:0
              TX packets:2069 errors:0 dropped:0 overruns:0 carrier:0
              collisions:0 txqueuelen:1000 
              RX bytes:174076 (174.0 KB)  TX bytes:174076 (174.0 KB)






However when I try to `ping -I enp0s8 192.168.0.27` I don't get any reply back. Also nothing shows up in tcpdump on enp0s3 interface. Can you please advise me what am I missing?

I am trying to do this in VirtualBox but perhaps that shouldn't matter that much in this case unless I am mistaken . Again, any help will be appreciated!

---

