---
title: "multicast loop back not working (client and server on same machine)"
date: 2013-10-02
forum: Networking &amp; Wireless
---

### Post by ilia2 on 2013-10-02
hi all,


first post for me here :)


i am trying to do the following:

(A)one process send msg to via multicast to address 225.3.1.1
(X,Y)two processes listen to the multicast address
(A->X,Y)

all processes on the same box, Ubuntu 10.4

the problem when i send the msg i can see it in tcpdump 
msg received in lo 

but the processes that listen to the socket in blocking mode(X,Y) does not receive the msg

after searching the internet i found that i have to enable the multicast and add a default route

ifconfig lo multicast
oute add -net 224.0.0.0 netmask 240.0.0.0 dev lo

i also added [FONT=Consolas]IP_MULTICAST_LOOP [/FONT][FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]on the sockets
[/FONT]

did i miss something?
is it possible under linux?

the same solution and code worked perfectly on windows

[FONT=Verdana, Arial, Tahoma, Calibri, Geneva, sans-serif]
[/FONT]

---

### Post by elopin on 2013-10-20
I would like to connect my problem with this one. I tried many advices but nothing works. 

I need to test multicast applications only on localhost without any network connection. My classmates works fine on Windows, but I work only when I have neither ethernet or wifi connection. When I try ping 224.0.0.1 multicast i get NETWORK UNREACHABLE.

If I set "sudo ip route add 224.0.0.0/4 dev eth0" and ping 224.0.0.1 there is no respond and all packet lost.

I tried /etc/sysctl.conf various modification according to various threads on various forums but I'm still lost.

How to set eth0 interface to corectly send and receive multicast packets without network connection.

All in all, how to do it that multicast works only on localhost without network connection?

Thanks for reply.

---

### Post by elopin on 2013-10-22
ELOPIN - SOLVED

This solved my problem.

[http://lcm.googlecode.com/svn-history/r522/www/reference/lcm/multicast-setup.html](http://lcm.googlecode.com/svn-history/r522/www/reference/lcm/multicast-setup.html)

abstract
[TABLE="width: 100%"]
[TR]
[TD][h=2]UDP Multicast Setup[/h] UDP Multicast Setup &#8212; Getting maximum performance on your LAN or local host
 [/TD]
 [TD="align: right"][/TD]
 [/TR]
[/TABLE]
  [h=2]Using LCM on a single host[/h] Since LCM uses UDP Multicast as a transport mechanism, a valid      multicast route must always be defined.     This means that to use LCM, even for inter-application communication on a     single host, *you must have a multicast-enabled network     interface*.  If your computer is already connected to the     Internet, LCM will generally "just work" because the default route will     allow LCM to find the correct network interface for multicast     traffic.
 If your computer is not connected to any network, you may need to      explicitly enable multicast traffic by adding multicast entries to your     system's routing table.  On Linux, you can setup the loopback interface for     multicast with the following commands:
     sudo ifconfig lo multicast
    sudo route add -net 224.0.0.0 netmask 240.0.0.0 dev lo
     Remember, you must always do this to use LCM if your machine     is *not connected* to any external network.

---

