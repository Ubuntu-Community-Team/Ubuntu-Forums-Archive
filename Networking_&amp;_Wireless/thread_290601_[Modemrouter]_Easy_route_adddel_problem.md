---
title: "[Modem/router] Easy route add/del problem"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by patrick295767 on 2006-11-01
Hi Ubuntu Users,

I have a very annoying problem of ROUTER, that I cannot solve alone... :confused: :-k 

My pptp connection (INTERNET) to my modem works fine when my Router is not in between.

I wanna make use of my router to be behind my "NAT"/router. 
The router is a ROBOTICS 8003 USR which cannot make it alone the PPTP connnection since static IP is the only way when doing PPTP.
 
So, When I place my router in between, so the IP address becomes with a 192.x.x.x of my pc, I can still ping to modem to make the PPTP connection but nothing comes out.

It s normally quite easy with route add to make it but since I am not expert in that ...

PLEASE COuld someone help me ? What could I try ?

route add ... 
route del ...
I tried knet (that is PPPoE / PPPoA)  and not working


####[COLOR="Red"]**Working/Internet working**[/COLOR]#####   PC <=======> MODEM Xdsl  <== NET
My Working internet gives me 
#route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.25.46.47    0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
10.0.0.138      172.17.116.1    255.255.255.255 UGH   0      0        0 eth0
172.17.116.0    0.0.0.0         255.255.255.0   U     0      0        0 eth0
192.168.75.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
0.0.0.0         172.25.46.47    0.0.0.0         UG    0      0        0 ppp0
```
 
 
 

#### [COLOR="Red"]**NON Working/NO INTERNET**[/COLOR]#####   PC <===> USR Router 8003 <====> MODEM Xdsl <== NET
My Working internet gives me 
#route -n
```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
10.0.0.138      192.168.123.254 255.255.255.255 UGH   0      0        0 eth0
192.168.75.0    0.0.0.0         255.255.255.0   U     0      0        0 vmnet1
192.168.123.0   0.0.0.0         255.255.255.0   U     0      0        0 eth0

```


ping [www.google.com](www.google.com)
gives host not found
ping 10.0.0.138 is still working and possible
 
  
My content of /ETC/PPP/options
```
lock
defaultroute
noipdefault
noauth
asyncmap 0
```


Thank you

Patrick


after
> sudo route add default gateway 192.168.(your router address)

This will get you on the net, get your updates and all should be well.
Reply With Quote

route add default gateway 10.0.0.138 
did not helped :-(

---

### Post by patrick295767 on 2006-11-09
I bought a brand new high-tech router with lot of configuration possibilities

It works now

cheers

---

