---
title: "tuxpaint seg fault on 64bit lucid"
date: 2010-05-18
forum: New to Ubuntu
---

### Post by techno-mole on 2010-05-18
Hello.

Is anyone getting a seg fault with tuxpaint on 64bit lucid ? I can't really give any more info because running it in terminal just gives this - 
```
Segmentation fault
```

the configuration tool works fine though ?

any help would be appreciated, my kids love tuxpaint.

---

### Post by techno-mole on 2010-05-18
After some messing around I have found that the segfault only occurs when trying to set up configuration options.

Whether you use the tuxpaint-config tool or try the old way (by creating tuxpaintrc file) setting any options, screen size, save directory etc seems to result in a segfault, if you leave the configuration alone and let it run with the defaults it works.

I don't know why the configurations are causing the segfault though, unless tuxpaint wants access to things the system doesn't want it to access ?


I have been looking around and I haven't found anything that really relates to my issue.
I did discover that if I edit the default config file found in - /etc/tuxpaint/tuxpaint.conf I can then set the screensize,and other options and tuxpaint will work, although I still don't know why it won't using the configuration tool or by creating the tuxpaintrc file.
Maybe it's a permission thing ?

---

