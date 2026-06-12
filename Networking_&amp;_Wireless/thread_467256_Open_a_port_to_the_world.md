---
title: "Open a port to the world ?"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by A.I. BOT on 2007-06-07
Im trying to open the port 43279 so people can telnet to my Python server script.

I have opened my router and tried to open port 43279 but it only gives me the option of opening it to my Home Network and not everyone.

I dont have a firewall, only my router. So is there any other way I can open the port to the world?

Thanks.

---

### Post by tturrisi on 2007-06-07
> **A.I. BOT said:**
> Im trying to open the port 43279 so people can telnet to my Python server script.

I have opened my router and tried to open port 43279 but it only gives me the option of opening it to my Home Network and not everyone.

I dont have a firewall, only my router. So is there any other way I can open the port to the world?

Thanks.

Port Forwarding
[http://portforward.com/](http://portforward.com/)

---

### Post by A.I. BOT on 2007-06-07
Yes I try to forward it to my INTERNAL IP address.

[http://img409.imageshack.us/img409/7959/screenshot1yp1.png](http://img409.imageshack.us/img409/7959/screenshot1yp1.png) <-- As seen here in my Router's Web Interface.

However, when I try to connect via "telnet {MY EXTERNAL IP} 43279" it says connection refused.

Thanks.

---

### Post by tturrisi on 2007-06-07
did you config telnetd to listen on that port or is is still using the default port 22?

---

### Post by Hendrixski on 2007-06-07
:-) you _do_  have a firewall in your Ubuntu though.  It's called IPTables.  If you'd like to configure it you can do so from the command line or just download a graphical frontend for it... like Firestarter.  I think you can use that to open a port, which by default all ports in Ubuntu are closed.

---

### Post by A.I. BOT on 2007-06-07
@tturrisi: telnet isent listining to the port, my Python server is, the telnet connect to it. The only way I can connect to my server is  "telnet {localhost|INTERNAL IP} 43279" ... but using my ENTERNAL IP instead of my INTERNAL IP wont let me connect.

@Hendrixski: I tried a few IPTables commands like "sudo iptables -A INPUT -p tcp -dport 43279 -j ACCEPT" etc, but no luck. It dosent open the port (I dont think, accoring to netstat -ant anyways).

---

### Post by Honig on 2007-06-07
> **A.I. BOT said:**
> @tturrisi: telnet isent listining to the port, my Python server is, the telnet connect to it. The only way I can connect to my server is  "telnet {localhost|INTERNAL IP} 43279" ... but using my ENTERNAL IP instead of my INTERNAL IP wont let me connect.

Your router is not going to work when you connect with the external IP address from a workstation behind the router. To test it you need to try from someplace that is not behind your own router.

---

### Post by A.I. BOT on 2007-06-07
I have had some friends try to connect to me via "telnet {EXTERNAL IP} 43279" and they instantly get shot down with a "connection refused" error.

---

### Post by tturrisi on 2007-06-07
> **A.I. BOT said:**
> @tturrisi: telnet isent listining to the port, my Python server is, the telnet connect to it. The only way I can connect to my server is  "telnet {localhost|INTERNAL IP} 43279" ... but using my ENTERNAL IP instead of my INTERNAL IP wont let me connect.

@Hendrixski: I tried a few IPTables commands like "sudo iptables -A INPUT -p tcp -dport 43279 -j ACCEPT" etc, but no luck. It dosent open the port (I dont think, accoring to netstat -ant anyways).
I don't follow your logic.
If you have a server, and you telnet (client) into that server, then that server MUST have the telnet daemon (server) running.  The telnet daemon has a config file that is probably setup to use the default telnet ports.

This is just like a www server.  The default port for the www server is port 80, but if you want to use a different port, then you have to config the www server to listen on that desired port, else clients won't be able to connect to the server.

see the section here re Basic Telnet Security:
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch16_:_Telnet,_TFTP,_and_xinetd](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch16_:_Telnet,_TFTP,_and_xinetd)

---

### Post by Mr. C. on 2007-06-08
> **tturrisi said:**
> If you have a server, and you telnet (client) into that server, then that server MUST have the telnet daemon (server) running.  The telnet daemon has a config file that is probably setup to use the default telnet ports.


This is incorrect.  Telnet is a simple 7-bit ASCII communication protocol.  By default, telnet will attempt to reach the well known telnet port of 23.  A telnet server is only required if you want to establish a telnet shell session.

It is common practice to give a telnet client a port number argument to communicate with a server that speaks simple ASCII commands.  The command:

```
$ telnet localhost 25
```

would connect to a local SMTP server.

MrC

---

### Post by Honig on 2007-06-08
It seems to me you are doing everything correct on your router. Most home routers that use NAT do not route correctly back to their own external IP address, so that explains why you cannot connect to the external IP address from your home computer. 

Are you certain that your ISP is allows connections to that port? Have you opened a forward temporarily on a more common port that the ISP might leave open and had your friends try to connect then?

---

### Post by A.I. BOT on 2007-06-08
I am not sure, what are some common ports I can try?

---

### Post by Honig on 2007-06-08
Try 23 (normally: telnet), 22 (normally: ssh), or 80 (http). Those are generally pretty common ports. If your ISP is blocking ports though, they might not work either. You might get your friends to just ping your external address and see if they even get a response to that. 

If your ISP is blocking all inbound ports, then it is going to be very hard if not impossible for your friends connect.

---

### Post by A.I. BOT on 2007-06-08
Yeah, tried them ports, I get a permission denied error. If I sudo my script, I get a "address is already in use" for 22, 23 and 80, I dont have a SSH or telnet server so I dont see how its in use.

---

### Post by Mr. C. on 2007-06-08
Ports below 1024 are privileged ports.  You must be root to use them.

If your system says port 22 is in use, then you either have an SSH server running, or some other program listening on that port.  If you don't know what it is, use lsof -i to find out.  Likewise for the others.

MrC

---

