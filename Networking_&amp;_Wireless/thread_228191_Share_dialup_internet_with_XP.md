---
title: "Share dialup internet with XP"
date: 2006-08-02
forum: Networking &amp; Wireless
---

### Post by orlox on 2006-08-02
I'm trying to share internet through  network connection with computers that have windows XP. The network is already set up, but I don't know how to share dialup internet....

Here is the output of the commands "ifconfig" and "route -n":

```

root@PCPABLO:/home/pablo# ifconfig
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:303 errors:0 dropped:0 overruns:0 frame:0
          TX packets:303 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:32384 (31.6 KiB)  TX bytes:32384 (31.6 KiB)

ppp0      Link encap:Point-to-Point Protocol
          inet addr:200.29.55.242  P-t-P:172.31.51.198  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:3284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3
          RX bytes:2010986 (1.9 MiB)  TX bytes:638935 (623.9 KiB)



root@PCPABLO:/home/pablo# route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
172.31.51.198   0.0.0.0         255.255.255.255 UH    0      0        0 ppp0
0.0.0.0         0.0.0.0         0.0.0.0         U     0      0        0 ppp0


```

---

### Post by hasimir44 on 2006-08-02
Try this..
 
1. Save your current firewall setup: 
sudo iptables-save > firewall.old

2. Setup your LAN NIC: 
sudo ifconfig eth0 192.168.100.1

3. Setup the new "firewall" (note: 6 commands): 
sudo iptables --flush                          
sudo iptables --table nat --flush
sudo iptables --delete-chain                    
sudo iptables --table nat --delete-chain
sudo iptables --table nat --append POSTROUTING --out-interface ppp0 -j MASQUERADE
sudo iptables --append FORWARD --in-interface eth0 -j ACCEPT         

4. Enable ip forwarding: 
sudo echo 1 > /proc/sys/net/ipv4/ip_forward 

5. Setup your windows xp box: 
assign a static ip of 192.168.100.5
assign a subnet of 255.255.255.0
assign dns as 172.31.51.198    - I think :) 


You can find your dns server by running: 
nslookup [www.google.com](www.google.com)

- from the linux box once it's connected to the internet. if the 172.31.51.198 doesn't work, then use what it says after "Server: "

hopefully this works.. i got my laptop to work as a router between my lan, but it's been a while. 

if this doesn't work or you determine that it's too unsecure (or whatever..) you can revert back by running: 
iptables-restore firewall.old

so no harm done..

---

