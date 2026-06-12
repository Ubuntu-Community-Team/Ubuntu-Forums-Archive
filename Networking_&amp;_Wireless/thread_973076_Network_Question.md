---
title: "Network Question"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by marsdend on 2008-11-06
Hi all,

I'm considering making a network with several users, I like the idea of the windows network with the active directory where the files and settings follow you around. I do not want to use windows due the great cost of software.

Is it possible to do this with Ubuntu and have a full network with users but also have the GDE installed as well as I am not very good with using code and prefer the mouse and screen lol!

Thanks in advance,
Daniel

---

### Post by superprash2003 on 2008-11-06
i think you mean samba+ LDAP

---

### Post by marsdend on 2008-11-06
> **superprash2003 said:**
> i think you mean samba+ LDAP

Ah, right so does this work well?, and how do i get the desktop environment for the server?

Thanks,
Daniel

---

### Post by Coreigh on 2008-11-06
Here is a link to a How-To for using Samba and LDAP to set up a domain controller with Ubuntu. The tutorial is written for 7.10 but later version of Ubuntu will be similar enough.

[http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10]("http://www.howtoforge.com/openldap-samba-domain-controller-ubuntu7.10")

When you said "how do i get the desktop environment for the server?" Did you mean how do you get a graphical environment on the server? You can add that easily by installing the gnome-desktop package.```
sudo apt-get install gnome-desktop
```
That will make the server nearly the same a the desktop version of Ubuntu. 
If you want something a little "lighter" then this is what I did for a very light-weight GUI desk top.```
sudo apt-get install icewm xdm numlockx xterm xserver-xorg-core xfonts-base
```

---

### Post by marsdend on 2008-11-06
Thats great thanks, what you did is that basically just the desktop without other programs etc?

Thanks,
Daniel

---

### Post by Iowan on 2008-11-06
I got out-typed again, but [this]("http://ubuntuforums.org/showthread.php?t=772796") thread has some desktop options - **Coreigh** already pointed out some/most.

---

### Post by Coreigh on 2008-11-06
Yes Ubuntu server with minimal graphical desktop. If you poke around there are even more minimal systems. You can basicall go all the way down to a system that does little more than start up and show the desktop. Then you are free to install only the specific program you want/need.

---

