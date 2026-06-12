---
title: "[SOLVED] liblame0"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by adobrakic on 2008-12-14
I wanna install this, but:

```
ado@ado-desktop ~ $ sudo apt-get install liblame0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package liblame0 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  libmp3lame0
E: Package liblame0 has no installation candidate
ado@ado-desktop ~ $ 


```

wot?

---

### Post by Bachstelze on 2008-12-14
As the message says, liblame0 does not exist anymore and has been replaced by libmp3lame0.

```
sudo apt-get install libmp3lame0
```

---

### Post by taurus on 2008-12-14
Maybe you want the libmp3lame0.

```
sudo apt-get install libmp3lame0
```

---

### Post by adobrakic on 2008-12-14
I can't install [Avidemux](http://www.getdeb.net/release/2981) without the one I tried though. Is there another way?

---

### Post by mc4man on 2008-12-14
Avidemux is in the ubuntu repos
```

sudo apt-get install avidemux
```

---

### Post by adobrakic on 2008-12-14
For some reason i just make everything harder for myself.. :x

Thanks!

---

