---
title: "[SOLVED] SSH &amp;amp; VNC trouble"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by csogilvie on 2008-08-26
I'm new... please bear with me!  =)

I've recently set up a home system (so I don't kill the new webserver) with Ubuntu 8.04LTS 64-bit.

I have configured SSH on the machine as well as tightvncserver so I can access session:1 from outside my home network.  (And opened up port 22 on my firewall)

While inside my home network, I can ssh to the machine and vnc to it (using Putty) and use the computer through the gnome desktop.

However, I'm now outside trying to get in.  I launch putty, use my SSH2 key, and I'm into the bash.  I'm using the exact same tunnelling settings that I would use inside my home network... But my VNC viewer can't seem to make a connection.  (RealVNC)

Anybody have any thoughts as to what I should try next?

---

### Post by Fire_Chief on 2008-08-26
Could you share the tunnelling settings you are trying to use? I've done some remote tunnelling before so hopefully I can help.

---

### Post by jigsaws on 2008-08-26
Which ports do you tunnel?

You should tunnel for example:
Source port: Local 5900 to 127.0.0.1:5900
Source port: Local 5901 to 127.0.0.1:5901
(remember to click Add in putty)

and after ssh to your server and try to connect by VNC to 127.0.0.1:5901 (for :1 screen)

Firewall should have open 22 for the network and all ports for 127.0.0.1.

---

### Post by csogilvie on 2008-08-29
Thanks!  Your suggested tunneling fixed the problem.

Cheers

---

### Post by ssam on 2008-08-29
why do people make it so complicated. most VNC programs have a -via option. this automatically makes a tunnel, and send the traffic down it.

```
vncviewer -via $REMOTEHOST localhost:0
```

this makes a tunnel to $REMOTEHOST and connect to the vnc server that $REMOTEHOST calls localhost i.e. $REMOTEHOST.

---

