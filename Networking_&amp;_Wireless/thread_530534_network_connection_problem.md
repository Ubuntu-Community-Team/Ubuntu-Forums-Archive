---
title: "network connection problem"
date: 2007-08-20
forum: Networking &amp; Wireless
---

### Post by kefei on 2007-08-20
Hi all,

I install Ubuntu 704 using wubi, dualbooting with my windows XP on Dell optiplex 320 (intel pentium D).

My problem is I can't connect to internet neither using Live CD or the installed one. HOWEVER, I do have IP ADDRESS allocated to me by DHCP, which is different to the one allocated to me when I work under windows.

Also, I CAN see other computers in the LAN by exploring "Networks" in Ubuntu. I CAN ping my own IP but I can't ping other PC's IP in my LAN.

Please help me out! Please see my ifconfig -a results as follows:

Thanks!

------------

eth0      Link encap:Ethernet  HWaddr 00:1A:A0:0B:24:64  
          inet addr:129.171.57.44  Bcast:255.255.255.255  Mask:255.255.255.0
          inet6 addr: fe80::21a:a0ff:fe0b:2464/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:101843 errors:0 dropped:0 overruns:0 frame:0
          TX packets:898 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:8266736 (7.8 MiB)  TX bytes:119594 (116.7 KiB)
          Interrupt:21 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:210 errors:0 dropped:0 overruns:0 frame:0
          TX packets:210 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:70047 (68.4 KiB)  TX bytes:70047 (68.4 KiB)

---

### Post by jakev383 on 2007-08-20
What does "iptables -L" show? And can we see the output of "route"?
Thanks.

---

### Post by kefei on 2007-09-13
> **jakev383 said:**
> What does "iptables -L" show? And can we see the output of "route"?
Thanks.

Sorry for the delays of responding! I've been out of town for quite a long time.

I'm unable to iptable -L directly without sudo. The following is the result of sudo iptables -L
[FONT="Courier New"]
kefei@ubuntu:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
[/FONT]

---

