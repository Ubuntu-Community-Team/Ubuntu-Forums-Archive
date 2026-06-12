---
title: "Sharing internet connection from VPN to wifi router (DHCP relay)"
date: 2017-03-07
forum: Networking &amp; Wireless
---

### Post by flomasters on 2017-03-07
Problem is: wifi users gets IP from ubuntu machine (through wifi router configured as DHCP relay) in range 192.168.137.10-192.168.137.100 with no problem, but without internet access!
Ubuntu have 2 network cards: eth0 is vpn internet, eth2 is connected to wifi router. Ubuntu should work as DHCP client to eth0 and DHCP server to eth2 same time. 
```

*ifconfig*
  eth0      Link encap:Ethernet
           inet addr:172.x.x.x [COLOR=grey]*(dinamic VPN provider IP)*[/COLOR]  Bcast:172.x.x.x  Mask:255.255.255.192
        
eth2      
          inet addr:192.168.137.1  Bcast:192.168.0.255  Mask:255.255.255.0
       
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
       
ppp0      Link encap:Point-to-Point Protocol  
            inet addr:X.X.X.X [COLOR=grey]*(internet white dinamic IP)*[/COLOR]  P-t-P:192.168.111.1  Mask:255.255.255.255
          
```
dhcpd.conf  [https://paste.ubuntu.com/24131474/](https://paste.ubuntu.com/24131474/)
dhcp.conf [https://paste.ubuntu.com/24131484/](https://paste.ubuntu.com/24131484/)
iptables.sav [https://paste.ubuntu.com/24131510/](https://paste.ubuntu.com/24131510/)
rc.local: ```
iptables-restore < /etc/iptables.sav
exit 0
```

tcpdump -ni eth2 -vvv
```
 192.168.137.16.51567 > 192.168.137.1.53: [udp sum ok] 8816+ A? www.google.com.
192.168.137.1 > 192.168.137.16: ICMP host 192.168.137.1 unreachable - admin prohibited
```

---

