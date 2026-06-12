---
title: "Panel Trash Icon won't empty"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by l951b951 on 2009-08-24
The Trash icon on my panel won't empty, Right clicking and selecting empty does nothing.  When I open the trash, it doesn't show anything in there, even if I show hidden files.  

A restart didn't fix it.  Hovering over the icon itself says 3 items in Trash. 

What should my next step be?

---

### Post by SunnyRabbiera on 2009-08-24
I have seen glitches like this happen sometimes with the gnome trash applet.
Its nothing to worry about though

---

### Post by lkraemer on 2009-08-24
Open a Terminal
```

cd .local/share/Trash
ls -alt

```
There you will see two Folders/Subdirectories
files & info

change to those folders with
```

cd files

```
then use the rm command to delete the files.
You may have to use the sudo command with rm.
Same goes for info
```

cd ..
cd info

```
```

man rm

```

lkraemer

---

### Post by melinda on 2009-08-24
Mine did the same thing for a while and then it started working again, it's annoying though.

---

### Post by l951b951 on 2009-08-24
> **lkraemer said:**
> Open a Terminal
```

cd .local/share/Trash
ls -alt

```
There you will see two Folders/Subdirectories
files & info

change to those folders with
```

cd files

```
then use the rm command to delete the files.
You may have to use the sudo command with rm.
Same goes for info
```

cd ..
cd info

```
```

man rm

```

lkraemer

Both folders (files & info) are empty.  I used dir to look, and sudo dir to see if it was maybe a permission thing.  Still shows both as empty.

---

### Post by wojox on 2009-08-24
Try running:
```
gksudo nautilus '/root/.Trash/'
```

You may find some in there.

---

### Post by l951b951 on 2009-08-24
> **wojox said:**
> Try running:
```
gksudo nautilus '/root/.Trash/'
```

You may find some in there.

It had 1 file there, but deleting it didn't solve the problem.  However, I did notice in Nautilus the sidepane shows my trash file empty.  I closed my sudo nautilus and the terminal and opened nautilus up with my normal user access.  I created a junk file on my desktop and deleted it - the sidepane icon changed from empty to not empty.  I right clicked it and emptied it from there, changing the icon back to empty.  So i can confirm that apparently the issue is with the panel app not registering properly as stated here:

> **SunnyRabbiera said:**
> I have seen glitches like this happen sometimes with the gnome trash applet.
Its nothing to worry about though

---

### Post by credobyte on 2009-08-24
Last time I had this problem, reinstalling Nautilus fixed it :)

---

### Post by l951b951 on 2009-08-27
> **melinda said:**
> Mine did the same thing for a while and then it started working again, it's annoying though.

It's funny, it started behaving normally again this morning.  Apparently the solution is to quit messing with it, have a few Guinness beers, and go to sleep.  

Hope this solution helps others.

---

### Post by mapes12 on 2009-08-27
> **l951b951 said:**
> It's funny, it started behaving normally again this morning.  Apparently the solution is to quit messing with it, have a few Guinness beers, and go to sleep.  

Hope this solution helps others.+ 1 for the Guinness :)

---

### Post by credobyte on 2009-08-27
> **l951b951 said:**
> It's funny, it started behaving normally again this morning.  Apparently the solution is to quit messing with it, have a few Guinness beers, and go to sleep.  

Hope this solution helps others.

Solution = Guinness ? :lolflag:

---

