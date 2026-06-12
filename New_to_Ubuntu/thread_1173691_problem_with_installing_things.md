---
title: "problem with installing things"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by ccpallavi on 2009-05-30
"[COLOR=Red]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report[/COLOR]."

i get this error whenever i try installing things like those recommended by update manager and media plug-in....wat to do..
becoz of this problem...i'm not able to work with music player,movie player as it requires plug-in..
What to do???
Plz help....

---

### Post by -kg- on 2009-05-30
Open your terminal and run:

```
sudo dpkg --configure -a
```

It will ask you for your password, which you should provide.

That should fix the problem.

---

### Post by Sef on 2009-05-30
Applications > Accessories > Terminal

then copy and paste in this command:

```
sudo dpkg --configure -a
```

Next copy and paste in this command:

```
sudo apt-get update && sudo apt-get upgrade
```

That will update your computer.

---

