---
title: "trying to run vbox guest additions in 11.04"
date: 2011-08-12
forum: New to Ubuntu
---

### Post by pcrussell50 on 2011-08-12
running xubuntu 11.04 in virtualbox, hosted by osx.  when i select, "install guest additions", it merely mounts a virtual cd in the guest os, (11.04).  when i open it and browse to the executable file, (on the virtual cd), and click on it, it says i need to run it in terminal.  however, when i open terminal i can only seem to get as far as the /media directory.  i can't get into the directory of the virtual cd, so i can run the executable that _should_ or might install guest additions.

-peter

---

### Post by melrokz on 2011-08-12
You may need to use the Terminal for this. Make the file executable by changing its permissions and run it:
```

sudo chmod 755 filename
./filename

```

P.S. I'm not great in Linux, but this should work... :)

---

### Post by haqking on 2011-08-13
> **melrokz said:**
> You may need to use the Terminal for this. Make the file executable by changing its permissions and run it:
```

sudo chmod 755 filename
./filename

```P.S. I'm not great in Linux, but this should work... :)

NO...LOL

The additions usually places a icon on the desktop or where ever it is.

Change to that directory using tab completion is easiest

cd Desktop (remember to capitalise) if it is not Desktop then whereever it is.

The run :

./VBox......... again use tab completion for whatever your need.

see here:

[http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/](http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/)

---

