---
title: "rsync without replacing identical files?"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by fraser_m on 2009-01-25
I want to sync all my music from one directory (~/Music) to another (/media/NO\ LABEL) with rsync, without replacing the files that are identical. Is there any way to do this with a single command? I've tried
```
rsync -r ~/Music /media/NO\ LABEL
```
but everything gets copied.

Any ideas?

---

### Post by emarkd on 2009-01-25
try the -a switch.  this uses rsync in archive mode and should do what you want.  you can add the -v switch if you want verbose output to see what it's doing.

---

