---
title: "Skype cam won't work"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by anotherdummhead on 2011-03-04
I've got this problem, my webcam isn't working with skype. I'm using Canyon CN-WCAM23, really old webcam, but the thing is i can't get it to work. Skype as far as i can see recognized her but it won't turn on in call.

---

### Post by anotherdummhead on 2011-03-04
Found it, thread solved :)

Run this in terminal :

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype

---

### Post by lpt2007 on 2011-03-23
> **anotherdummhead said:**
> Found it, thread solved :)

Run this in terminal :

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype


I tried this but my canyon cn-wcam23 still not working!!!

any ideas? I am using xubuntu

thx

---

### Post by Dutch70 on 2011-03-23
> **lpt2007 said:**
> I tried this but my canyon cn-wcam23 still not working!!!

any ideas? I am using xubuntu

thx

If you want to get help, you need to start your own thread. This one is marked as solved, very few people will look at it.

Also, you may want to read this first.
[[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=1422475[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1422475")

---

