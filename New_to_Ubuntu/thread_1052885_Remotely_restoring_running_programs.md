---
title: "Remotely restoring running programs"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by TuxImpersonator on 2009-01-28
I run mathematica at work (Cent OS / KDE) and at home (Ubuntu) and sometimes I need to start a program running at work and later modify that program remotely from home.

I've had some success at doing this with screen and the mathematica terminal interface, but this requires a lot of work each run and not all mathematica commands are accessible for the terminal line.

My questions is this: is it possible to start a graphical interface of mathematica on my work pc, somehow background the whole program (such that the computation carries on), log-out, go home, ssh into my work pc and restore the graphical interface?

Sorry for the length of the questions but can anyone help?

---

### Post by Nepherte on 2009-01-28
You could tunnel the gui to your own screen. This can be done with the -X switch of ssh:
```
ssh -X username@host
```
This will give you a terminal as usual, but when you run a graphical application it will show up on your screen. For example:
```
xclock
```
A clock should now appear on your screen.

---

### Post by TuxImpersonator on 2009-01-28
Nepherte,

That's a good method but only works to make a new x and a new clock. I would like to be able to restore an all-ready running graphical process on a remote computer.

---

### Post by TuxImpersonator on 2009-02-05
To anyone reading this who's in the same situation we managed to get this working:

Prerequisites:
-On the computer to log into:
-- ssh server
-- [x11vnc]("http://www.karlrunge.com/x11vnc/") (a VNC server for real X displays)

-On the remote computer:
-- some sort of vnc viewer (ubuntu's remote desktop viewer does the trick)

Once these are installed follow [this guide]("http://www.linuxplanet.com/linuxplanet/tutorials/6155/2/"). But where it says "laptop> vncviewer localhost:0" instead load ubuntu's remote desktop viewer, choose "connect" and type "localhost:0". Hopefully this will work as well for you as it did for me.

---

