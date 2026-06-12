---
title: "Exporting List of Items In Folders?"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by wpwend42 on 2011-06-28
I feel like I should know how to do this, but I don't...

How would I go about exporting a txt file of all the folders in my Music folder? I need to cross reference some music and with 100+gb of music, it would be annoying to do so via bouncing between folders.

---

### Post by mcduck on 2011-06-28
Just the folders, or their contents as well?

```
ls -R ~/Music* > ~/Desktop/music.txt
```

```
ls -Rd ~/Music* > ~/Desktop/music.txt
```

---

### Post by wpwend42 on 2011-06-30
I think just the folders will suffice. Thanks!

---

