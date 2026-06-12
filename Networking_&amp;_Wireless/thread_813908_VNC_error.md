---
title: "VNC error"
date: 2008-05-31
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2008-05-31
I am getting the following error when using the vncserver:```
Warning: linux-1501:1 is not taken because of /tmp/.X11-unix/X1
Remove this file if there is no X server linux-1501:1
A VNC server is already running as :1

```

This is odd as this is the first time I tried using it. Any ideas on what to do?

---

### Post by lsutiger on 2008-05-31
OK I am having hell with this.

I am connected to my computer at home from my office via SSH.
I killed the instance of vncserver running on the computer at home.
I started the vncserver on the computer at home. I changed the password via vncpasswd. 
When I run vncviewer, it asks for the password then gives my permission denied.
Did I do something in the wrong order?
Why would it reject the password I just created?

---

### Post by lsutiger on 2008-05-31
OK here's what I got:```
brian@brian-linux:~$ vncviewer -via complexity@antec.homelinux.net linux-1501:1

VNC Viewer Free Edition 4.1.1 for X - built Apr 16 2008 13:02:40
Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
complexity@antec.homelinux.net's password: 

Sat May 31 09:57:19 2008
 CConn:       connected to host localhost port 5599
channel 3: open failed: connect failed: Connection refused
 main:        End of stream

```
I have the port 5900 on my router forwarded to my computer at home. My username on my computer at home is complexity. The domain name that is forwarded to my router is antec.homelinux.net. the name of the computer is linux-1501. vncserver is running on :1 on the computer at home.

So am I doing everything correctly? And what is with that port 5599 in the response from vncviewer?

---

### Post by lsutiger on 2008-05-31
Ok got that fixed. Killed the vncviewer on 1 and setup on two.```
vncviewer -via complexity@antec.homelinux.net linux-1501:1


```
Now I am trying to set it up to where I can see the full screen. Only a part of it is showing. When I press F8 and choose full screen, I get full screen, but just part of the desktop shows. Right click on the desktop does nothing.

Thanx in advance for any response!

---

### Post by lsutiger on 2008-06-01
??

---

### Post by lsutiger on 2008-06-03
Now I am trying to set it up to where I can see the full screen. Only a part of it is showing. When I press F8 and choose full screen, I get full screen, but just part of the desktop shows. Right click on the desktop does nothing.

UPDATE: I set the geometry to the desktop size (1280X800) and now I get nothing but a grey screen.

Can anybody help me with this?

---

