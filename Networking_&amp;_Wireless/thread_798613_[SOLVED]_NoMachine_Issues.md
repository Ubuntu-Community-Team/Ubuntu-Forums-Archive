---
title: "[SOLVED] NoMachine Issues"
date: 2008-05-18
forum: Networking &amp; Wireless
---

### Post by stalker145 on 2008-05-18
I seem to have borked my setup somehow and I'm wondering if anyone may have a clue as to what I did or how to fix it.

Basically, I'm trying to connect (RDP/VNC) using NoMachine to my home server. Whenever I attempt this, I get ```
NX> 203 NXSSH running with pid: 23850
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: xxx.xxx.xxx.xxx on port: 22
NX> 202 Authenticating user: nx
NX> 208 Using auth method: publickey
HELLO NXSERVER - Version 3.2.0-7 - LFE
NX> 105 Hello NXCLIENT - Version 3.2.0
NX> 134 Accepted protocol: 3.2.0
NX> 105 Set shell_mode: shell
NX> 105 Set auth_mode: password
NX> 105 Login 
NX> 101 User: **************
NX> 102 Password: ***************
NX> 500 Authentication failed
NX> 500 Remote host identification has changed
NX> 500 Offending key in /usr/NX/home/nx/.ssh/known_hosts
NX> 999 Bye.
NX> 280 Exiting on signal: 15
```

I have tried purging and reinstalling the NoMachine debs on the local machine (I haven't gotten to trying it on the server). I've deleted all of the config files from .nx in my home directory as well.

As odd as it sounds (and I'll mention it anyway) the only thing that I've done that is out of the ordinary is that I installed the NoMachine software on my fiancee's XP desktop and accessed my server yesterday.

I can't seem to find a directory named ```
/usr/NX/home/nx/.ssh
``` and I have already gone and deleted *all* keys from the known_hosts file in my home directory.

Going back to the XP computer, I receive the same error as noted above. 

<sigh>

Rebooted the server. Haven't installed anything out of the ordinary. Positive it's the same computer and there is no "man in the middle" attack.

Thanks to anyone that can help.

---

### Post by rdoolen on 2008-05-18
I would guess that this was caused by a recent upgrade of openssh that fixed a security issue. I think you need to fix the known_hosts file on the server. The only way I know how to do this is to rename the file (as a backup in case it really messes something up). The file should be ~/.ssh/Known_hosts, but from your post it might be the file in the /usr/NX/ directory.

If there is a way to fix this file, I would like to hear about it. Deleting it feels like overkill.

---

### Post by jetsam on 2008-05-18
There's a recent solved thread on the same issue that might help:

[http://ubuntuforums.org/showthread.php?t=794136&highlight=nomachine]("http://ubuntuforums.org/showthread.php?t=794136&highlight=nomachine")

---

### Post by stalker145 on 2008-05-18
> **jetsam said:**
> There's a recent solved thread on the same issue that might help:

[http://ubuntuforums.org/showthread.php?t=794136&highlight=nomachine]("http://ubuntuforums.org/showthread.php?t=794136&highlight=nomachine")

Thanks for pointing me in the right direction. That is exactly what I needed. Here I was looking all over the client and the fault was with the server.

---

