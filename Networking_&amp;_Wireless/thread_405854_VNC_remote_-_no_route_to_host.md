---
title: "VNC remote - no route to host"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by rajko on 2007-04-10
Hi everyone, I have small problem. I can not connect to vnc server running on ubuntu from outside of local subnet 192.168.0.x. Ii works fine within but from outside I get 
vncviever: ConnectToTcpAddr: connect: No route to host
I tested from outside client and ports are opened as follows:
5900/tcp  open     vnc            VNC (protocol 3.7)
5901/tcp  open     vnc            VNC (protocol 3.3)

when I connect with telnet to port 5900:
Trying 83.131.xx.xx...
Connected to name.dyndns.org.
Escape character is '^]'.
RFB 003.007

so it can connect and route is found... :confused: 

I'm behind NAT  and port forwarding is active (I can connect as shown :) )

rajko

---

### Post by bnuytten on 2007-04-21
Since you are able to telnet to port 5900 and get the initial string from the VNC server this looks more like an application issue. Unless you have to deal with multiple network interfaces and asynchronous routing or so...

---

