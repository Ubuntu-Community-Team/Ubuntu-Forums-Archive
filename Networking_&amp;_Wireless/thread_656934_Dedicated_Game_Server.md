---
title: "Dedicated Game Server"
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by The Titan on 2008-01-03
I have 2 computers on a network, 1 i like to call a server and the other is my personal computer both of which are running Ubuntu 7.10.  I have a quake server running on the "server" computer and i can connect to it just fine from the other computer on the network but i cannot connect to it from anywhere outside the network.  I did netstat and it dosent say that it is listening.


```

root@theTemple:~# netstat -an
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:2183            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:720             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:3583            0.0.0.0:*               LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::21                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
tcp6       0      0 ::ffff:192.168.0.2:22   ::ffff:192.168.0.:32857 ESTABLISHED
tcp6       0      0 ::ffff:192.168.0.2:22   ::ffff:192.168.0.:41933 ESTABLISHED
udp        0      0 0.0.0.0:1024            0.0.0.0:*                          
udp        0      0 0.0.0.0:2049            0.0.0.0:*                          
udp        0      0 0.0.0.0:1026            0.0.0.0:*                          
udp        0      0 0.0.0.0:10000           0.0.0.0:*                          
udp        0      0 0.0.0.0:420             0.0.0.0:*                          
[COLOR="Red"]udp        0      0 0.0.0.0:27960           0.0.0.0:*  [/COLOR]                        
udp        0      0 0.0.0.0:717             0.0.0.0:*                          
udp        0      0 0.0.0.0:111             0.0.0.0:*                          
udp        0      0 0.0.0.0:759             0.0.0.0:*                          
Active UNIX domain sockets (servers and established)
Proto RefCnt Flags       Type       State         I-Node Path
unix  2      [ ACC ]     STREAM     LISTENING     6931     /var/run/mysqld/mysqld.sock
unix  2      [ ]         DGRAM                    3961     @/com/ubuntu/upstart
unix  2      [ ACC ]     STREAM     LISTENING     3962     @/com/ubuntu/upstart/logd
unix  2      [ ]         DGRAM                    4062     @/org/kernel/udev/udevd
unix  2      [ ]         DGRAM                    55948    /dev/log
unix  2      [ ACC ]     STREAM     LISTENING     7380     /var/run/proftpd/proftpd.sock
unix  2      [ ]         DGRAM                    13861    
unix  2      [ ]         DGRAM                    7456     
unix  2      [ ]         DGRAM                    7339     
unix  2      [ ]         DGRAM                    6928     
unix  2      [ ]         DGRAM                    6834     

root@theTemple:~# netstat -an | grep LISTEN
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:2183            0.0.0.0:*               LISTEN     
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:720             0.0.0.0:*               LISTEN     
tcp        0      0 0.0.0.0:3583            0.0.0.0:*               LISTEN     
tcp6       0      0 :::80                   :::*                    LISTEN     
tcp6       0      0 :::21                   :::*                    LISTEN     
tcp6       0      0 :::22                   :::*                    LISTEN     
unix  2      [ ACC ]     STREAM     LISTENING     6931     /var/run/mysqld/mysqld.sock
unix  2      [ ACC ]     STREAM     LISTENING     3962     @/com/ubuntu/upstart/logd
unix  2      [ ACC ]     STREAM     LISTENING     7380     /var/run/proftpd/proftpd.sock


```


i am a complete idiot when it comes to things like this and i am just trying to learn.  Any help is appreciated and if you need more information please just let me know.

thank you,
 Dan

---

### Post by Predator[23rd] on 2008-01-03
you have to tell your gateway/router to forward the quake ports to your "server".

it could be easier for you to setup your routing computer as quake server. in case you "only" have a dsl/cable modem as router check it's manual for port forwarding ...

---

### Post by The Titan on 2008-01-03
Im sorry, i forgot to mention that i do have the ports forwarded, ive also tried doing the "server" computer as DMZ which from what i understands forwards ALL ports to that computer unless specified otherwise(please correct me if im wrong on that). 

 what do you mean by "routing" computer?  i have a modem and an IBM 8223 HUB if that matters.  I dont think the hub is like a router where ports need to be forwarded but im going to look into that. 
[EDIT] Just checked and this is NOT like a router where prots need to be forwarded and such[/EDIT]

 Also, i have a web, mysql, and svn servers running that all work fine outside the network.

  Ive also called my ISP and they said that they dont block any ports because i thought that was the issue also.  Im really stumped man

---

### Post by Predator[23rd] on 2008-01-03
Hi again!

Your network setup is a bit unclear to me. How do you connect to the internet? Is it your modem which manages all the connection details (dials the connection, logs in, etc.) or a certain machine?

---

