---
title: "Tunnel Firefox through SSH?!?"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by markbusu on 2008-12-13
Hi all,

Not sure if this is possible,

Basically got Ubuntu Server on site, and need to get to Firefox which is installed in the server to access a local site (Since tunneling the port is not working..)

I tried using ssh -x and execute firefox but get:

Error: no display specified

Is this possible?

Thanks!

---

### Post by tigerstripedcat on 2008-12-13
Sure this is possible, but it will probably be really slow.  You might want to look into nomachine as a better alternative.  Make sure you can get any X-app over ssh, try "xclock" or "xterm".  If you don't get those up, then you have a problem with your setup.  I think it's "ssh -X" with a capital "X", I think.  If it still doesn't work, you'll need to check your /etc/ssh/sshd_config and ssh_config on server and client and make sure that X is being forwarded.

TSC

---

### Post by bluefrog on 2008-12-13
cannot forward X11 if X is not installed.

---

### Post by Rolcol on 2008-12-13
This may not be a solution but if you want Firefox on your computer to use an SSH connection as its tunnel, it can be done.

First: Open up an ssh connection and specify to open up the port for tunneling (I use port 55555). ```
ssh -D 55555 user@host
```

Second: Have Firefox use the tunnel.  Go to Edit -> Preferences -> Advanced -> Network -> "Configure how Firefox connects to the Internet [Settings]".  Mark the "Manual proxy configuration" option.  In the "SOCKS Host:" field type in "localhost" and the port should be set to the same one you specified in step one (55555 in my case).  Remove the text inside of the "No Proxy for: " field if you want localhost requests to get pages from the ssh server.

---

### Post by The Cog on 2008-12-13
That should be a capital x:
**ssh -X servername**

And make sure you shut your local firefox down first, or it will somehow just use that instead. I don't understand how it does that.

---

