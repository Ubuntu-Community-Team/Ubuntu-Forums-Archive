---
title: "[SOLVED] VNC - Hardy to Mythbunutu 7.10 not working"
date: 2008-07-12
forum: Networking &amp; Wireless
---

### Post by gamerteck on 2008-07-12
I can't seem to remote from my Hardy to Gutsy(Mythbuntu) box. I can through XP/Vista.

I VNC to screen :2 through an SSH tunnel. SSH works fine.

The only thing I can see in my iplogs on my Mythbuntu box is:
> Sat Jul 12 22:24:30 2008; TCP; eth1; 40 bytes; from 172.168.25.5:12243 to 172.168.25.130:46922 (source MAC addr <deleted MAC for post>); Connection reset; 1 packets, 40 bytes, avg flow rate 0.00 kbits/s; opposite direction 1 packets, 60 bytes; avg flow rate 0.00 kbits/s


Even if I try to connect just using vncviewer without a tunnel it doesn't work.

Help!

---

### Post by superprash2003 on 2008-07-12
firstly ensure both are able to ping each other.. then in your hardy pc in the terminal type vncviewer x.x.x.x:0 where x.x.x.x is the ip of the gutsy machine

---

### Post by gamerteck on 2008-07-12
Here is the message I get when I run vncviewer from the terminal.

> vncviewer: ConnectToTcpAddr: connect: Connection refused
Unable to connect to VNC server


My laptop is a dual boot. In XP I can VNC to myt Mythbox without any problem, but when I boot into Hardy I can't.
I can also SSH to my Mythbox from Hardy.

---

### Post by superprash2003 on 2008-07-13
are you running firestarter or anything similar which maybe be blocking!!

---

### Post by gamerteck on 2008-07-13
I'm running IPTABLES.

On the same machine but with using XP, i can connect just fine. For some reason I can't connect when using hardy.

ON Hardy I have disabled UFW.

---

### Post by gamerteck on 2008-07-14
I can use the Remote Desktop Viewer to connect but I still cannot use VNC. 
bot VNC on client and server are the same.

---

### Post by gamerteck on 2008-07-18
I figured it out. It was a syntax error.

**_[SIZE="4"]In 7.10[/SIZE]_**, I could use the command below to create an SSH tunnel and then VNC through it:
> ssh -L 5900:27.28.29.30:5900 ubs@27.28.29.30
AS well as when utilizing the vncviewer command I would do:
> vncviewer localhost:5900


**_[SIZE="4"]In 8.04[/SIZE]_**, I now have to use:
> ssh -L 5900:localhost:5900 ubs@27.28.29.30
And the vncviewer command as:
> vncviewer localhost::5900

Thanks self!

---

