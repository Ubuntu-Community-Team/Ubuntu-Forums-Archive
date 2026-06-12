---
title: "HUGE problems with my ADSL line... [HEEEELP MEEEEE]"
date: 2007-07-01
forum: Networking &amp; Wireless
---

### Post by Mapkoz on 2007-07-01
hi everybody.
I am having problems with my ADSL line since I have upgraded to kubuntu feisty....
simply, i cannot connect to the internet if I am not connected to a LAN line (like when I am at uni). 
At home, when I do try to connect I give 
```
sudo pppoeconf
```
but at the end af the procedure I cannot connect. when I try to ping some site he just tells me "unknown host"
I tried to look at my resolv.conf file, this is all I have into that
```
nameserver 85.37.17.4 
nameserver 85.38.28.70 
```
these are the businness DNS for that line, so I tried so substitute them with the normal user one...no way, everytime he just re-writes the old ones...
these are some of the commands I gave
```
marco@cliff:~$ plog

Jun  9 00:14:18 cliff pppd[6756]: PPP session is 25555

Jun  9 00:14:18 cliff pppd[6756]: Using interface ppp5

Jun  9 00:14:18 cliff pppd[6756]: Connect: ppp5 <--> eth0

Jun  9 00:14:39 cliff pppd[6756]: Remote message: Authentication failed

Jun  9 00:14:39 cliff pppd[6756]: PAP authentication failed

Jun  9 00:14:39 cliff pppd[6756]: Connection terminated.


marco@cliff:~$ ifconfig ppp0
ppp0      
Link encap:Point-to-Point Protocol
          
inet addr:87.4.45.198  P-t-P:192.168.100.1  
Mask:255.255.255.255
          
UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1492  Metric:1
          
RX packets:34 errors:0 dropped:0 overruns:0 frame:0
          
TX packets:3 errors:0 dropped:0 overruns:0 carrier:0
          
collisions:0 txqueuelen:3
          
RX bytes:1538 (1.5 KiB)  TX bytes:54 (54.0 b)
```
I also tried 
```
kdesu kate /etc/resolv.conf
```
(add the new dns) and then 
```
sudo chmod a-w /etc/resolv.conf
```
but no way... it keeps on re-writing the old DNS
the I tried
```
sudo chattr +1 /etc/resolv.conf
```

but no way again...
what can I do???
Please developers help me!!!
Anybody help me!!!

---

### Post by Mapkoz on 2007-07-01
nobody can help me?

---

