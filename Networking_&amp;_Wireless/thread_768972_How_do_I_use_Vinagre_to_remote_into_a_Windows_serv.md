---
title: "How do I use Vinagre to remote into a Windows server?"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by ZeusABJ on 2008-04-26
I've been using Terminal Server Client to remote into the Windows machines on my network since the early days of Ubuntu, but since Vinagre was so hyped on the new feature list I thought I' d give it a go. I hate to say it but I can't for the life of me figure out how to use it. I can't seem to find any helpful HowTo's out there on this subject either. If you go to the Vinagre site you can see a screenshot of it being used to remote into a Windows computer:

[http://www.gnome.org/projects/vinagre/vinagre1g.png](http://www.gnome.org/projects/vinagre/vinagre1g.png)

I'd just like to know how this was accomplished. Anybody know?

---

### Post by Monicker on 2008-04-26
Appiclations -> Internet -> Remote Desktop Viewer


That is Vinagre.  It only works with vnc, and not terminal services, so the windows machine would have to be running some form of vnc server.

I tested it over a vpn connection to work and it worked great.  Just click on connect and enter the ip address of the machine to which you want to connect.

---

### Post by ZeusABJ on 2008-04-28
> **Monicker said:**
> Appiclations -> Internet -> Remote Desktop Viewer


That is Vinagre.  It only works with vnc, and not terminal services, so the windows machine would have to be running some form of vnc server.

I tested it over a vpn connection to work and it worked great.  Just click on connect and enter the ip address of the machine to which you want to connect.

AH! I did not realize that! D'Oh! Thanks for the clarification. Is VNC better than Terminal Services?

---

### Post by Monicker on 2008-04-28
> **ZeusABJ said:**
> AH! I did not realize that! D'Oh! Thanks for the clarification. Is VNC better than Terminal Services?


In my opinion, if you are connecting to a Windows machine, Terminal Services offers better video performance.  VNC seems to have a bit more lag in refreshing the screen.

---

### Post by ZeusABJ on 2008-04-30
Okay, thanks for all the help!

---

### Post by nhasian on 2008-05-04
I would like to use vnc to connect to Windows Vista from Vinagre in Ubuntu 8.04 Hardy Heron.  I read that Ultra VNC doesnt work with Vinagre, so what other VNC server for windows vista would you recommend?

> **Monicker said:**
> Appiclations -> Internet -> Remote Desktop Viewer


That is Vinagre.  It only works with vnc, and not terminal services, so the windows machine would have to be running some form of vnc server.

I tested it over a vpn connection to work and it worked great.  Just click on connect and enter the ip address of the machine to which you want to connect.

---

### Post by AnRkey on 2008-10-17
You cant use Vinagre for RDP yet.

To use RDP on ubuntu do this...

alt + f2
rdesktop -5 server-name-or-ip-here

the -5 will force protocol v5
and -4 will force protocol v4

I dont know about protocol v6 yet.

Later,

R

---

### Post by weirdorecords on 2008-12-06
I'm in this same situation & tried following this advice, but I just get a blinking cursor, and then after a few minutes an error that says 'connection timed out'. Any ideas what I've done wrong?

---

### Post by AnRkey on 2008-12-08
Try this, open up a console and type this in

sudo apt-get install tsclient

then go to Applications > Internet > Terminal Services Client

I use RDP 5 instead of 4. Copy and paste works fine and I get to stay where I belong, using Ubuntu instead of winblows. :guitar:

R

EDIT: removed mistake

---

