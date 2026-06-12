---
title: "hamachi ubuntu 7.10 cant ping users.."
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by Tusnal on 2007-11-08
hey 

i can connect to the network and see all users online, but i can only ping users if they are in the same local network..

 * [XXXX]
       5.13.214.195     XXX                  
       5.27.20.103      XXXX                   
       5.176.10.154     XXXX                   
     * 5.189.74.187     XXX                   192.168.1.15:1092
       5.40.248.169    XXXXXX          
       5.46.151.130     XXXXX                   
       5.67.198.128     XXXX                 
       5.137.72.193     XXXX                  
     * 5.145.35.154     XXXXX                     62.X.X.199:1967

tusnal@:~$ ping 5.145.35.154
PING 5.145.35.154 (5.145.35.154) 56(84) bytes of data.

--- 5.145.35.154 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2009ms


tusnal@:~$ ping 5.189.74.187
PING 5.189.74.187 (5.189.74.187) 56(84) bytes of data.
64 bytes from 5.189.74.187: icmp_seq=1 ttl=128 time=1.78 ms
64 bytes from 5.189.74.187: icmp_seq=2 ttl=128 time=3.19 ms

--- 5.189.74.187 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 1999ms
rtt min/avg/max/mdev = 1.783/2.490/3.197/0.707 ms


anybody know whats the problem? firestarter is stopped ...

thx!

---

