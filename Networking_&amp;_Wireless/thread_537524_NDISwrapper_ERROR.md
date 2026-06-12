---
title: "NDISwrapper ERROR"
date: 2007-08-29
forum: Networking &amp; Wireless
---

### Post by Dwiman89 on 2007-08-29
hey. Im trying to install ndiswrapper. When i type ''make'' in terminal. i get a whole bunch of errors. Ive installed it befor on another computer and didnt have this issue. unfortunatly i cant copy and paste what i got in terninal because ubuntu is on a differet hard drive inside my computer. why am i not able to compile proporly? please help. hambone

---

### Post by kevdog on 2007-08-29
You proabably did not install either the build-essential package or the linux header files.

Try typing this in the terminal:

If you already have an internet connection (ie a working wired ethernet connection),
please skip to step #4. Without any internet connection, please begin at step #1.

All commands typed at command prompt:

```

   1. After booting into Ubuntu, put the Ubuntu installation CD in drive and wait for it to "spin up"
   2. sudo apt-cdrom add
   3. sudo aptitude update
   4. sudo aptitude install build-essential linux-headers-`uname -r`
```

---

