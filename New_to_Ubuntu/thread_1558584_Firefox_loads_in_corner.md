---
title: "Firefox loads in corner"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by esvoytko on 2010-08-22
Rookie alert...

Every time I open Firefox, the browser window opens in the top-left corner of the desktop (I don't run Firefox maximized). I like to have it in the middle of the screen, but the application doesn't remember where it was the last time I used it - just opens in the top corner every time. A minor annoyance.

Here is the command from which I launch Firefox:

```
firefox %u
```My sub-question would be: what does the above syntax mean? If I had created that menu item from scratch, it would have looked something like usr/bin/firefox. What does %u mean?

Thanks,

Eric

---

### Post by jonnywombat on 2010-08-22
There is a list of the launcher codes [here]("https://help.ubuntu.com/7.04/user-guide/C/launchers.html")


hth

---

### Post by esvoytko on 2010-08-22
Those are helpful. But I am left with the problem of firefox loading in the corner. I want the application to remember the window size and location I last used when I open a new instance.

---

### Post by Elfy on 2010-08-23
Try using devilspie - I use it, but not the geometry function.

[https://help.ubuntu.com/community/Devilspie](https://help.ubuntu.com/community/Devilspie)
[http://live.gnome.org/DevilsPie](http://live.gnome.org/DevilsPie)
[http://live.gnome.org/DevilsPie#geometry](http://live.gnome.org/DevilsPie#geometry)

---

### Post by Elfy on 2010-08-23
To make it easy gdevilspie works well to set it up.

[http://code.google.com/p/gdevilspie/downloads/list](http://code.google.com/p/gdevilspie/downloads/list)

Extract and run gdevilspie from within the extracted folder.

I played with the geometry function - seems to work ok.

---

### Post by esvoytko on 2010-08-23
Thank you. That works, although seems like a bit of a work-around.

---

### Post by Elfy on 2010-08-23
possibly there are other ways to do it - I use devilspie to move apps to specific windows si already use it - the geometry thing I've never bothered with tbh

---

