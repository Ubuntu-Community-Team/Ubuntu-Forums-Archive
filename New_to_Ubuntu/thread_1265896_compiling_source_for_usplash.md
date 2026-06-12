---
title: "compiling source for usplash"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by shanep-server on 2009-09-14
I extracted all the files in the .tar.gz to a folder called usplash on my desktop. 

In the terminal I type

cd ~/Desktop/usplash/

once at the folder I type

make and I get the following

:`/Desktop/Splash$ make
make: Circular throbber_back.png > throbber_back.png.c
/bin/sh: pngtousplash: not found
Make: *** [throbber_back.png.c] Error 127
rm throbber_back.png.c

Not sure what that is but i don't think its compliling anything

---

### Post by relay_man on 2009-09-14
Look here:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Have patience, you will most likely get some errors and may have few dependencies to work out. 
Post back here when you run into a snag.

---

