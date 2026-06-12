---
title: "Hostname Problem..."
date: 2009-06-27
forum: New to Ubuntu
---

### Post by stevoo on 2009-06-27
i have recently changed my ISP so a new modem/router was installed. 

I have set the rest 3 routers up correctly and i can see ( ping all the computers as i used too ).

I cannot ping any of  the 3 ubuntu pc's that i have using my hostname.

This was not the case before changing ISP.

I am wondering if i am missing something : 

My hosts 
127.0.0.1 localhost
127.0.1.1 stevooFileServer

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts


stevoo@stevooFileServer:~$ hostname
stevooFileServer
stevoo@stevooFileServer:~$ hostname -a

stevoo@stevooFileServer:~$ hostname -f
stevooFileServer

stevoo@stevooonubuntu:~$ ping  stevooFileServer
ping: unknown host stevooFileServer
stevoo@stevooonubuntu:~$ ping 192.168.10.14
PING 192.168.10.14 (192.168.10.14) 56(84) bytes of data.
64 bytes from 192.168.10.14: icmp_seq=1 ttl=64 time=1.85 ms


Some help perhaps into getting back and fixing this problem that has been puzzling me for some time ! 

Regards 
Stelios

EDIT : When i open up Vinagre i can see on the right stevoo Remote Desktop on stevooFileServer which  points to the hostname correctly. But when i load 'vinagre stevooFileServer' it will not connect me like this.


EDIT AND SOLVED : Seemed my previous router had an auto dns on it and was automatically finding the name of my machines.
Added the ip of my machine on the hosts and that fixed it. 
Thanx to the ones that helped me .... :lolflag:

---

