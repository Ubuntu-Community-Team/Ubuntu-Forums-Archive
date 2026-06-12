---
title: "k9copy and 10.04 crashing"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by baddnady23 on 2010-06-04
Has anyone else been having issues with k9copy crashing on 10.04?  I can't get it to open a disc for the life of me now that I have upgraded...:confused:

---

### Post by sheridanm962 on 2010-06-04
> **baddnady23 said:**
> Has anyone else been having issues with k9copy crashing on 10.04?  I can't get it to open a disc for the life of me now that I have upgraded...:confused:

ubuntu 10.04 is pretty new and has few updates by any chance do you have/know your system specs so you can post it here?

```
system->administration->system monitor. 
then click system
```

then post it here ;) :popcorn::popcorn::popcorn::guitar:

---

### Post by baddnady23 on 2010-06-04
thanks for helping...  Very frustrating lol

---

### Post by lkraemer on 2010-06-04
Check this:
I had the same problem, trying to backup a dvd with css protection.
The solution was pretty simple:

Install libdvdread4:
sudo apt-get install libdvdread4

Install libdvdcss2:
sudo /usr/share/doc/libdvdread4/install-css.sh

lk

---

### Post by baddnady23 on 2010-06-04
> **lkraemer said:**
> Check this:
I had the same problem, trying to backup a dvd with css protection.
The solution was pretty simple:

Install libdvdread4:
sudo apt-get install libdvdread4

Install libdvdcss2:
sudo /usr/share/doc/libdvdread4/install-css.sh

lk


Seems like this did the trick... Thank you!

---

### Post by soluckytouselinux on 2010-07-21
hi everyone. this worked for me to fix k9copy. the second command sudo /usr/share/doc/libdvdread4/install-css.sh worked for me. thanx a billon!!!

---

