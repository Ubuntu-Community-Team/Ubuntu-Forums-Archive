---
title: "creating a fake interface in ubuntu14.10 - Cannot find device &quot;dummy1&quot;"
date: 2015-05-08
forum: Networking &amp; Wireless
---

### Post by eyaln on 2015-05-08
Hi, 

I was trying this code in order to create fake interfaces in ubuntu14.10 
I need it for bonding

sudo /sbin/modprobe dummy numdummies=3
sudo /sbin/ip link set name eth10 dev dummy0
sudo /sbin/ifconfig eth10 hw ether 00:10:10:ff:ff:ff


sudo /sbin/ip link set name eth11 dev dummy0:1
sudo /sbin/ifconfig eth10 hw ether 00:11:11:ff:ff:ff

while I got eth10 , I couldn't get eth11 , I tried it both with dummy0:1 and dummy1
in both cases the result was the same

Cannot find device "dummy1"
Any ideas?

eth10 seems OK though
ifconfig -a

eth10     Link encap:Ethernet  HWaddr 00:10:10:ff:ff:ff  
          BROADCAST NOARP  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

