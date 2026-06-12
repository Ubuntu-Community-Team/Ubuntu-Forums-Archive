---
title: "Need to move all files out of subfolders recursivley into a parent directory"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by dandescendant on 2011-02-22
Need to batch organise my film collection if possible, its a job that's been steadily increasing and as I'm about to migrate everything to a new machine now seems the time to do it.

What I need to do initially is move all files out of subdirectories into the parent directory i'm sure theirs an easy way to script this but my initial attempts and some time googling have come up empty, any ideas guys?

---

### Post by Vaphell on 2011-02-22
```
find . -mindepth 2 -type f -exec mv "{}" . \; 
```

---

### Post by jamesjwilsonsr on 2011-10-27
> **Vaphell said:**
> ```
find . -mindepth 2 -type f -exec mv "{}" . \; 
```
Bravo!  :popcorn:
It's always nice to do a search and find a thread ender first reply

---

