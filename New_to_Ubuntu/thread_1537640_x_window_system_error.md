---
title: "x window system error"
date: 2010-07-23
forum: New to Ubuntu
---

### Post by libihero on 2010-07-23
lately i've been getting a x window system error for different applications, and they either wont open or wont play (such as miro).  it says its a "bad match error"

---

### Post by mc4man on 2010-07-23
maybe try some of what's mentioned here and post 2 (try x11 video output

[http://ubuntuforums.org/showthread.php?p=9625311#post9625311](http://ubuntuforums.org/showthread.php?p=9625311#post9625311)

Otherwise post up what your video  adapter is ( and if restricted drivers are being used or even available.), possibly someone with similar hardware can help you
Info on video adapter 

```
sudo lshw -C display
```

---

### Post by 3rdalbum on 2010-07-24
Do   you   have   RGBA   (semitransparency)   enabled?   If   so,   then   you   will   need   to   add   the   program  ,such   as   Miro,   to   the   RGBA   blacklist.  This  depends   on   the method   you  used   to   enable   RGBA,   but   on   my  system   it's  in   the   '.profile'   file   in   my  home   directory,   right   at  the  bottom  of  the  file  in   the line  'allbut'.

---

### Post by libihero on 2010-07-24
i had enabled it before, but i thought i disabled it.  i don't see any "albut" in my ".profile" :(
i enabled it using gnome color chooser

---

### Post by libihero on 2010-07-25
bump

---

