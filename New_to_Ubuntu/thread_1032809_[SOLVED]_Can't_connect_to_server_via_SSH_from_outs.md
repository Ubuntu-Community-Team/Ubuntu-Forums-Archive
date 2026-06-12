---
title: "[SOLVED] Can't connect to server via SSH from outside network"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by ptn107 on 2009-01-06
The problem is exactly that.  I can connect to the server with ssh from within the network but not from the outside.  The server machine is behind a hardware firewall and also Ubuntu's ufw.  Both are configured to allow access.  Since I can connect from within the network I can already suspect ufw is configured correctly (22/tcp).  ssh just hangs at the following prompt indefinitely.

```

phil@phil-desktop:~$ ssh -v -v hostname
OpenSSH_5.1p1 Debian-3ubuntu1, OpenSSL 0.9.8g 19 Oct 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to hostname [ip] port 22.

```
Obviously I've omitted the server's real hostname and ip address for security reasons.

---

### Post by JoshuaRL on 2009-01-06
Are you sure the address is right?  If you're inside the network, you could use an internal IP address and it would work. (IE 192.168.1.5)  But the external address is different, so that wouldn't make any sense to someone outside the network.  Also, the router has to be set up to allow SSH port forwarding to the server you want to SSH into.

---

### Post by blueridgedog on 2009-01-06
How have you tested the hardware firewall to verify that it is not the issue?

You omit the host name, but are you certain that the hostname resolves via public DNS to the external IP of the external firewall?

What other services do you have port forward in from the firewall?  Do they work?

Why not debug with telnet to port 22 to see what dialog unfolds?

---

### Post by albinootje on 2009-01-06
> **ptn107 said:**
> 
Obviously I've omitted the server's real hostname and ip address for security reasons.

Double-check the ip of your hostname.
For example :
```

host yourhost.domain.com
dig yourhost.domain.com

```

Check whether the port is open :
```

sudo apt-get install nmap
nmap -vv yourhost.domain.com -p 22

```
Or simply :
```

nc yourhost.domain.com 22

```

> 
Checking port 22 on my local fileserver :
$ nc ftp 22
SSH-2.0-OpenSSH_4.3p2 Debian-8ubuntu1.5
^C


And.. opening ports on firewall sometimes need an extra firewall rule to enable traffic both ways.
Are you sure your router is port_forwarding correctly to the ip address of your machine in the LAN ?

.. of course all the above mentioned commands should be done outside your LAN, elsewhere, far away :)

---

### Post by ptn107 on 2009-01-06
Found the solution.  Ubuntu's ufw was blocking name domain server on port 53 (tcp/udp).  After a *sudo ufw allow 53* all is well.

(Back when I used Firestarter I never told it to leave open port 53 and everything worked fine.  Why it doesn't work now without explicitly opening port 53 in ufw I just don't know.)

---

