---
title: "vnc through ssh over internet"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by terry f on 2008-04-26
Hi,

I have been trying to vnc through ssh over the internet.  I am able to ssh into my computer from the internet but when I try to start vncviewer I get "Error: Can't open display".

Can any one help?

---

### Post by Monicker on 2008-04-26
Are you doing the ssh forwarding from the command line?  Have you verified you have connectivity to the vnc port on the remote side?

I use port forwarding to tunnel web traffic through a proxy on my home machine, using the following syntax:

```
ssh -C -L 8080:localhost:3128 username@hostname
```

For vnc it would be

```
ssh -C -L 5900:localhost:5900 username@hostname
```

The first port after -L can be whatever you choose as long as the last port corresponds with the service listening on the remote side.

---

### Post by terry f on 2008-04-26
yes I am doing trying to do the ssh forwarding from the command line.  I have not verified you have connectivity to the vnc port on the remote side; how would I do that.  I tried your second piece of code, but I still cant get it to work.

---

### Post by Monicker on 2008-04-26
You can get a normal shell session on the remote machine?  If so, run "netstat -anltp|grep LISTEN", and see if there is a process listening on the vnc port (default is 5900 for first display). Or run "ps aux|grep vnc", to see if vnc even shows up in the process list on the remote side.

---

### Post by terry f on 2008-04-26
I ran netstat -anltp|grep LISTEN and got this:

tcp        0      0 0.0.0.0:5901            0.0.0.0:*               LISTEN      22196/Xtightvnc 
tcp        0      0 0.0.0.0:6001            0.0.0.0:*               LISTEN      22196/Xtightvnc 
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5583/cupsd      
tcp6       0      0 :::2500                 :::*                    LISTEN      20856/inetutils-ine
tcp6       0      0 :::5900                 :::*                    LISTEN      6619/vino-server
tcp6       0      0 :::110                  :::*                    LISTEN      20856/inetutils-ine
tcp6       0      0 :::22                   :::*                    LISTEN      22926/sshd 


I ran ps aux|grep vnc and got:
user    22196  0.0  0.6  19648  6564 ?        S    01:11   0:06 Xtightvnc :1 -desktop X -auth /home/user/.Xauthority -geometry 1024x768 -depth 24 -rfbwait 120000 -rfbauth /home/user/.vnc/passwd -rfbport 5901 -fp /usr/share/X11/fonts/misc,/usr/share/X11/fonts/cyrillic,/usr/share/X11/fonts/100dpi/:unscaled,/usr/share/X11/fonts/75dpi/:unscaled,/usr/share/X11/fonts/Type1,/usr/share/X11/fonts/CID,/usr/share/X11/fonts/100dpi,/usr/share/X11/fonts/75dpi,/usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID -co /etc/X11/rgb
user    28217  0.0  0.0   5164   856 pts/1    S+   14:17   0:00 grep vnc

---

### Post by Monicker on 2008-04-26
You have both vino-server and tightvnc running.  They basically do the same thing.  Tightvnc is listening on ports 5901 and 6000.

I don't know if the 2 apps will interfere with each.  I have never run them together, but you really only need one or the other.

---

### Post by terry f on 2008-04-26
well here is what I have been typing into the terminal.


ssh -C -L 5900:localhost:5900 user@ipAddress

vncviewer
Error: Can't open display:

---

### Post by Monicker on 2008-04-26
Try this instead:

```
ssh -C -L 5901:localhost:5901 user@ipAddress
```


and then do:

```
vncviewer localhost:1
```

---

### Post by terry f on 2008-04-26
is localhost suppose to be the computer name or the ip address of the computer.

---

### Post by Monicker on 2008-04-26
> **terry f said:**
> is localhost suppose to be the computer name or the ip address of the computer.


localhost is supposed to be localhost.  The remote server is going to intepret localhost from its perspective, and since it is running vnc server, it knows to direct the connection to itself (localhost).

---

### Post by terry f on 2008-04-26
same result as before; still cant get it to work.

---

### Post by Monicker on 2008-04-26
> **terry f said:**
> same result as before; still cant get it to work.

Clean up all those instances of vino and tightvnc.  It works perfectly fine for me.


You can also try Method 2 at this site:

[https://help.ubuntu.com/community/VNC]("https://help.ubuntu.com/community/VNC")


I've never done it that way myself.

---

### Post by terry f on 2008-04-26
how would I clean up?

---

