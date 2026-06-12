---
title: "Where is xorg.conf ?"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by const451 on 2010-05-20
I have just installed Ubuntu and I need to edit xorg.conf to fix the video. The file is supposed to be under /etc/X11 folder but the file in there called xorg.conf.failsafe. Is it correct one? if not, where is the correct one?

I have GNOME, if that matters.

Thank you.

---

### Post by Peter09 on 2010-05-20
Later version of Ubuntu do not use xorg.conf, although if you create one it will read it. 

What is the problem with your screen setup?

---

### Post by daimaru on 2010-05-20
there should also be a xorg.conf. the failsafe is just a backup. 
does the file contain anything if you open it from terminal using gedit?
```
gksu gedit /etc/X11/xorg.conf
```if there isn't one, that would be kind of weird. if you have an nvidia graphics card and nvidia restricted drivers installed you can generate one automatically by typing this in terminal.
```
sudo nvidia-xconfig
```you can then edit that file. which should be called xorg.conf
[COLOR=Red]EDIT[/COLOR]: did not know that 10.04 does not need xorg.conf file anymore, am still using one though for custom settings.

---

### Post by const451 on 2010-05-20
> **daimaru said:**
> there should also be a xorg.conf. the failsafe is just a backup. 
does the file contain anything if you open it from terminal using gedit?
```
gksu gedit /etc/X11/xorg.conf
```if there isn't one, that would be kind of weird. if you have an nvidia graphics card and nvidia restricted drivers installed you can generate one automatically by typing this in terminal.
```
sudo nvidia-xconfig
```you can then edit that file. which should be called xorg.conf
[COLOR=Red]EDIT[/COLOR]: did not know that 10.04 does not need xorg.conf file anymore, am still using one though for custom settings.

The first command open the empty editor. - I guess I'll just create an empty file.

The second command gave me "command not fount".

I'll create another thread about the problem I am having with video. 

Thank you.

---

