---
title: "My desktop is gone!"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by GHFury on 2009-02-02
I was following this sound guide:[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
And then when I rebooted my computer (I was following the guide), first the ubuntu logo and the loading bar showed up. Then when it had loaded, I got to some like terminal. First it asked me got my username and password, then it was excactly like terminal. How do I fix this without reinstalling ubuntu?

---

### Post by lykwydchykyn on 2009-02-02
First try this:  log in as yourself, then type "startx".  Probably that will fail, but you will get some error output.  Output lines beginning with "EE" are errors, post them here and we can diagnose what went wrong.

---

### Post by GHFury on 2009-02-02
YES! I typed in "startx", and it worked! But why is it like this? Why isnt it like it was before?

---

### Post by perlluver on 2009-02-02
> **GHFury said:**
> YES! I typed in "startx", and it worked! But why is it like this? Why isnt it like it was before?

Did you follow the part where it said to type ```
sudo apt-get install gdm ubuntu-desktop
```  It said Gnome users have reported that those files have been deleted.

---

### Post by GHFury on 2009-02-07
Yes! Thanks a lot! It's back to narmal. I guess I missed out on that part. :D

---

