---
title: "Add/Remove Apps problem"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by pedro3005 on 2009-09-01
My Add/Remove apps suddenly stopped showing anything. Just says "There is no matching application available", even though "All Available apps" is selected. Any help? I tried reinstalling it, didn't fix. I tried "sudo apt-get update" and "sudo apt-get upgrade". I got a new unedited sources.list . Synaptic works perfect.
Thanks!

---

### Post by LowSky on 2009-09-01
open a terminal and type this or paste this command.
```
sudo apt-get install --reinstall app-install-data app-install-data-commercial
```

---

### Post by isparkes on 2009-09-01
Got anything in the "Search" box? (Top right hand corner). If you put the name of something in there that does not exist, you'll narrow the display down to nothing, and get that message...

---

### Post by pedro3005 on 2009-09-01
LowSky, thanks, did it! :D

---

### Post by Little Bit on 2009-09-01
I use Synaptic exclusively to add and remove software. I haven't even tried "Add and Remove." I really don't know why I never bothered, except that Synaptic so so easy I never needed anything "simpler" or different.

I'm glad you got it fixed, but in case anyone else has the same trouble, it's probably just as easy to use Synaptic instead as a work-around.

Amy

---

