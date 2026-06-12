---
title: "Google earth crashing."
date: 2009-10-09
forum: New to Ubuntu
---

### Post by fixerman on 2009-10-09
Having successfully installed Google Earth it seemed to work for a while but now crashes most times it run it. Any help appreciated!

---

### Post by DougieFresh4U on 2009-10-09
Have you tried running it from terminal and see what errors it gives?
Terminal>googleearth

---

### Post by nickpaton on 2009-10-09
Could it be anything to do with NASA 'crashing' into the moon today?!!

Sorry but I wish I could suggest a proper solution

---

### Post by x C0MMAND0 x on 2009-10-09
I would uninstall and reinstall it.  

```
Sudo apt-get purge googleearth
```

Then do the following.

1. Go to [http://dl.google.com/earth/client/current/GoogleEarthLinux.bin](http://dl.google.com/earth/client/current/GoogleEarthLinux.bin) to download the newest version.

2. Open terminal

3. Go to directory where file is located
```
cd /path/to/.binfile
```

4. Make file executable
```
chmod +x GoogleEarthLinux.bin
```

5. Execute program
```
 ./GoogleEarthLinux.bin
```

That will prompt the install.  Then, it tells you how to run it.  It double listed Google Earth for me in Applications > Internet, but you can remove that from System > Administration > Main Menu > Internet

---

### Post by fixerman on 2009-10-09
> **DougieFresh4U said:**
> Have you tried running it from terminal and see what errors it gives?
Terminal>googleearth

I tried that but it crashed straight away.

---

### Post by DougieFresh4U on 2009-10-09
> **fixerman said:**
> I tried that but it crashed straight away.

Any info from terminal?

---

### Post by fixerman on 2009-10-09
> **DougieFresh4U said:**
> Any info from terminal?

Like I said...it crashed straight away when I ran it from terminal before I could read the result.

---

