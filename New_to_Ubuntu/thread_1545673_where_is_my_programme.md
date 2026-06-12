---
title: "where is my programme?"
date: 2010-08-04
forum: New to Ubuntu
---

### Post by woodseaves on 2010-08-04
I have installed a programme using Wine. Everything appeared to go well with the install but where is my programme? and how do I get it to run?

regards

---

### Post by todak on 2010-08-04
Try looking under *Applications> Wine> Programs*. It should be listed there.

---

### Post by mapes12 on 2010-08-04
[http://ubuntuforums.org/showthread.php?t=885111](http://ubuntuforums.org/showthread.php?t=885111)

---

### Post by ytsurk on 2010-08-04
or try

> apt-cache policy wine

or

> whereis wine

in terminal to see the location

you can add it later to the panel if desired,
if not already there .. ;)

---

### Post by woodseaves on 2010-08-04
> **todak said:**
> Try looking under *Applications> Wine> Programs*. It should be listed there.
That is the most obvious place and is where I looked first. Not there

Wine  is not the problem, the problem is finding the programmes that I have downloaded that open in wine.

---

### Post by aeiah on 2010-08-04
wine creates a mock C: drive structure.. i think it's in ~/.wine/drive_C/

so your applications will be in there. see if you can simply launch them with ```

wine ~/.wine/drive_c/path/to/program.exe
```

if so, you can then create a menu entry with that command, since it seems one wasn't created for you.

---

### Post by mkvnmtr on 2010-08-04
In your home if you enable see hidden files you will find .wine. Then c drive and then program files. You can open the choosen program by right clicking on it and choosing to open with wine.

---

