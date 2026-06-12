---
title: "running program from inetd.conf"
date: 2008-03-10
forum: Networking &amp; Wireless
---

### Post by dsbw on 2008-03-10
I'm trying to initiate a program when people telnet into my server:

telnet stream tcp nowait root.root /usr/sbin/tcpd /usr/sbin/in.telnetd -h -L usr/sbin/dgamelaunch 

But when I telnet in, I get:

telnetd: /usr/sbin/dgamelaunch: No such file or directory

The program is there and it is executable as root, but as a regular user I get a "cannot change root directory" error (which I think is what I want).

Any ideas?

---

### Post by SpaceTeddy on 2008-03-11
> **dsbw said:**
> telnet stream tcp nowait root.root /usr/sbin/tcpd /usr/sbin/in.telnetd -h -L usr/sbin/dgamelaunch 


have you tired it with the absulte path - i.e. this entry ?
telnet stream tcp nowait root.root /usr/sbin/tcpd /usr/sbin/in.telnetd -h -L **[SIZE="3"]/[/SIZE]**usr/sbin/dgamelaunch

also, i am not sure, but maybe you'd need to start a shell before you load the programm, so the enviroment gets initialized.... maybe ?

---

### Post by dsbw on 2008-03-14
That didn't work (I had actually tried it shortly after) but it made me realize that it wasn't pointing to the right program. It seems to work now.

Ish.

(Separate video issues.)

Thanks!

---

