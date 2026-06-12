---
title: "Help with tunelling and vnc"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by calsaverini on 2008-05-05
Hi there.

I'm trying to configure a "double tunnel" to access my desktop remotely.

My problem is as follows: my workstation is in an internal network in my university, and I don't have direct SSH access to this computer. Instead, I have SSH access (not privileged) another computer (the server/cluster) and from this machine I can access my workstation.

So I tried the following:
[LIST]
[*]First of all I liberated remote desktop access with vino by the common procedure (System/Preferences/Remote Desktop etc... etc...).

[*]Then I created a tunnel from the server to my workstation, listening to the 5900 port:

```
at SERVER> ssh my_user@my_workstation -L 5900:my_workstation:5900
```

[*] I created a tunnel from my computer at home to my server, listening to the same port:

```
at HOME> ssh my_user@server -L 5900:server:5900
```

[*] Then tried to load the vncviewer:

```
 at HOME> vncviewer localhost:0 
```

[/LIST]

I got the following result:
```

calsaverini ~ $ vncviewer 127.0.0.1:0

VNC Viewer Free Edition 4.1.1 for X - built Sep 10 2007 16:58:22
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.

Tue May  6 00:02:44 2008
 CConn:       connected to host 127.0.0.1 port 5900
 main:        End of stream
calsaverini ~ $ 

```

It connects then the connection is closed without nothing happening.
I can't see the problem in my approach. I never used a double tunnel before, don't know if its possible. 

If someone can help, please reply :).

---

### Post by Monicker on 2008-05-06
This should work for you

```

ssh user@server -L 5900:workstation:5900
```

As long as the server can reach the workstation, it can route your tunnel to it.

---

### Post by kevdog on 2008-05-06
Yes this is possible -- Here is how I see your situation


server <firewall=no inbound ports to server> <---> middle computer <--> client

Basically server needs to login to middle computer via ssh with a reverse tunning method.  Client then logs into middle.  A few other things need to be set up, however take a look at these three links (reading them in order):

[http://gentoo-wiki.com/TIP_SSH_Reverse_Tunnel](http://gentoo-wiki.com/TIP_SSH_Reverse_Tunnel)
[http://security.raffy.ch/Unix_Administration/Services/SSH.php3](http://security.raffy.ch/Unix_Administration/Services/SSH.php3)
[http://www.brandonhutchinson.com/ssh_tunnelling.html](http://www.brandonhutchinson.com/ssh_tunnelling.html)

---

### Post by calsaverini on 2008-05-06
Thanks Monicker. This worked fine.

---

