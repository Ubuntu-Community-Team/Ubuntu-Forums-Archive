---
title: "XP/vnc server + Ubuntu/vnc viewer : maybe a simple thing?"
date: 2007-12-27
forum: Networking &amp; Wireless
---

### Post by Mr.Johnny on 2007-12-27
Hi... I've searched for similar threads but found no immediate solution... :(

The Ubuntu host sees the XP host, but when I try to connect to the vnc server in the XP machine, the viewer in ubuntu says it can't find the host...

What could it be?

thanks.

---

### Post by solar george on 2007-12-28
Is your XP firewalled?

---

### Post by Mr.Johnny on 2007-12-28
No, it's off... and I can access it running vnc viewer on a XP machine. :(

---

### Post by solar george on 2007-12-28
Which VNC server are you using?

---

### Post by Mr.Johnny on 2007-12-28
vnc-4_1_2-x86_linux.tar, dl from [www.realvnc.com](www.realvnc.com). :(

---

### Post by solar george on 2007-12-28
Is this the command you use on the linux host,

```
vncviewer *serverip*
```

---

### Post by Mr.Johnny on 2007-12-28
no, i simply type "vncviewer" and it crashes when I type the machine's name. Sorry for being such a noob, but how do I know the ip of the XP machine from ubuntu?

---

### Post by solar george on 2007-12-29
> no, i simply type "vncviewer" and it crashes when I type the machine's name. Sorry for being such a noob, but how do I know the ip of the XP machine from ubuntu?

The ubuntu machine won't know how to relate hostname and the ip number - use the windows networking information to find the ip of the windows machine and use this to connect.

---

