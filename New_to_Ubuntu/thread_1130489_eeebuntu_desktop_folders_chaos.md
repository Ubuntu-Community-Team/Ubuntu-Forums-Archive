---
title: "eeebuntu desktop folders chaos"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by kamaboko on 2009-04-19
Hello,

I've got this thing set up pretty much how I want it except for a folder issue.  As you can see on the pic, whenever I make a folder in my home folder a copy is put on the desktop.  It's driving me mad.  I'm sure this must be a simple fix.  Why is this default for eeebuntu?  God!  So, how is this fixed?  

Thanks,
K

[IMG]http://i168.photobucket.com/albums/u166/marpibeach/Screenshot.png[/IMG]

---

### Post by _Purple_ on 2009-04-19
Open ~/.config/user-dirs.dirs and edit the line with "XDG_DESKTOP_DIR" so that it looks like ```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

---

### Post by kamaboko on 2009-04-19
Thanks. :D  That was the trick.

K

---

