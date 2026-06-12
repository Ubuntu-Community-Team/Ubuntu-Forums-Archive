---
title: "How to change start-up tone ?"
date: 2010-01-23
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-01-23
How to change start-up tone ?
thanks for the assistance

---

### Post by JiuJitsu500 on 2010-01-23
The music that plays at login?

Find a sound bite you like, convert it to .ogg (I use Audacity), name it "desktop-login.ogg"

Press Alt+F2 at your desktop to open Run and type "gksu-nautilus" and type your password. Open File System > Usr > Share > Sounds... (if there are more options it's in the Ubuntu folder, then stereo) and rename "desktop-login" to something unrelated to preserve it (i.e. desktop-login55.ogg, etc)... then drag and drop your file here.

If you have to be root to do this because it brings you into a root shell, open a terminal and type "sudo passwd" to set your root password first :) I don't know if you HAVE to be root to do this, but I always am when fiddling around here.

---

