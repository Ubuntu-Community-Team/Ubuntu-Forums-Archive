---
title: "Cannot Connect to In-Home Dedicated Server"
date: 2015-03-26
forum: Networking &amp; Wireless
---

### Post by tra561 on 2015-03-26
I have a Half Life 2 DeathMatch dedicated Server that I recently setup. It is connected via ethernet to my router.

I have a second computer (both computers are running ubuntu) that I'm running the Client Version of HL2 DM on (connected to the router via wireless connection


The client cannot detect my server. 


I Attempted local port forward for the 27015/27020 TCP ports on both computers. 


I belive the 2 computers are not connected via LAN or VPN, Any Suggestions on How to connect them?

---

### Post by JohnnyComeL8ly on 2015-03-26
Try pinging your server from the client PC.  

Also, try connecting manually, by using the IP address of the LAN server.  

What is the output of "sudo ufw status"?

---

### Post by tra561 on 2015-03-26
(192.168.1.6) is my server
(192.168.1.5) is my client


For the Ping (from client):


```

jim@Fedora:~$ ping -c 10 192.168.1.6
PING 192.168.1.6 (192.168.1.6) 56(84) bytes of data.
64 bytes from 192.168.1.6: icmp_seq=1 ttl=64 time=0.967 ms
64 bytes from 192.168.1.6: icmp_seq=2 ttl=64 time=1.43 ms
64 bytes from 192.168.1.6: icmp_seq=3 ttl=64 time=0.965 ms
64 bytes from 192.168.1.6: icmp_seq=4 ttl=64 time=1.77 ms
64 bytes from 192.168.1.6: icmp_seq=5 ttl=64 time=0.995 ms
64 bytes from 192.168.1.6: icmp_seq=6 ttl=64 time=9.94 ms
64 bytes from 192.168.1.6: icmp_seq=7 ttl=64 time=0.963 ms
64 bytes from 192.168.1.6: icmp_seq=8 ttl=64 time=0.966 ms
64 bytes from 192.168.1.6: icmp_seq=9 ttl=64 time=0.934 ms
64 bytes from 192.168.1.6: icmp_seq=10 ttl=64 time=0.970 ms

--- 192.168.1.6 ping statistics ---
10 packets transmitted, 10 received, 0% packet loss, time 9010ms
rtt min/avg/max/mdev = 0.934/1.992/9.948/2.665 ms
jim@Fedora:~$ 

```

And sfw (also from client):


```

jim@Fedora:~$ sudo ufw status
Status: active

To                             Action      From
--                                    ------      ----
27015                        ALLOW       Anywhere
27020                        ALLOW       Anywhere
27005                        ALLOW       Anywhere
27015 (v6)                 ALLOW       Anywhere (v6)
27020 (v6)                 ALLOW       Anywhere (v6)
27005 (v6)                 ALLOW       Anywhere (v6)

jim@Fedora:~$ 

```


Maybe My Provider (version) simply doesn't allow servers?

---

### Post by tra561 on 2015-03-26
Works!



Connecting via the "connect 192.168.1.6" commmand Connects.


Thank you.

---

