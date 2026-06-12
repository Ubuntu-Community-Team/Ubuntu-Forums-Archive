---
title: "Remote access from Mac - tutorial?"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by shaggy_mutt on 2009-12-17
Hi there!

I have an Ubuntu 9.04 machine at work and want to access the desktop remotely from an OSX 10.5.8 Mac at home, so that I can use the work intranet.

I've looked in various places for some sort of tutorial for how to do this, but no dice so far. I get that I need to use VNC, but can someone offer tips on how to set up VNC so that it's reasonably secure? Thanks in advance!

---

### Post by eddietours on 2009-12-17
look into ssh

---

### Post by shaggy_mutt on 2009-12-17
I should clarify, I need to be able to use the web browser too. What I'm trying to do is to access an intranet at work through my Ubuntu machine (which is part of it), without having to actually drive in every time I want to use it.

SSH by itself doesn't do graphical things like browsers, right? What do I need to add to SSH for this?

---

### Post by issih on 2009-12-17
You want to set up an ssh tunnel and a vncserver.

In essence you use ssh to forward the port that the vncserver is listening on on your ubuntu machine onto a local port on your home machine (the mac).

You then point a vncviewer (I recommend jolly's fast vnc) on the mac to that port at localhost and voila you will have a connection, secured through ssh.

The exact nature of what is required will depend on the setup of your local network at work, in terms of what machines are externally visible to the internet.

---

