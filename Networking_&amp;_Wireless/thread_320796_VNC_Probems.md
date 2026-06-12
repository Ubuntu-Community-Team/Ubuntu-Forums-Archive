---
title: "VNC Probems"
date: 2006-12-17
forum: Networking &amp; Wireless
---

### Post by 13291 on 2006-12-17
I hope this is in the right section.

I am trying to set up my computer so that I can vnc to it from a slower computer and have them run two different desktops. So far, I have been able to get my current desktop to show on the slower computer, but when I try to get a separate desktop, all I get is a terminal window. I tried this guide [http://ubuntuforums.org/printthread.php?t=42941](http://ubuntuforums.org/printthread.php?t=42941) but I am getting the following error. Can anyone help me with setting my computer so that I can log in remotely?

Error:
****@****-Laptop:~$ vncviewer localhost:1
VNC viewer version 3.3.7 - built Jul 4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
ReadFromRFBServer: rdr::SystemException: read: Connection reset by peer (104)

---

### Post by 13291 on 2006-12-18
Bump

---

### Post by benfindlay on 2006-12-20
thats the exact same problem I've been having. I've just upgraded to 6.10 from 6.06 and set up my vnc exactly the same way, but no joy!

Any help would be much appreciated!

---

### Post by 13291 on 2006-12-21
Just a question.  Did you upgrade to 6.10, or reinstall?  I reinstalled, but am wondering if I would have the problem if I simply upgraded (I was afraid to simply upgrade with all of the issues that people had had).

---

### Post by mayhemt on 2006-12-21
Why not use nxclient & nxserver to use 2 desktops?

---

### Post by 13291 on 2006-12-21
I did something when trying to install FreeNX a while ago.  I tried aptitude remove, but that didn't get rid of all the settings, and now it doesn't work.  I think the problem may be in something SSH related, but removing that didn't get rid of all my problems either.  If you could tell me how to get rid of all of the settings and reinstall FreeNX, that would basically fix all my problems.

---

### Post by 13291 on 2006-12-22
OK, here is a half solution to the problem.  I prefer to have my remote session be XFCE, so you may need to change this to get it to work yourself.  When you get to the open terminal, simply run xfdesktop|xfce4-Panel.  You need to keep the terminal window open (you can minimize it), but it appears to load up xfce.  If you want the xfce window manager, this is what I did (on kubuntu) kwin-replace, then press Control + C.  You now have no window manager open.  You can then type xfwm4|xfdesktop|xfce4-panel.  If anyone knows of a better solution, I would like to know.

---

### Post by benfindlay on 2006-12-22
Decided to sack it, and downgrade back to Dapper. My attempts through Edgy were done on a fresh install using the alternate iso, as installing via the normal cd and via update manager both gave me problems. ](*,) 

Am I correct in my understanding that Edgy is still rather unstable in places? Seeing as Dapper is the Long Term Support version, I think that I will stick with it for now! To quote that well known phrase "If it aint broke, don't fix it!"

Anyways, cheers for the advice guys, and cheers for the XFCE solution 13291!

---

### Post by 13291 on 2006-12-22
I am thinking about doing the same thing, but I am not sure that I need the ability badly enough to re-download the iso.  And I really wouldn't call it a solution.  Certain programs will not start, and you have at least one terminal window at the bottom of your screen that will not close.  For some reason, I can just not get Ubuntu to work with everything at the same time.  Now I have a choice, local beryl, or the ability to log in remotely?  Right now beryl is winning 8) .

---

### Post by 13291 on 2006-12-23
OK, here is a full solution.  If you are logging in from a linux computer, just login via XDMCP and search an available computer.  If you need to login from a Windows computer then download the free xserver for windows from here: [http://sourceforge.net/projects/xming](http://sourceforge.net/projects/xming) .  If you then select Fullscreen, and login via XDMCP, then search for a login, at first you will get an X session with nothing, but after about 15 seconds, you will get your login screen.  At this point, you have a fully usable (and almost lag free if it is on a LAN) linux session on your Windows computer!  And if you decied to go fullscreen, you may not even know that you are using Windows.  While this is more difficult to set up, it appears to be faster then VNC, and better quality (though I would still prefer NX).

---

