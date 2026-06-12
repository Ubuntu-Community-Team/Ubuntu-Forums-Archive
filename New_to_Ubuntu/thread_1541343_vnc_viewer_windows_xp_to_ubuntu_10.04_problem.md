---
title: "vnc viewer: windows xp to ubuntu 10.04 problem"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by rasengan08 on 2010-07-29
hi all, I installed ubuntu 10.04 32bit on my laptop last 2 days ago and I'm having problems regarding remotely configuring ubuntu through vnc viewer (windows xp 32bit on my desktop). My remote setup to ubuntu seems fine (because I can access it through xp's vnc) 
 
However, my problem is whenever i access ubuntu, I only get the FIRST screen or frame at my XP's vnc viewer but I can still remotely configure it (I mean if I look at my laptop, my mouse and keyboard responds to my actions but it doesn't show in vnc viewer, only the 1st screen!)
 
[COLOR=black]As for the vnc viewer, I used VNC Free Edition Viewer for Windows (installer and stand-alone) and TightVNC 2.0.2[/COLOR]
 
Thanks and please help me, a completely newbie ubuntu user :(

---

### Post by rasengan08 on 2010-07-29
I thinks this is a possible FIX which i dug while reading the forums:
 
 
From the VNCclients document, troubleshooting section:
*If you connect to a VNC server, can see the initial desktop, can see the mouse moving around, but the rest of the screen doesn't update, then you probably need to disable desktop effects on the shared desktop. A [known bug]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/353126") means that desktop effects are currently incompatible with most VNC servers*
 
 
..solved it, i had my effects turned on and vnc worked by turning them off

---

