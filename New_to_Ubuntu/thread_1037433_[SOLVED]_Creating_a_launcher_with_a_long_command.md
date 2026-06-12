---
title: "[SOLVED] Creating a launcher with a long command"
date: 2009-01-11
forum: New to Ubuntu
---

### Post by stussy on 2009-01-11
Hi guys,

I am playing some old games like doom and mario and was wondering if there is a way to create a launcher for Doom2.  I have to run this in the console to get it to start: ./chocolate-doom -iwad DOOM2.WAD

But if I type that in the command box of the launcher it doesn't react at all, any ideas?

---

### Post by Xiong Chiamiov on 2009-01-11
./ refers to the directory you're currently in, so you'll need to give the launcher the full path.  If you don't know what it is offhand, navigate to the directory where you normally launch the game, then type the command
```

pwd

```
In the launcher, put that directory before the filename.

---

### Post by mjheagle8 on 2009-01-11
use ```
pwd
``` to find the directory, then make your run application ```
path/to/directory/chocolate-doom -iwad DOOM2.WAD
```

---

### Post by stussy on 2009-01-11
I tried this but it doesn't work.  I put this in the command box of the launcher but nothing happens

```
sudo /home/stussy/chocolate-doom/chocolate-doom -iwad DOOM2.WAD
```

---

### Post by Joeb454 on 2009-01-11
try changing it to ```
gksudo /home/stussy/chocolate-doom/chocolate-doom -iwad DOOM2.WAD
```

---

### Post by stussy on 2009-01-11
never mind, stupid question, thanks guys!

---

