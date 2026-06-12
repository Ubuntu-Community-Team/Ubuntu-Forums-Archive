---
title: "Java Does Not Work"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by Tumpster on 2009-08-13
I've got a recently fresh install going (June) and have had no troubles using java up until about 2-3 weeks ago. Whenever I load up Facebook's picture uploader which runs on java it locks my firefox up and I have force quit to get out of it. What can I do to fix this? I've tried uninstalling and reloading and still encounter the same problems. Any help is appreciated!

---

### Post by RedSingularity on 2009-08-13
Java is installed with other pluggins.  These are usually hidden in your home/user/.mozilla folder.  If you delete this folder and uninstall firefox then it will be completely removed from the system.  From there you can reinstall firefox and java and try again.  

Beware:  Your favorites are also stored in the .mozilla folder.  Deleting that will delete your favorites.

---

### Post by Tumpster on 2009-08-14
> **Shadow121 said:**
> Java is installed with other pluggins.  These are usually hidden in your home/user/.mozilla folder.  If you delete this folder and uninstall firefox then it will be completely removed from the system.  From there you can reinstall firefox and java and try again.  

Beware:  Your favorites are also stored in the .mozilla folder.  Deleting that will delete your favorites.

Still same problem. ?

---

### Post by Cresho on 2009-08-14
use nautilus, go into your home directory by clicking on home and places.  select view and show hidden files.



make sure all firefoxes are closed.
look for .mozilla and rename it to .mozilla-backup and load firefox again.  look at facebook and see if you have a problem.  If you dont, then something in that directory is corrup.  so delete the new .mozilla directory created, restore the backup name to original, save your bookmarks and you can redoo process again to achieve your fresh firefox.

---

### Post by Katalog on 2009-08-14
Not to stray too far off topic, but there seems to be an unusual number of people having trouble with FF these days for some reason. And people have laughed at me for sticking with Epiphany all these years. Mwahahahahaha! :twisted: Been rock solid and never had nary a problem with it ever.

---

### Post by RedSingularity on 2009-08-14
Well i have found the new firefox is unstable (in my case) but the older 3.0 version is perfectly fine.

---

### Post by QIII on 2009-08-14
Could you post the results of 

```
java -version
```

It is possible that you are using OpenJDK, and an update is not behaving properly.

Some sites may be expecting Sun Java, which might cause problems.

---

### Post by Tumpster on 2009-08-16
> **QIII said:**
> Could you post the results of 

```
java -version
```

It is possible that you are using OpenJDK, and an update is not behaving properly.

Some sites may be expecting Sun Java, which might cause problems.

craig@craig-desktop:~$ java -version
java version "1.6.0_14"
Java(TM) SE Runtime Environment (build 1.6.0_14-b08)
Java HotSpot(TM) Server VM (build 14.0-b16, mixed mode)
craig@craig-desktop:~$

---

### Post by RedSingularity on 2009-08-16
In firefox go to Edit>Prefs>Content tab.  Make sure Java and Java Script are enabled.

---

### Post by Tumpster on 2009-08-16
> **Shadow121 said:**
> In firefox go to Edit>Prefs>Content tab.  Make sure Java and Java Script are enabled.

Both are checked.

---

