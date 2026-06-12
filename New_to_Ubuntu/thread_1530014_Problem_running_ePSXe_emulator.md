---
title: "Problem running ePSXe emulator"
date: 2010-07-13
forum: New to Ubuntu
---

### Post by camn on 2010-07-13
Whenever I try to run ePSXe it gives me an error saying > cam@cam-laptop:~/ePSXe$ ./epsxe
./epsxe: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory What do I do? I really wanna play Legend of Dragoon >_<

---

### Post by Dr_Willis on 2010-07-13
I cant find that lib in the package manager or anywhere else. 

I would guess that the epsxe binaries you have are compiled with the older libraries. You need to find  a newer version thats compiled with whats included in the ubuntu you are using.  That program is apparently VERY old. 

Check out newer versions of the program at

[http://www.playdeb.net/updates/ubuntu/10.04/](http://www.playdeb.net/updates/ubuntu/10.04/)

use any unofficial repositories with caution.

---

