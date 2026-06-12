---
title: "How to configure internet connection Wi-Fi @ Home"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by rachitbhatia on 2009-07-23
How to configure internet connection Wi-Fi @ Home. I had used it using proxy server IP address. but now i want ot use it @ my home using wi-fi ...but a cross is shown over the net symbol on desktop . I even ticked " direct connection" in internet proxy. I am a totally new user of ubuntu

---

### Post by mapes12 on 2009-07-23
post the output of:


```
cat /etc/network/interfaces
```


```
cat /etc/hosts
```


```
cat /etc/resolv.conf
```


```
iwconfig
```


```
ifconfig
```

---

### Post by Rockky on 2009-07-24
Code:
cat /etc/network/interfaces 
output:
auto lo
    iface lo inet loopback
 
Code:
cat /etc/hosts
output:
127.0.0.1 localhost
   127.0.1.1 rachit-laptop
   # The following lines are desirable for IPv6 capable hosts
   ::1 ip6-localhost ip6-loopback
   fe00::0 ip6-localnet
   ff00::0 ip6-mcastprefix
   ff02::1 ip6-allnodes
   ff02::2 ip6-allrouters
   ff02::3 ip6-allhosts

Code:
cat /etc/resolv.conf
output:
### BEGIN INFO
    #
    # Modified_by:  NetworkManager
    # Process:      /usr/bin/NetworkManager
    # Process_id:   5155
    #
    ### END INFO
 
    nameserver 172.16.20.1

Code:
iwconfig
output:
lo        no wireless extensions.
 eth0      no wireless extensions.

Code:
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1d:09:5c:f3:c5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:16 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1348 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1348 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:67400 (65.8 KB)  TX bytes:67400 (65.8 KB)

---

### Post by mapes12 on 2009-07-24
It looks like your wifi device is not supported in Linux. These links may help you fix the problem or locate a compatible wifi adapter:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported?highlight=(supported)|(wifi)#head-e669905d73a32156274930398b3d3c3468508d45)

---

### Post by LookTJ on 2009-07-24
Please post the output of:
```
lspci
```

---

