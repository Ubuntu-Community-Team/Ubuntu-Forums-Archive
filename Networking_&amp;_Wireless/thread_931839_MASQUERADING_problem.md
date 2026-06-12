---
title: "MASQUERADING problem"
date: 2008-09-27
forum: Networking &amp; Wireless
---

### Post by morgonhed on 2008-09-27
Hi!

I have a problem with iptables-masquerading on Ubuntu 8.04.
It should be an easy problem but I seem to be too stupid...

What I want to do is to connect my Palm TX PDA to the internet using my laptop (Thnikpad X30) as a gateway.

My laptop is connected to the internet via UMTS (ppp0 - dynamic IP).
My Palm is connected to my laptop via Wifi (wlan0 - laptop is 192.168.0.1, palm is 192.168.0.2).

My laptop has connectivity.
My Palm can access the laptop (e.g, my palm can access my local apache).
On my palm I have configured the DNS to use my UMTS DNS-server's IP.

So here is what I do (as root):

echo 1 > /proc/sys/net/ipv4/ip_forward
iptables -t nat -A POSTROUTING -s 192.168.0.2 -o ppp0 -j MASQUERADE

Here some output to show my configuration:


mh@x30:~$ cat /proc/sys/net/ipv4/ip_forward 
1
mh@x30:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
mh@x30:~$ sudo iptables -t nat -L
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
MASQUERADE  all  --  192.168.0.2          anywhere            
MASQUERADE  all  --  192.168.0.2          anywhere            

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 


But it does not work.
Packets from my palm seem to get dropped, all connection attempts time out.

What I am missing?

Many thanks!

---

