---
title: "Tightvnc Gray Screen"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by azpac on 2009-08-10
I am using Ubuntu Server 9.04 on PC1 and Vista on PC2. I installed tightvnc on PC1 and start it by running vncserver. I installed tightvnc viewer on PC2. I can login to PC1 from PC2 but the screen is gray. I can not see the command prompt or do anything.

---

### Post by Threbus5 on 2009-08-11
Let me see if I understand.
You seemed to indicate that when you use tightVNC on the Vista machine you see a grey screen from the Ubuntu server.

When the Vista machine displays a grey screen does the Ubuntu server also show a grey screen?

If the Ubuntu server does not show a grey screen then check the video settings for the VNC connection - try setting them on the windows computer client and if that does not help adjust them on the server. They usually may be set for various amounts of color and/or dimensions.

Good luck.

---

### Post by azpac on 2009-08-11
[INDENT]*You seemed to indicate that when you use tightVNC on the Vista machine you see a grey screen from the Ubuntu server.*
[/INDENT]There may be a misunderstanding. I am trying to remote into the Ubuntu server from the Vista machine. I can successfully connect but my remote session is gray. 
 
[INDENT]*When the Vista machine displays a grey screen does the Ubuntu server also show a grey screen?*
[/INDENT]I'm not sure of this question but will try to answer. After I connect from the vista machine into the Ubuntu server, the remote session on the vista machine displays the gray screen. However, if I walk over to the local console of the Ubuntu server, the command line screen if fine.
 
[INDENT]*.....then check the video settings for the VNC connection - try setting them on the windows computer client and if that does not help adjust them on the server....*
[/INDENT]There are no video settings within the tightvnc viewer app on the vista machine. I have tried adjusting the video settings on the server. If I understand correct, this is done when starting the vncserver host mode at the Ubuntu server. ie <vncserver -geometry 800x600 –depth 24>

---

### Post by halitech on 2009-08-11
does the Ubuntu server have an X server installed?

---

### Post by ubu_can on 2009-08-11
I did have the same problem. I do not know whether my solution is the best possible, but it does work: 

1) run your vncserver as:
vncserver:1 (or some other number other than 0, which is the default)
(when you try to connet to that, you will have to specify that number in your vista program)

2) edit your .vnc/xstartup file:
   uncomment the line
unset SESSION_MANAGER

next write (if it is not there)
gnome-session &  (in my case I have the lighter 'icewm-session &')
the remaining should be the same...

good luck

---

### Post by azpac on 2009-08-11
[INDENT]*@halitech, does the Ubuntu server have an X server installed?*
[/INDENT]I do not have any X server/GUI installed. Is this required for vnc? I would prefer not if possible.
[INDENT]*@ubu_can, .......2) edit your .vnc/xstartup file:*.....
[/INDENT]I have tried modifying the /.vnc/xstartup but when I start vncserver, it does not seem to acknowledge anything in the xstartup file. Maybe this is because I don't have any gui installed?

---

### Post by halitech on 2009-08-11
> **azpac said:**
> [INDENT]*@halitech, does the Ubuntu server have an X server installed?*
[/INDENT]I do not have any X server/GUI installed. Is this required for vnc? I would prefer not if possible.
[INDENT]*@ubu_can, .......2) edit your .vnc/xstartup file:*.....
[/INDENT]I have tried modifying the /.vnc/xstartup but when I start vncserver, it does not seem to acknowledge anything in the xstartup file. Maybe this is because I don't have any gui installed?

if you are trying to use vnc then yes, it needs to have a screen to draw. if you want to use it with the cli, then use ssh to connect instead of vnc

---

### Post by ubu_can on 2009-08-11
As the previous post said, you should use ssh (or telnet) if you do not want X server. A good ssh client for XP is 'putty'. It should work under vista as well, but I have not tried it there.

---

### Post by azpac on 2009-08-14
The ssh/putty works great. Thanks for the help.

---

