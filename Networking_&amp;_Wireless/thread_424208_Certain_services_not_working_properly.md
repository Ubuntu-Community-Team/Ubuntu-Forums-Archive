---
title: "Certain services not working properly"
date: 2007-04-26
forum: Networking &amp; Wireless
---

### Post by Das Oracle on 2007-04-26
I am trying to ftp into another computer on the network with a static IP. I have done this several times before prior to a fresh install of feisty. ftp and smb do not work and just refuse connection, upon ping it reverts to my local ip address and tracepath does the same thing:  

```
PING 192.168.0.103 (192.168.0.103) 56(84) bytes of data.
From 192.168.0.106 icmp_seq=2 Destination Host Unreachable
From 192.168.0.106 icmp_seq=3 Destination Host Unreachable
From 192.168.0.106 icmp_seq=4 Destination Host Unreachable

--- 192.168.0.103 ping statistics ---
6 packets transmitted, 0 received, +3 errors, 100% packet loss, time 5000ms
, pipe 3

```

any thoughts?

*the 106 is my IP address while 103 is the computer i am trying to reach, i forgot to mention that i can reach this computer just fine from other computers on my network

---

