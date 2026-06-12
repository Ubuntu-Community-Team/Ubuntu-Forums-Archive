---
title: "Help! Lost folder"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by furoido on 2009-08-02
Just lost a folder on my desktop...one minute it was there, the next minute it vanished!
Have checked my waste bin and used 'search', but no luck...can anyone give me any suggestions of how else to look for it?!

---

### Post by credobyte on 2009-08-02
```
find / -name "folder_name"

```

---

### Post by mgranet on 2009-08-02
Make sure it's not hidden. Any file or folder with a . in front of it is hidden.

Example: .textfile

Not really familiar with Nautilus, but there should be an option in one of the menus to show hidden files. If not, from a terminal: ```
ls -a
``` will show you all contents, hidden or not, of a directory.

---

### Post by egalvan on 2009-08-03
One more trick to finding "lost" desk-top files is to use Nautilus...

Places -> Desktop

will open a Nautilus window where you can browse all files.

For instance, no 'back-up' type files shows on my desk,
but they show up on the Nautilus view.

And at times, files I've just added will not show on the desktop
(downloaded or moved/copied), but will show in Nautilus.

---

### Post by furoido on 2009-08-04
How do I run nautilus?? just installed it, but if i click 'places' followed by 'desktop', all i get is the desktop-file browser, which only shows what I can see anyway on my desktop...

---

