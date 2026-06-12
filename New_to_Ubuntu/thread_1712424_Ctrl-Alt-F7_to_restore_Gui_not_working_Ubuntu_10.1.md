---
title: "Ctrl-Alt-F7 to restore Gui not working Ubuntu 10.10"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by samcot on 2011-03-22
I'm brand new to Linux. Just installed Ubuntu 10.10 (multiboot with Windows 7). It boots up to the Gnome desktop just fine, and I can go to console mode just fine using Ctrl-Alt-F1, but I can't restore the GUI with Ctrl-Alt-F7, nor Alt-F7. It does nothing; the cursor just blinks. If I type "startx" I get:
 
Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock
and start again.
 
Please consult the The X.Org Foundation support
at [http://wiki.x.org](http://wiki.x.org)
for help.
 
ddxSigGiveUp: Closing log
 
However, if I type "sudo /etc/init.d/gdm restart" I *can* successfully restore my GUI session. I consider this to be a workaround solution, but is this as good as it gets? Is there a way I can get it to work using Ctrl-Alt-F7 or Alt-F7, or some other quick and easy method? 
 
Thanks!

---

### Post by nothingspecial on 2011-03-22
Try F8

---

### Post by samcot on 2011-03-22
Thanks for replying nothingspecial, but F8 doesn't work either. I'm trying to see if it might have something to do with the function keys themselves, and I'm following some leads.

---

### Post by JKyleOKC on 2011-03-22
And if F8 doesn't do it, try F6. I've had at least one box that for some reason didn't install the normal number of virtual TTYs (6), so using F7 wouldn't work on it...

---

### Post by samcot on 2011-03-22
I think I've solved it, almost by accident (I have a funny feeling that's the way some problems are solved in Linux). I was reading about some of the frustrations with the Microsoft Keyboard F-lock, and so I was trying to figure out how to toggle the F-lock off and on. Long story short, if I use the key combination Ctrl-Fn-Alt-F7, I can resume my Gnome GUI. It's funny, because when I'm in Gnome, I can get to the console using either Ctrl-Alt-F1 or Ctrl-Fn-Alt-F1, it doesn't seem to matter. But once I'm in console mode, I must use the Fn key to get the F-keys to work properly. The same goes if I want to add more terminals, e.g. "Ctrl-Fn-Alt-F2" to bring up TTY2. 
 
:D

---

### Post by samcot on 2011-03-22
Hello, Kyle, thank you for your response. I saw another thread that suggested F6 but that didn't work, either. I'm getting another funny feeling that there might be multiple solutions to the same problem, depending!

---

