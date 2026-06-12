---
title: "Can't install ndiswrapper"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by Divad89 on 2007-04-10
I've downloaded the ndiswrapper, but when I want to install it, it comes out with errors, the first error is: loadndisdriver.c:15:20: error: stdlib.h: No such file or directory.

Before that I've unpacked the ndiswrapper, and runned "make distclean", "make" and "make install", do you know what I'm doing wrong?

Sincerely
David

---

### Post by spd106 on 2007-04-10
I suggest that you follow this wiki page [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

You may want to skip to step 11.

---

### Post by dbott67 on 2007-04-10
Did you install build-essential before trying to compile?
```
sudo apt-get install build-essential
```

If you did, what version of Ubuntu are you using?

-Dave

---

