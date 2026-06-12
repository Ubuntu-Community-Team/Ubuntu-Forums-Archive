---
title: "Wine won't open &quot;Browse C:/ Drive&quot; option"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-04
Title says it all.

When I go to wine on the apps menu, and choose "Browse C:/ Drive", nothing happens?

How do I fix this?

---

### Post by skymera on 2009-03-04
Open up Wine config (winecfg) and set the C:\ manually.

See if that works

---

### Post by Gp. on 2009-03-04
Sorry, but how exactly do I do this? :S

---

### Post by skymera on 2009-03-04
Application > Wine > Settings (or similar)


or run winecfg from the terminal

---

### Post by Gp. on 2009-03-04
Oh no no,
I've got the wine configuration open, I just don't how to point wine to .wine as the C:/ drive...? It seems to be already set and I can't change the value.

---

### Post by skymera on 2009-03-04
I think the C:\ drive for wine is

/home/USER/.wine/drive_c/

Choose browse and have a look :)

---

### Post by Gp. on 2009-03-04
Yes, but it won't let me modify the C:/ path. :S

---

### Post by JPtux on 2009-03-04
Go to ~/.wine/drive_c/

---

### Post by Gp. on 2009-03-04
Thanks, that gets me there, but why doesn't it open this location from the wine menu?

---

### Post by JPtux on 2009-03-04
> **Gp. said:**
> Thanks, that gets me there, but why doesn't it open this location from the wine menu?

Sorry, I have no idea. I'm using KDE atm.

---

### Post by Gp. on 2009-03-04
:( Anyone?

---

### Post by Gp. on 2009-03-07
Tired reinstalling wine, that didn't fix it either.

---

### Post by Penguin-Guru on 2009-09-12
Same problem here but I can't open that location. I can CD into it but that's about it. I'm a newb to linux so I'm lost.

---

### Post by mc4man on 2009-09-12
This may or may not point to a possible solution.

Could you open a terminal and run this command and see what happens

```
xdg-open ~/.wine/drive_c
```

---

### Post by tudor117 on 2009-09-12
I had this issue too.
I don't recall how i fixed it...
But, since you are okay with reinstalling wine, just delete the .wine directory (will delete all wine programs and settings) but should work.

---

### Post by G-D on 2010-11-11
I found a forum that tells you how to fix it.  

[http://kubuntuforums.net/forums/index.php?topic=3114133.0](http://kubuntuforums.net/forums/index.php?topic=3114133.0)

1. Right click on the Applications tab in the KDE launcher

2. Browse to the "Browse C: drive" and go to the advanced tab

3. Change the work path to your user directory.

It should work.

---

### Post by dinesh301 on 2011-04-17
Run winecfg in terminal, it will create .wine folder for your use. Give me a hit someday [http://thesurmise.blogspot.com/2011/04/ubuntu-wine-c-drive-problem.html](http://thesurmise.blogspot.com/2011/04/ubuntu-wine-c-drive-problem.html)

---

