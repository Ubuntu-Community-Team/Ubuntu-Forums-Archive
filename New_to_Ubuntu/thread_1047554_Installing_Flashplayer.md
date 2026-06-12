---
title: "Installing Flashplayer"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by MikeylovesJade on 2009-01-22
well i tried installing Dofus but it wants me to install flash player and it asked if i wanted to so i did but it said..


Error: Invalid SWF file name

in the terminal after installing it and retrying to run dofus, can anyone help me install this right? i use ubuntu 8.10

---

### Post by RomeReactor on 2009-01-22
Hi. Make sure you don't have Gnash installed:
```
sudo aptitude purge mozilla-plugin-gnash gnash gnash-common
```
and then install Flash (if it's not already installed):
```
sudo aptitude install flashplugin-nonfree
```

What is the entry for Flash listed by entering
```
about:plugins
```
in Firefox's address bar?

---

### Post by MikeylovesJade on 2009-01-22
did what u said (the commands) but i dont know wat u mean by whats it say in firefox sry im brand new to this, i just came from windows xp lol


edit:

application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes
application/futuresplash 	FutureSplash Player 	spl 	Yes

---

### Post by MikeylovesJade on 2009-01-22
still says invalid swf name though :/

---

### Post by RomeReactor on 2009-01-22
Are you able to view YouTube videos? we need to know if this issue is with Flash or if the problem is elsewhere.

---

### Post by MikeylovesJade on 2009-01-22
yeah im able to view youtube videos

sound is low on em but thats a different problem lol

---

### Post by XanTrax on 2009-01-22
What is dofus?

Is it this: [http://www.dofus.com/en?](http://www.dofus.com/en?)

Is it like some standalone flash program so you can play online?

---

### Post by philinux on 2009-01-22
[http://ubuntuforums.org/showthread.php?t=434657](http://ubuntuforums.org/showthread.php?t=434657)

See especially post #10 #14.

---

### Post by MikeylovesJade on 2009-01-22
yeah it is, but its in .bin


edit:

I know how to open dofus, friend told me n he told me how to do puzzle pirates but puzzle pirates works but runs in java, n he said to ask here about getting flash installed for dofus cause hes not familiar with it.

---

### Post by MikeylovesJade on 2009-01-22
Also i even tried opening a nes emulator, TuxNes and it wont, i gave the permissions it asked for n says it couldnt open that .bin file, is there something im doing wrong (with) the .bin files or?


edit: sry typo: (with), and also i'd like to thank you guys for helping a noobie like me lol. people on these forums already helped me get java properly installed n switched to my default.

---

### Post by RomeReactor on 2009-01-22
> **MikeylovesJade said:**
> Also i even tried opening a nes emulator, TuxNes and it wont, i gave the permissions it asked for n says it couldnt open that .bin file, is there something im doing wrong the .bin files or?

Try running the .BIN file from the terminal:
```
/path/to/file.bin
```
or change to the directory where the file is:
```
cd /path/to/file
```
and then run it:
```
./file.bin
```

There are NES emulators in the repositories; try **gfceu**.

---

### Post by MikeylovesJade on 2009-01-22
tryed that, just says its unable to open that .bin file

---

