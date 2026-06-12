---
title: "Install vnc on ubuntu 8.10 with ssh"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by ThaMaster on 2010-01-03
Hi all

I have a server with ubuntu 8.10 on it.
Now i want to install a vnc server on it.
I only have ssh access.
I'm a real noob with ubuntu+ssh i hope some one can tell me what to do. i tried some tutorials but that wasn't working.

i hope to hear something soon.

---

### Post by spiderbatdad on 2010-01-03
I believe 8.10 comes with vino installed. To access it; something like :
```
ssh -L 5900:localhost:5900 <user@server>
```
Have you tried the X option?```
ssh -X user@serverip
```

---

### Post by ThaMaster on 2010-01-03
i think thats not what i want

I want to install vnc on ubuntu with ssh.
Connect to it with windows.

---

### Post by Cheesemill on 2010-01-03
Do you actually have a GUI installed on the server?

You say you only have SSH access, did you install this server or is it hosted?
Without a GUI there is nothing to VNC to.

---

### Post by bodhi.zazen on 2010-01-03
On Ubuntu, enable the shared desktop option, be sure to use a strong password.

System -> Preferances -> Remote desktop.

Then install teh ssh server

```
apt-get install ssh
```

Again, be sure to use a strong password, or preferably ssh keys

[SSH/OpenSSH/Keys - Community Ubuntu Documentation]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") 

You then use Putty from windows

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

You need to forward port 22 (ssh) on your router.

---

### Post by Cheesemill on 2010-01-03
> **bodhi.zazen said:**
> On Ubuntu, enable the shared desktop option, be sure to use a strong password.

System -> Preferances -> Remote desktop.


He only has SSH access.

---

### Post by bodhi.zazen on 2010-01-03
> **Cheesemill said:**
> Do you actually have a GUI installed on the server?

You say you only have SSH access, did you install this server or is it hosted?
Without a GUI there is nothing to VNC to.

That is not exactly true, it depends on teh vnc server. You can install vnc4server and that does not require X on the server. You ssh in and if needed start the server.

The default vnc server, vino, requires both X and that a user is logged in.

---

### Post by ThaMaster on 2010-01-03
> **Cheesemill said:**
> Do you actually have a GUI installed on the server?

You say you only have SSH access, did you install this server or is it hosted?
Without a GUI there is nothing to VNC to.


it is hosted:)

---

### Post by Cheesemill on 2010-01-03
> **ThaMaster said:**
> it is hosted:)

In that case it doesn't have a GUI installed that you can VNC onto.

You would first have to install a GUI before you think about VNC, this may not be possible if it's a VPS rather than an actual machine, you may be stuck with SSH.

Bodhi knows more about this than I do though.

---

### Post by bodhi.zazen on 2010-01-03
If you do not have X (a graphical desktop) I suggest you use ssh -X

You can do this from windows , but you need Putty and XMing (XMing is an X server for windows). Both Putty and XMing run from a flash drive so they are portable.

[http://sourceforge.net/projects/xming/](http://sourceforge.net/projects/xming/)

TO be honest, most servers are managed wither over ssh (you mainly edit config files with VIM / nano / or emacs). If you want a graphical app take a look at something like webmin.

If you *must* vnc, you should look at tightvnc server

[https://help.ubuntu.com/community/VNC/Servers#tightvncserver](https://help.ubuntu.com/community/VNC/Servers#tightvncserver)

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

You will then need to install a light weight X window manager such as Fluxbox, but honestly, VNC would be my last option.

---

### Post by ThaMaster on 2010-01-03
Thank you all for your fast reply and information.
Gonna give it a try tomorrow.

---

