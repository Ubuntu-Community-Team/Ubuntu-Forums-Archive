---
title: "TIGHTVNC - I'm lost!"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by adamjkok on 2010-07-13
I just downloaded TIGHTVNCSERVER. I'm completely lost. What do I do?

---

### Post by bodhi.zazen on 2010-07-14
First of all, learn how to secure VNC. nc servers are the most common cracks on these forums.

Either tunnl VNC over SSH or use Freenx

Next see any of the on line tutorials :

[http://www.davelachapelle.ca/guides/ubuntu-tightvnc-server/](http://www.davelachapelle.ca/guides/ubuntu-tightvnc-server/)

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

[https://help.ubuntu.com/community/VNC/Servers](https://help.ubuntu.com/community/VNC/Servers)

Again you are "OK" on a LAN, but otherwise learn how to ssh. You can forward X applications over ssh

[http://martybugs.net/smoothwall/puttyvnc.cgi](http://martybugs.net/smoothwall/puttyvnc.cgi)

ssh -X

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

Other then that you will need to ask a more specific question or tell us where you got stuck.

What did yo download ? Why did you not install a VNC server from the repositories ? Why not use the default VNC server, Vino ?

---

### Post by Jakiejake on 2010-07-14
> **adamjkok said:**
> I just downloaded TIGHTVNCSERVER. I'm completely lost. What do I do?

Why Didn't you just use the default one that comes with Ubuntu!

---

### Post by techunit on 2010-07-14
using the built in VNC client in Ubuntu is both easy and efficient here is a video that shows you how to use it. [http://ubuntuvideotutorials.wordpress.com/2010/06/22/using-vnc-with-ubuntu/](http://ubuntuvideotutorials.wordpress.com/2010/06/22/using-vnc-with-ubuntu/)

---

### Post by YesWeCan on 2010-07-14
> **adamjkok said:**
> I just downloaded TIGHTVNCSERVER. I'm completely lost. What do I do?
I use tightvncserver. It's a piece of cake.
On the server terminal type 'vncserver'
It will ask for a password the first time so give it one. This is the password you need to supply when connecting. Use something different from your other ubuntu passwords.
Then it will tell you the desktop number it has allocated. The first time you run it it will be 1. The port it uses will be 590X where X is the desktop number (with tightvncserver you can have multiple desktops at the same time).
Then on the client use a vnc viewer application to connect. I use vinagre. Give the viewer the IP address of the server and the port number of the desktop and then the password.
That's it.
Note that you need to be logged in to the server for vnc to work properly, either at the server itself or remotely logged in.
To stop a desktop being exported, on the server type 'vncserver -kill :X' where X is the desktop number.

The previous comments about security are very important. Don't do this over the public internet without using an encrypted tunnel or a hacker could, in theory, use a vnc viewer to hack into your server.

---

### Post by adamjkok on 2010-07-15
Everybody seems to want to know why I didn't want to use VINO. There's one simple reason: I don't want to see what's on the physical display, I want to start a session that can only be seen on the remote display. In other words, I need to "create a screen." On the local display, the login screen would still be shown.

---

### Post by bodhi.zazen on 2010-07-15
> **adamjkok said:**
> Everybody seems to want to know why I didn't want to use VINO. There's one simple reason: I don't want to see what's on the physical display, I want to start a session that can only be seen on the remote display. In other words, I need to "create a screen." On the local display, the login screen would still be shown.

That is a perfect reason not to use vino =)

---

