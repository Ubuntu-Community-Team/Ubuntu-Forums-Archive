---
title: "Using the value returned by a command in a second (writing .sh file)"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by Jakey_TheSnake on 2010-12-17
So in short I'm writing a small script to back up my settings so I can restore them after a new install with a converse script. I'm now retrieving my background and saving it in my external HDD. 

Now ```
gconftool-2 --get /desktop/gnome/background/picture_filename
``` returns the exact filename and location of my background, I then need to copy it across to my HDD. So I need something like:

```
cp 'gconftool-2 --get /desktop/gnome/background/picture_filename' /media/WD1TB/Documents/Warez/New\ install/
```

where 'inverted commas' makes it execute that command before the cp.

---

### Post by TeoBigusGeekus on 2010-12-17
```
cp $(gconftool-2 --get /desktop/gnome/background/picture_filename) /media/WD1TB/Documents/Warez/New\ install/
```

---

### Post by Jakey_TheSnake on 2010-12-17
> **TeoBigusGeekus said:**
> ```
cp $(gconftool-2 --get /desktop/gnome/background/picture_filename) /media/WD1TB/Documents/Warez/New\ install/
```

I <3 you

---

### Post by TeoBigusGeekus on 2010-12-17
> **Jakey_TheSnake said:**
> I <3 you
Me too!!!:P
By the way: brilliant [book]("http://sourceforge.net/projects/linuxcommand/files/TLCL/09.12/TLCL-09.12.pdf/download") on linux command line.

---

