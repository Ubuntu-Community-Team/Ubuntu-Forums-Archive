---
title: "ubuntu laptop wont resolves names of home network server to itself"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by bobdobbs on 2008-10-31
Strange one this.

My ubuntu laptop resolves the names of the hosts on my webserver to itself.

Of course thing that I thought was that I'd messed up the hosts files.
The host file on my laptop is pretty simple:

127.0.0.1     localhost
127.0.0.1     ubuntu-laptop
127.168.1.81  myserver

The server's hosts file is nearly as simple:

127.0.0.1    localhost
127.0.0.1    myserver


However, when I try to access myserver from ubuntu-laptop, the laptop gets web service from itself.
If I try to get web service from myserver by it's ip address, I do succeed.

What am I doing wrong?

---

### Post by Iowan on 2008-10-31
Typically, 127.0.0.1 is used for localhost, and 127.0.1.1 is used for the hostname. 127.168.x.x seems (to me, at least) an unusual address.  Again with tradition, "usual" local addresses are 192.168.x.x. (or 10.x.x.x)

---

### Post by bobdobbs on 2008-10-31
Here are my updated and corrected hosts files:
My laptop ( with the resolution problem)
127.0.0.1	localhost
127.0.0.1	endorra
127.168.1.81	myserver
127.168.1.81	myserver2


And the server:

127.0.0.1       localhost
127.0.0.1       myserver
127.0.0.1       myserver2

192.168.1.75    endorra    #laptop

the problem remains - 
When I want to access the server from the laptop by name, the laptop gets service from itself.

---

