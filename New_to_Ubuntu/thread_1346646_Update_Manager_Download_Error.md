---
title: "Update Manager Download Error"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by nefarmboy on 2009-12-05
I get this error when trying to run updates from the Update Manager:

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

Is the problem on my end or Ubuntu's?

---

### Post by LuisGMarine on 2009-12-05
Hello,

That message is usually displayed when you have two or more applications trying to access synaptics, your package manager.

Close every window you have open, and try running the update manager again.  This includes any terminals.  If the problem still persists come back here and let me know and we'll take it from there.

---

### Post by Soul-Sing on 2009-12-05
```
sudo rm /var/cache/apt/archives/lock
```

```
sudo apt-get update
```
-------------------------------------

or: ```
sudo killall dpkg
``` 
or another packagemanager proces...(-apt?)

---

### Post by nefarmboy on 2009-12-05
It's working fine now.  Thanks for the insight.

---

### Post by LuisGMarine on 2009-12-06
can you please mark this thread as solved then?  Thanks! :popcorn:

---

