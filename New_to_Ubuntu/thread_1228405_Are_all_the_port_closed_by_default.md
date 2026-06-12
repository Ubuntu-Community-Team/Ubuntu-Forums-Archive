---
title: "Are all the port closed by default?"
date: 2009-07-31
forum: New to Ubuntu
---

### Post by ozzyprv on 2009-07-31
Before you install port management programs like Firestarter or enabling ufw, are all the port closed by default?
I am at least referring to 9.04.

Thank you.

---

### Post by Katalog on 2009-07-31
I believe there are least a few, two of them being port 80 and 25. One way to check is to go to this web site, put in a port number and see if the system can see you or not:

[http://www.canyouseeme.org/](http://www.canyouseeme.org/)

---

### Post by Sealbhach on 2009-07-31
Yes, all ports are closed:

[http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security](http://www.ubuntu.com/products/whatisubuntu/serveredition/features/security)

***No open ports***

 * By default, Ubuntu does not install default services that listen on open network ports. (The astute reader will note that local network service clients like DHCP and Avahi are the only exception.) This reduces the chances that a system would be compromised through a service that was installed without the explicit knowledge of the administrator. *

Also, a port scan from a site like [Shields Up]("https://www.grc.com/x/ne.dll?bh0bkyd2") gets no results.

.

---

### Post by CatKiller on 2009-08-01
> **Sealbhach said:**
> Yes, all ports are closed:

No they aren't, as is indicated by the quote you included. By default, all ports are open, but no services are listening on any ports. So if you try to connect to port 22 nothing will happen, but if you install an SSH server and try to connect to port 22, the SSH server will respond without port 22 having to be opened.

Port scans will show no results because there's nothing to respond to the port scan on any port. I think the Windows-firewall style nomenclature for this behaviour would be "stealthed."

---

### Post by jacklinux on 2009-08-01
Even if the ports are closed im sure you can open any you like?. Right.

---

### Post by Sealbhach on 2009-08-01
> **jacklinux said:**
> Even if the ports are closed im sure you can open any you like?. Right.

Yes, you can install gufw which will allow you to open any ports you like.

.

---

### Post by ironpoa on 2009-08-03
> **Sealbhach said:**
> Yes, you can install gufw which will allow you to open any ports you like.

.
No, i´ve tried this, and nothing happened. I want to install SVN server, and the port is closed. After put all the rules in the ufw and iptables, and further I disabled all the firewalls, the port still closed. Anyone knows how to open a port without install a service in Ubuntu 9.04 ? Thanks

---

### Post by The Cog on 2009-08-03
> **ironpoa said:**
> No, i´ve tried this, and nothing happened. I want to install SVN server, and the port is closed. After put all the rules in the ufw and iptables, and further I disabled all the firewalls, the port still closed. Anyone knows how to open a port without install a service in Ubuntu 9.04 ? Thanks

Firstly, remove the firewall again. There is no point in trying to install a firewall (whos job is it is to block ports) just so as you can reconfigure it to let them through again afterwards. 

All ports are closed in a default Ubunti install. In order to open a port, an application has to open a listening socket. You do this by starting a server listening on that port number. Subversions normal port number is 3690. So starting a subversion server will open port 3690. You can check if port 3690 is actaully open and listening with the command **netstat -lnt** and looking for an entry like:
> tcp        0      0 0.0.0.0:3690              0.0.0.0:*               LISTENAn address of 0.0.0.0:3690 or :::3690 is fine. If instead you see an address of 127.0.0.1:3690 or ::1:3690 then the server is only listening on the loopback port, and you need to adjust its configuration and restart the service.

If you have installed a firewall, you will additionally have to unblock port 3690 in the firewall the users still won't be able to connect to the open port.

Another test you can do is to try this command from another PC:
**telnet <address> 3690**
where <address> is your server address. There are 3 possible responses:
* connection refused : The port is closed - svn is not listening for connections
* connected : The port is open - svn is accepting connections
* timeout (eventually) : The port is blocked by a firewall, or a network problem is preventing connectivity.

---

### Post by ozzyprv on 2009-08-03
> **Sealbhach said:**
> Yes, all ports are closed:
...
***No open ports***


> **CatKiller said:**
> No they aren't, as is indicated by the quote you included. By default, all ports are open, but no services are listening on any ports.



> **The Cog said:**
> ...
All ports are closed in a default Ubunti install. In order to open a port...


So, are they open or close by default? 
The quote from the official website seems to indicate that, at least for the server version, they are closed.

I thought this was a well known fact that average users knew...and I was just a n00b asking a dumb question ;-)

---

### Post by juancarlospaco on 2009-08-03
if you have 1 port open, you have N ports open, 
because you can connect via SSH, and then connect to any port from localhost to localhost,
but... if you have the *"know how"* you already make the correct security enforcements.

I have 1 port open, for SSH *(not port 22)*, and configured to only accept connection from localhost.
:)

---

### Post by Sealbhach on 2009-08-04
> **ozzyprv said:**
> So, are they open or close by default? 
The quote from the official website seems to indicate that, at least for the server version, they are closed.

I thought this was a well known fact that average users knew...and I was just a n00b asking a dumb question ;-)

It does seem to indicate that but then other people say they're not closed, they're just "not open" so it's all very confusing.

.

---

### Post by The Cog on 2009-08-04
> **Sealbhach said:**
> It does seem to indicate that but then other people say they're not closed, they're just "not open" so it's all very confusing.

.

It is fairly well known that a default Ubuntu install will refuse TCP connection requests. In this sense, the ports are all closed. 

It is also fairly well known that by default iptables, the Ubuntu firewall, allows all packets in and out of the PC. Of course, if connection requests weren't alloowed in or the refusal packets were being blocked by the firewall then you would not get a connection refused message.

Unfortunately, some people use the terms "open" and "closed" to refer to whether the firewall is blocking packets or not. In my opinion this terminology is wrong, and firewall stated should be called "blocking" or "accepting"/"permitting" to avoid confusion with the actual port state. 

In order to be able to connect, of course, a port must be both permitted by any firewall and opened for incoming calls by a program on the PC.

---

