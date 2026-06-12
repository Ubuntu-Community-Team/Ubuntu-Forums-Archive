---
title: "How to do VNC on firewalled VNCSERVER using reverse SSH?"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by frenchn00b on 2010-07-17
Hello,

My friend has windows and vncserver installed, and I have to configure his router. 

The idea is that he makes a SSH reverse, so that I can log into his vncserver, any ideas how to do that ?

---

### Post by Bachstelze on 2010-07-17
Why not just temporarily open the VNC port in the firewall?

---

### Post by frenchn00b on 2010-07-17
because he doesnt know how to configure the router

so the idea is to use:
```


sshrevclient.sh 
#!/bin/sh
# $1 is the user
# $2 shall be -p
# $3 is the port on the target
# ssh -R 7654:localhost:`cat /etc/ssh/sshd_config  | grep Port | cut -d' ' -f 2`  $1 -p $3
ssh -X $1@localhost -p 7654
```


```
sshrevserver.sh 
#!/bin/sh
# user@ip
# $2 shall be -p
# $3 is the port on the target
ssh -X -R 7654:localhost:`cat /etc/ssh/sshd_config  | grep Port | cut -d' ' -f 2`  $1 -p $3
```



here it is:
>  putty.exe -ssh -2 -l USERNAME  -R PORTREVERSE:localhost:5500 HOSTNAMESSHSERVER

---

### Post by diablo75 on 2010-07-17
Why not just do a reverse VNC connection and port forward 5500 on your router to your PC.

You invoke:

```
vncviewer -listen
```

They invoke:

```
x11vnc -connect [your IP/DynDNS hostname]
```

And viola!  You're connected.

You will of course need them to install x11vnc on their machine:

```
sudo apt-get install x11vnc
```

And a vnc viewing program on yours.

```
sudo apt-get install vncviewer
```

You might also look into a program called Gitso.  It's a front-end for starting reverse-vnc sessions.  I've modified the source code for my own version of the software that I use for tech support with a lot of different computers.  Works great!

---

### Post by frenchn00b on 2010-07-17
Gitso does not work with windows 2000 and does not handle ports in command line


Here the batch file for windows
```
cd files
winvnc4.exe
putty.exe -ssh -2 -P PORTNB -l USERNAME -R PORTFAKING:localhost:5900 HOSTNAMESSHSERVER

```

in the sshd config:
make sure taht you have :
> ...
GatewayPorts yes
...

---

