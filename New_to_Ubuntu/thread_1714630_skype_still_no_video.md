---
title: "skype still no video"
date: 2011-03-25
forum: New to Ubuntu
---

### Post by ernst.tamsen on 2011-03-25
Hi
I am trying to install skype. 
everything ok, but no video.
In this forum, I found the following: start skype from terminal using LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype.
This works!
Now how do I get the desktop icon to do the same? when I just put this magic line into the icon properties, the error message reads: Details: Kindprozess »LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so« konnte nicht ausgeführt werden (No such file or directory)
am I missing something or is it just not so simple?

tia
ernst

---

### Post by Perfect Storm on 2011-03-25
Try this instead:
```
sh -c "LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype"
```

---

### Post by ernst.tamsen on 2011-03-25
This works!
Thanks

---

