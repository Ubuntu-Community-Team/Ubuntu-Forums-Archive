---
title: "Is there a way to install a Logitech camera using skype?"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by TAspr on 2011-02-28
Is there a way to do this?

---

### Post by metalf8801 on 2011-02-28
You need to give more information before anyone can help. First what model of camera do you have and what have you tried to do so far?

---

### Post by ajgreeny on 2011-02-28
More info please.  I have a logitech camera working with no problem in 10.04 with skype and all other apps that can use it.  It is a very simple webcam with no mic, version C120.

It is possible that you may need to preload the video software with a script to start skype, and it will depend on your version of ubuntu what that script contains.  A previous one I needed when I was using my digital camera as webcam was
```
#!/bin/bash
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype
```so it could be worth a try.  If you have a 64 bit system this may need an edit to point to the correct .so file, so have a search for that first.

---

### Post by seawolf167 on 2011-03-01
I've got a Logitech Pro 9000, and it has had no problems. Didn't have to deal with drivers or anything, everything worked right out of the box. Skype & cheese haven't had any problems.

---

