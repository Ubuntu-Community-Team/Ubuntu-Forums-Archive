---
title: "skype webcam"
date: 2011-07-01
forum: New to Ubuntu
---

### Post by helphelp on 2011-07-01
Hi,
I have to open a  file and copy and paste this command 
(LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype )
into terminal  every time i want web cam to work in skype.
I don't leave my computer on all day so it's a bit of a pain.
Is there a way i can get skype to work with webcam  by just clicking on the launcher ?
THank you

---

### Post by androssofer on 2011-07-01
quick fix wud b to make a desktop shortcut. then select its properties.. and paste in 

```
 && LD_PRELOAD =/ usr/ lib/libv 4l/
v4l1 compat.so skype
``` after the launch command. thts a cheap fix tho..

---

### Post by helphelp on 2011-07-02
Thanks for that.

---

### Post by crispy_420 on 2011-07-02
Wouldn't another option be to have it run auto at startup?

---

### Post by abybaddi on 2011-07-02
> **helphelp said:**
> Thanks for that.

If you've got your solution then click on thread tools and mark this thread as solved so that other users may come to know that.

---

### Post by helphelp on 2011-07-02
works now.
I found instruction to go to system>preferences>main menus: applications>skype>properties and changed the command there to
     Code:
     bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype' 
loads now with video

---

