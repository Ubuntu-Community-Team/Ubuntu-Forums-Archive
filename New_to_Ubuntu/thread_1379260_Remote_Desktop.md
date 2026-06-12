---
title: "Remote Desktop"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by Malice007 on 2010-01-12
I know Ubuntu comes with Remote desktop and from what I read it is only good for LOCAL connections. I need someone that will allow me to control a Ubuntu machine from across town the world etc...Is there such a program? If so can someone point me in the right direction? 

I switched many of my family members over to Ubuntu and it is getting old running back and forth to there homes doing things for them.. :)

---

### Post by doas777 on 2010-01-12
I recommend freexn: [https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

you will have to do a little router configuration to make it work, and I suggest using a differant port than the standard 22.

---

### Post by aeiah on 2010-01-12
if you only need a command prompt, then ssh is the way to go. if you need a gui try a VNC program. specifically one that will tunnel through ssh for you to make it more secure.

freenx sounds like it could be quite good though, but ive never used it.

---

### Post by doas777 on 2010-01-12
> **aeiah said:**
> if you only need a command prompt, then ssh is the way to go. if you need a gui try a VNC program. specifically one that will tunnel through ssh for you to make it more secure.

freenx sounds like it could be quite good though, but ive never used it.

ssh is defn the best bet for CLI. VNC however is not safe to expose to the internet, wether it is ubuntu's vino (remote desktop) implementation, or another, unless the traffic is tunnelled over ssh. 

freenx is ssh based so the connection is secure, and it has basically the same benifets as vnc, except that you cannot share a session (eg: have 2 users moving the mouse on the same screen at the same time.)

---

