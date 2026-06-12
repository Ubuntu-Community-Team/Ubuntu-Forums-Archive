---
title: "Kill desktop icons"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by dwavidbwyant on 2009-02-23
Im using ubuntu 8.10 and I want to break the paradigm that we have to use a desktop to store files. I have conky installed and i configured it so it was transparent to the desktop and was above the icons. 

I want to know the safest way to loose my desktop icons without deleting them, just keeping them from being visible on the main desktop.

---

### Post by agim on 2009-02-23
I am not sure how to do that. I am just curious as to why you would like completely transparent desktop icons. Or am I misunderstanding you? If that is the case I'm sure I or someone else could help you with it.

desktop icons and functionality on gnome and kde are kept in .desktop files, are you trying to save the .desktop file but not see an icon?

---

### Post by jerrrys on 2009-02-23
maybe or maybe not

[http://ubuntuforums.org/showthread.php?t=1057259](http://ubuntuforums.org/showthread.php?t=1057259)

---

### Post by mr.p on 2009-02-23
Start gconf-editor and go to /apps/nautilus/desktop

Untick those options you don't want (volumes_visible is probably the only one on).

[http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

---

### Post by protodog on 2009-02-23
or...you could also use a tiling Window Manager like [ion3]("http://www.modeemi.fi/~tuomov/ion/"). No "desktop" at all :)

---

### Post by dwavidbwyant on 2009-02-24
alright thanks a lot.

---

