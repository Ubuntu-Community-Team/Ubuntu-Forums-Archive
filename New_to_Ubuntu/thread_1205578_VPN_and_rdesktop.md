---
title: "VPN and rdesktop"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by supererki on 2009-07-06
i have sucessfully established a VPN connection and now i want to take over the remote desktop. so i use the Remote Desktop Viewer. but it cannot take over the desktop. gives me error that connection was closed. anyway. it seems to be using port 5900 by default, i want to use 3389, but i cant change it! i tried <host>:3389 but it doesnt work. so can i change this port or is there a better application ?

---

### Post by dgoosens on 2009-07-06
I have the same "problem" 
I use tsclient instead and that works fine...

---

### Post by diablo75 on 2009-07-06
If you want to change the default VNC listening port on the server check this out:

[http://davestechsupport.com/blog/2009/06/14/howto-change-vncs-listen-port-in-ubuntu/](http://davestechsupport.com/blog/2009/06/14/howto-change-vncs-listen-port-in-ubuntu/)

If you're using SSH to establish your private connection, there's an easy way to connect VNC via SSH with one command:

```
vncviewer -via root@192.168.222.1 localhost:0
```

In the above example, "root" is the username you wish to login as.  192.168.222.1 is the IP address of the server you're SSHing into.

"localhost" means the client PC, or rather, the PC you are physically sitting in front of.

Since you're intended to change the default listen port, you'll probably have to modify it some, and I'm not sure what it would look like exactly.  To be honest, I wouldn't change the default listening VNC port, but instead block 5900, allow 22 for SSH (or whatever you'd like) then use the above command as usual.  That way the only way a VNC connection could be established is via SSH.

---

### Post by superprash2003 on 2009-07-06
you would have to restart the vnc service after making changes..

---

### Post by dgoosens on 2009-07-07
hi,

do you want to use Remote Desktop or a VNC viewer...
the two are not the same and for the VNC viewer to work you should have a VNC server installed on the other machines...

tsclient allows you to connect remotely to any kind of computer... and it works great...

---

### Post by The Cog on 2009-07-07
Just to add - TSC is in Applications->Internet->Terminal Server Client. Or use **rdesktop x.x.x.x** from the command line. Use these for MS Remote Desktop protocol.

Use Remote Desktop Viewer for the VNC remote conbtrol protocol.

Confusing naming there, I feel.

---

