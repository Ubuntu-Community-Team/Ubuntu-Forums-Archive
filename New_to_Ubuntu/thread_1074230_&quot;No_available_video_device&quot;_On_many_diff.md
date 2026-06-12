---
title: "&quot;No available video device&quot; On many different games"
date: 2009-02-19
forum: New to Ubuntu
---

### Post by beastrace91 on 2009-02-19
I am getting the following then I try to load several different games:

```
jeff@jeff-ubuntu:~$ supertux
Datadir: /usr/share/games/supertux
Warning: Unable to open the file "/home/jeff/.supertux/config" for read!!!

Warning: I could not set up audio for 44100 Hz 16-bit stereo.
The Simple DirectMedia error that occured was:
No available audio device


Error: I could not initialize video!
The Simple DirectMedia error that occured was:
No available video device
```

The messages before vary but the last one is always "No available video device" this is happening with several of the games I downloaded from the repositories :( Any ideas?

I have a NVidia 9500M GS and I am running the latest 180.27 drivers.

~Jeff

---

### Post by harithski on 2009-02-19
If you are running compiz/beryl, disable it before you start the game. Tell us if you have any luck.

---

### Post by beastrace91 on 2009-02-19
Nope. Just running what ever the default Ubuntu 8.10 window manager is.

~Jeff

---

### Post by gackt on 2009-02-20
maybe you want to googling about mesa and glx driver

---

### Post by beastrace91 on 2009-02-20
I'm currently using the latest NVidia driver...

~Jeff

---

