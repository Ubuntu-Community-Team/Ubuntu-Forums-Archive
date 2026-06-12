---
title: "Menu Bar Gone"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by nothilaryy on 2009-09-07
Ok this seems like it would be a really simple problem that I could fix in about 20 seconds in windows, but for some reason I can't figure it out in ubuntu. Currently I run Ubuntu netbook remix and a little bit ago the menu bar across the top stopped appearing. I must have turned something off without meaning to. It hasn't been a problem because I start off in the netbook version of the desktop so I can still access all my programs, but last time I accidentally turned it off while it was in the traditional desktop mode and now I can't figure out how to access anything but one file I saved on my desktop. 

Also, this may not have anything to do with it, whenever I opened firefox in the netbook remix it would resize really oddly and not take up the full screen and wouldn't allow itself to be minimized but the problem fixed itself by going into traditional desktop mode and then out and back into netbook mode.

Everything was working fine for awhile so it must have been something I accidentally changed and I have no idea what, or how to change it back, or how do anything at all. Help!

I run Ubuntu Netbook Remix on a HP Mini 110. Currently I'm typing this on a separate laptop. 

If there is anything else you need to know, just tell me and I'll try my best to figure it out.

---

### Post by NoaHall on 2009-09-07
Try using "gnome-panel" in a terminal

---

### Post by nothilaryy on 2009-09-07
I would if I had any clue how to get to the terminal without clicking on the icon somewhere. Is there some sort of keyboard shortcut? And once I'm there I just type in "gnome-panel"?

---

### Post by garyed on 2009-09-07
This might work.

alt-F2   then type in the command:  gnome-panel

---

### Post by nothilaryy on 2009-09-07
Alt-F2 didn't do anything.:(

---

### Post by arrange on 2009-09-07
Crtl+Alt+F1; login with your username and password, then type```
gnome-panel &
```Does it throw any errors? If not, try to come back by pressing Alt+F7.

---

### Post by astrakhan on 2009-09-07
try this. someone else had the same problem - post number six

---

### Post by astrakhan on 2009-09-07
[http://ubuntuforums.org/showthread.php?t=1201893](http://ubuntuforums.org/showthread.php?t=1201893)

---

### Post by nothilaryy on 2009-09-07
Thanks! It worked! I lost a couple settings, but whatever. I haven't had it too long.

---

### Post by coolglobal on 2009-09-10
the command gnome-panel brings up a butt ugly panel that looks more at home on windows 3.1. this is a bug, and an annoying one.

---

### Post by coolglobal on 2009-09-11
Paste this command in the terminal press enter, then restart, to fix the Ubuntu Netbook Remix Desktop Switcher bug.

gconftool-2 --set /desktop/gnome/session/required_components_list --type list --list-type=string ["windowmanager","panel"]

---

