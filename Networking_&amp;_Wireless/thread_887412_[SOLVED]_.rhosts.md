---
title: "[SOLVED] .rhosts"
date: 2008-08-12
forum: Networking &amp; Wireless
---

### Post by sulekha on 2008-08-12
Hi,


 can any one give an example for configuring .rhosts file  so that 
 i can allow some trusted computers in my LAN to access my ubuntu machine via telnet,ssh without having to enter password

---

### Post by sulekha on 2008-08-12
but i am not even able to ssh into my machine 

i am getting the message:

ssh: connect to host 192.168.40.230 port 22: Connection refused

 which services will i have to enable ?

---

### Post by Iowan on 2008-08-12
Maybe a silly question, but worth asking: SSH-server is installed?

---

### Post by sulekha on 2008-08-13
> **Iowan said:**
> Maybe a silly question, but worth asking: SSH-server is installed?

i am able to ssh into other ubuntu machine from my machine and the o/p of the command  "which ssh" gives /usr/bin/ssh. BTW i had installed sshfs on my machine to access remote directories , has it got anything to do with this ?

---

### Post by davidshere on 2008-08-13
To allow other users to access your machine via ssh, you need the package openssh-server installed.  The following will install openssh-server if you don't have it, update it if it's out of date, or tell you it's already the latest version if that is the case.

```
sudo apt-get install open-ssh-server
```

We're assuming that you do have this package installed, I think, because you apparently are having the problem that other users have to enter a password before accessing your machine via ssh.  Presumably they already have access, are entering a password, and gaining access.

For other users to access your machines via ssh without a password, you want this:

[http://www.linuxproblem.org/art_9.html](http://www.linuxproblem.org/art_9.html)

This is relatively dangerous from a security perspective, (anyone with access to the remote machine also has access to your machine) and should be avoided.

You can also use samba file sharing package to share over a local network without a password:

```
sudo apt-get install samba
```

I think samba could be easier to configure.

---

