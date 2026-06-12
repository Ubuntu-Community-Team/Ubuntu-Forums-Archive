---
title: "I lost my desktop wallpaper!"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by switch10 on 2009-06-08
My desktop wallpaper pops up for a second when I restart but then it turns brown (or whatever color I choose in preferences).  I have compiz-fusion installed.  I tried the killall nautilus command, someone fixed it that way, but it didn't work for me.  Any idea's?

Thanks

Dave

---

### Post by switch10 on 2009-06-08
The problem is not system wide because the other users have a desktop background.

---

### Post by switch10 on 2009-06-08
bump

anyone??

---

### Post by s.fox on 2009-06-08
Hi,

Have you tried Alt-F2 and then entering:
```
gconf-editor
```

Once it opens, navigate to desktop > gnome > background and make sure 'draw_background' is enabled.

-Ash R

---

### Post by reeseslover531 on 2009-06-08
Also have you tried re setting what your background is? Just go to the preferences and try setting it again.

---

### Post by HappyFeet on 2009-06-08
This will happen if the original pic is located on another partition or drive. Unless those partitions/drives automount, this will continue to happen. Put the pics you want as wallpapers in your home folder, and you will be good to go.

---

### Post by AutumnPhoenix on 2009-06-08
I don't know much but it could be a few things...

location...did the picture move?
size...did the size or format change?
actual pic...did it corrupt?
load...check which program that is running the background...some require you to load in the picture even if you can sample the pic.

---

### Post by switch10 on 2009-06-08
> **Ash R said:**
> Hi,

Have you tried Alt-F2 and then entering:
```
gconf-editor
```

Once it opens, navigate to desktop > gnome > background and make sure 'draw_background' is enabled.

-Ash R

Dude thank you so much for this.  I was in the process of moving my home folder to a different account.

Thanks again

Dave

---

### Post by smudge12b on 2009-06-24
While you're messing about with wallpapers I found some really nice ones here
 
[http://www.hongkiat.com/blog/60-most-execellent-ubuntu-wallpapers/](http://www.hongkiat.com/blog/60-most-execellent-ubuntu-wallpapers/)

---

