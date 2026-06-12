---
title: "[SOLVED] copy .vob files"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by expatCM on 2008-12-24
I have just borrowed some DVD movies from a friend.  I would like to copy them to my hard drive.  I have found that all files will copy with the exception of any .vob files, the error message I get is that this is an i/o error.

I do not understand why ….  the discs appear to be fine otherwise.....  all other files will copy over...  

I am using nautilus but the same thing happens with gnome-commander.  I can browse the content of the media.

The only difference I can see from other DVDs is that these are ntsc whereas all the others are pal but I am not sure whether or not this is significant ….   Any ideas?

---

### Post by nhasian on 2008-12-24
use dvdrip

```
sudo apt-get install dvdrip
```

---

### Post by hyper_ch on 2008-12-24
or k9copy

---

### Post by binbash on 2008-12-24
or wine + dvdshrink

---

### Post by expatCM on 2008-12-24
Thanks for responding ....  I will explore the two programs ....

---

### Post by Nepherte on 2008-12-24
This command will also do exactly what you want:
```
mplayer -v dvd://1 -dumpstream -dumpfile titlename.vob
```

You will need to install mplayer if you haven't done it yet. The stream number may vary (i.e. dvd://2 or dvd://3, just check it with a movie player).

---

