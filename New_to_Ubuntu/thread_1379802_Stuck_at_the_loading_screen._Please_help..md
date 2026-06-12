---
title: "Stuck at the loading screen. Please help."
date: 2010-01-12
forum: New to Ubuntu
---

### Post by MarkSkywalker on 2010-01-12
First time poster here. With a problem already, haha.

I was messing around in the CCSM settings and I pressed something to the extent of "Reflective Windows" if I'm remembering correctly. Everything froze up and nothing would move for about ten minutes so I forced the computer to restart and now, whenever I log in, I see the Ubuntu loading screen, hear the starting theme, and it just sits there, not doing a thing.

Can anyone please help? I'm pretty confused and frustrated.

Thanks in advance.

---

### Post by Gone fishing on 2010-01-13
OK I think this will work

Reboot - do not log in but Alt F1 this will take you to a terminal log in to the terminal then```
 rm -r /home/yourusername/.compiz.
``` Then reboot ```
sudo reboot
``` and all should be fine

---

### Post by MarkSkywalker on 2010-01-13
I'm afraid I might not completely understand. I went to the log-in screen and pressed Alt+F1 and nothing happened, but maybe you meant something else by it? Was I supposed to press it somewhere else?

---

### Post by rossmoore on 2010-01-13
Try crtl+alt+F1 instead of alt+F1

---

### Post by MarkSkywalker on 2010-01-13
That did help quite a bit. I got to the terminal log-in. However, when i typed in what i needed to, it said it could not remove "home/myusername/.compiz."  because there was "no such file or directory".

---

### Post by Gone fishing on 2010-01-13
Sorry about that Control Alt F1 :oops:

However,  ```
home/myusername/.compiz.
```needs to be ```
/home/myusername/.compiz 
```

sorry the extra dot is my fault again :oops:

I was rushing to work when I typed this morning

---

