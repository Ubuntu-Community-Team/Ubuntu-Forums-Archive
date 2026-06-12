---
title: "Problems compiling Crawl by Stone Soup 0.6"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by Ozymandias_117 on 2010-05-22
Hi, I'm trying to compile the Tiled version of Dungeon Crawl by Stone Soup version 0.6 (Found here: [http://crawl.develz.org/wordpress/]("http://crawl.develz.org/wordpress/")) It acts like it's going to work, then at the end it says ```
    LINK crawl
/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make: *** [crawl] Error 1
```

Does anyone know what this means and how I can fix it?

---

### Post by Ozymandias_117 on 2010-05-23
bmp

---

### Post by Ozymandias_117 on 2010-05-23
Fixed by using 
```
cd /usr/lib
sudo mv libGL.so libGL.so.bak
sudo ln -s libGL.so.1.2 libGL.so
```

Thanks to the idea from [http://ubuntuforums.org/showthread.php?t=409438]("http://ubuntuforums.org/showthread.php?t=409438")


Edit: Apparently, the original libGL.so was a sym link to /usr/lib/mesa/libGL.so which was a sym link to /usr/lib/mesa/libGL.so.1 but there WASN'T a file there named libGL.so.1 so, that was probably why I was having difficulties.

---

