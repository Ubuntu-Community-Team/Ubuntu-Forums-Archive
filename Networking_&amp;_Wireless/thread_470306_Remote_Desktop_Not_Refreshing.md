---
title: "Remote Desktop Not Refreshing?"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by patchmonkey on 2007-06-10
I've been able to connect using VNC Viewer (on notebook running Vista) to my other notebook running Ubuntu (great for controlling the media player on that machine without moving from the couch).

However, although I can connect - the desktop never refreshes. I can control the system, and I can see that what I'm doing on the local (running VNC Viewer on Vista) is occurring on the remote (Ubuntu) machine, the screen never refreshes on the local.

Any ideas on how to make this work? I want to set up my old desktop as a better media/file server, but I can't if I can't actually get this to work properly. 

Thanks!

---

### Post by Ek0nomik on 2007-06-11
Well if you want to transfer files to it, I would suggest SSH.  It's encrypted transfer which makes it more secure.  You can also run software from your Ubuntu box on your Windows box by having an X emulator.  (For an example, let's imagine on your Ubuntu box you open a program like Deluge, or Amarok, or Totem, and it opens on your computer.  With an X Emulator + SSH you could have that program actually open on your Windows machine and be able to use it.)

However, if you can't accept this solution, then I would look into using a different method of VNC.  The built in VNC software in the box of Ubuntu is pretty bad.  (It's called Vino).

This may work better for you:

_**HOWTO: Install x11vnc to access your main desktop (display :0)**_
[LIST=1]
[*]Install x11vnc and vnc-common:[INDENT]```
sudo apt-get install x11vnc vnc-common
```[/INDENT]
[*]Create a VNC password.  The first password prompt is asking you for your user password, the second and third are to enter a new VNC-only password:[INDENT]```
sudo /usr/bin/vncpasswd /etc/vnc.passwd
```[/INDENT]
[*]Edit gdm setting:[INDENT]```
sudo gedit /etc/X11/gdm/gdm.conf
```Find the line like this:```
#KillInitClients=true
```and replace it with this:```
KillInitClients=false
```[/INDENT]
[*]Add to gdm startup script:[INDENT]```
sudo gedit /etc/X11/gdm/Init/Default
```Add this line just above the PATH line:```
/usr/bin/x11vnc -rfbauth /etc/vnc.passwd -noxdamage -forever -bg -o /var/log/x11vnc.log -rfbport 5900
```[/INDENT]
[*]Restart gdm, OR just restart your computer is probably the best bet.[INDENT]```
sudo /etc/init.d/gdm restart
```[/INDENT]
[/LIST]

(Credit to user *jnorth* for writing the tutorial)

Then, a program like UltraVNC for Windows to control your Ubuntu box would work perfectly.

---

### Post by patchmonkey on 2007-06-11
**Ek0nomik** - I'm gonna give that a shot. I don't need the ability to run files on the local (Windows) machine, as the notebook running ubuntu is actually running as a file/print server at the moment, and I can get what I need via SMB. I think the second method may work best for me.

---

### Post by krunge on 2007-06-11
If you are going to use x11vnc, be sure to use the ```
-noxdamage
``` option that   ek0nomik points out. I believe it is the workaround to your screen refreshing problem:

[http://www.karlrunge.com/x11vnc/#faq-beryl]("http://www.karlrunge.com/x11vnc/#faq-beryl")

---

### Post by bsaik on 2007-06-18
I was having trouble getting vino to work. I'd connect using tightVNC from my XP machine and I'd get the remote window with a "please wait - drawing initial desktop message" but then nothing would happen.

I followed the directions above to switch x11vnc and all works great. Just hoping to help out a few other folks who may have seen the problem I was having.

Thanks!!

---

### Post by finite9 on 2007-06-26
i have the same refresh problem with Xvnc, whish is part of the vnc4server package in the repository.  I cannot see a -noxdamage option anywhere in the man pages, or any other setting that seems relevant apart from -deferUpdate 0 which did not work.

Is this problem common to all linux VNC servers?  I tried realvnc viewer on vista and get the same problem there.

---

### Post by Mark England on 2007-07-17
Thank you Ek0nomik,

I had the problem described using Ubuntu - Feisty Fawn and your suggestion worked a treat :)

---

### Post by jebblue on 2007-12-25
Thanks much, awesome tip on the -noxdamage!

---

