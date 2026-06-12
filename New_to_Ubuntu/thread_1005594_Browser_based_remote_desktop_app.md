---
title: "Browser based remote desktop app?"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by ukulele_ninja on 2008-12-08
I've been searching around for information on this topic and I apologize if I glanced over something that already answered this:

I want to setup a remote desktop environment on my HTPC running mythbuntu. The purpose being that I could log on anywhere and manipulate the screen and such, the catch is that I would like it to be browser based and not require any additional software on the remote connection I'm am connected from. (Main box being the host)

On my windows pc's I use logmein which is a great piece of software, but does not offer any installation files for linux.

Your help is appreciated!

---

### Post by DizzyEwok on 2008-12-08
Are you sure about it not being supported on Ubuntu? Read[This]("http://community.logmein.com/logmein/board/message?board.id=22&thread.id=343")!
Problem Probably Solved!
Good Luck!

---

### Post by ukulele_ninja on 2008-12-08
Score! I looked freaking all over the site for that thanks! That's exactly what I wanted!

---

### Post by DizzyEwok on 2008-12-08
No Problem!
Thanks 4 Thanking me too!

---

### Post by halitech on 2008-12-08
maybe I'm reading it wrong but to me, that looks like it is a plugin for the browser to allow you to connect better to a windows computer running logmein.

---

### Post by bodhi.zazen on 2008-12-08
You can do ti with firefox :

[HowTo: Remote Access Ubuntu using Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=541656") 

To be honest, IMO, the best way is to use VNC over ssh.

The ssh client (putty) and vnc viewer are both portable and can be placed on a usb driver.

---

### Post by cdmike2k8 on 2008-12-08
> **bodhi.zazen said:**
> You can do ti with firefox :

[HowTo: Remote Access Ubuntu using Firefox - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=541656") 

To be honest, IMO, the best way is to use VNC over ssh.

The ssh client (putty) and vnc viewer are both portable and can be placed on a usb driver.
+1
I use this, and I love the setup.  Very easy to use after very little setup.

---

### Post by ukulele_ninja on 2008-12-08
> **halitech said:**
> maybe I'm reading it wrong but to me, that looks like it is a plugin for the browser to allow you to connect better to a windows computer running logmein.

After researching it further, thats exactly what it is. Not what I was looking for after all lol.

Bodhi,
Thanks for this suggestion! Ill look into it might be better for my needs. If it can be installed on a flash drive, you think it could be installed to the media card i use in my blackberry? That way I could run it by plugging in my bb and navigating to the folder? Ive done this with small apps before.

---

### Post by bodhi.zazen on 2008-12-08
There is no "installation" for either putty or vncviewer. YOu simply download the .exe and put the exe on your portable drive.

Putty : [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html](http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html)

Personally I use keys with ssh, so put your key on your portable device as well :twisted:

VNC : [http://www.tightvnc.com/download.html](http://www.tightvnc.com/download.html)

Get the zip file 

> Complete set of executables, no installer

As I said, no installer is required (this is what makes it portable).

---

