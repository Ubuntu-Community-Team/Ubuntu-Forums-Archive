---
title: "Wireless Routing issue"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by p1ruj3 on 2008-10-14
I think the problem is my routing table...

evdo connection works great but randomly routes my internal ip 10.10.0.xx over the ppp0 interface causing the connection to be terminated by my isp (verizon)

ics works fine in windows and the routing table appears to be different

linux routing table

```

Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
66.174.66.4     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
10.0.0.0        0.0.0.0         255.0.0.0       U     0      0        0 eth0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0

```

windows routing table
```
 
Network Destination Netmask Gateway Interface Metric
0.0.0.0 0.0.0.0 70.219.141.12 70.219.141.12 1
66.174.67.4 255.255.255.255 70.219.141.12 70.219.141.12 1
70.219.141.12 255.255.255.255 127.0.0.1 127.0.0.1 50
70.255.255.255 255.255.255.255 70.219.141.12 70.219.141.12 50
127.0.0.0 255.0.0.0 127.0.0.1 127.0.0.1 1
192.168.0.0 255.255.255.0 192.168.0.1 192.168.0.1 20
192.168.0.1 255.255.255.255 127.0.0.1 127.0.0.1 20
192.168.0.255 255.255.255.255 192.168.0.1 192.168.0.1 20
224.0.0.0 240.0.0.0 192.168.0.1 192.168.0.1 20
224.0.0.0 240.0.0.0 70.219.141.12 70.219.141.12 1
255.255.255.255 255.255.255.255 70.219.141.12 70.219.141.12 1
255.255.255.255 255.255.255.255 192.168.0.1 192.168.0.1 1
Default Gateway: 70.219.141.12


```
are you sure its not in how my routing tables are look at the two above there are differences  arnt there?


how do i add this route in linux? ```
 66.174.67.4 255.255.255.255 70.219.141.12 70.219.141.12 1
 
```

i have tried adding my own routes 
```

sudo /sbin/route del default gw 0.0.0.0
sudo /sbin/route del default
sudo /sbin/route add default gw $PPP_LOCAL

```

so it now looks like this but not the same as windows table
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
66.174.67.4     0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
10.10.0.0       0.0.0.0         255.255.255.0   U     0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         70.215.214.135  0.0.0.0         UG    0      0        0 ppp0

```

detailed troubleshooting for over 9 months i cannot get this figured out thanks in advance for any help

(ics is configured properly no network manager have tried different things and am clearing my ip tables everytime)

[http://ubuntuforums.org/showthread.php?t=906126&page=7](http://ubuntuforums.org/showthread.php?t=906126&page=7) has config details or i can put them here let me know what info you want...

---

