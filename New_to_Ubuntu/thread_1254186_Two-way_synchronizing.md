---
title: "Two-way synchronizing"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by paal on 2009-08-31
I have a few folders in two locations which I'm trying to keep synchronized. One is local and one is accessed via ssh. I edit, create and delete files from both locations. I've tried to do this using rsync like this:
```
rsync -vruz /location1 /location2
rsync -vruz /location2 /location1
```
It works fine unless I create or delete files. Then it gets confused and tries to create deleted files etc. I suppose I can't do what I want with rsync as I would need some kind of database that keeps record of my files. Could somebody suggest a way I can do this? I'd prefer to have a command line tool so I can make it a cron job.

---

### Post by mapes12 on 2009-08-31
Others have suggested Unison but I couldn't get along with it myself but it sounds what you're looking for.

---

### Post by Mlok on 2009-08-31
I'm a beginner with rsync, but I wonder if you are aware of the --delete option which lets you decide how rsync should manage deletions.

---

