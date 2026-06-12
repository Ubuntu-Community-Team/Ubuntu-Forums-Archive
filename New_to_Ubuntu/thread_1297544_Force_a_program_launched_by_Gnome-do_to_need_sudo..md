---
title: "Force a program launched by Gnome-do to need sudo."
date: 2009-10-21
forum: New to Ubuntu
---

### Post by Remagen on 2009-10-21
So, I'm writing an application w/ pcap.

This requires my application to have root privileges in order to read from the wire.  I'm writing this in code blocks, I tried setting it so that only root could run codeblocks permission wise in /usr/bin (the idea was that I'd be prompted to elevate permissions)

Then I added gksudo to the Applications menu option for codeblocks, and that works, but only if I launch using the mouse.  

But I use gnome do, and I like gnome-do, so where do I edit gnome-do so that codeblocks will require root privileges?

---

### Post by pgar23 on 2009-10-21
Maybe try sudo su instead of gksudo. Just might work, but idunno.

---

### Post by 3rdalbum on 2009-10-21
Usually what you should do is have a little conditional in the program that tests what user is running it; the "whoami" shell command works for this. If the answer is not "root", then run the following shell command  and exit:

```
gksudo /usr/bin/myapp
```

This will relaunch your program immediately with a gksudo prompt so it will run as root.

---

