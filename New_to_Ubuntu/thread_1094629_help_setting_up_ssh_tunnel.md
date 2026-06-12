---
title: "help setting up ssh tunnel"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by medic8ted on 2009-03-12
I'm trying to use rsync between laptop and desktop, but rsync only allows port 22.  I use ssh on another port on the desktop, and I guess I need to set up a tunnel from port 22 on laptop to port 22001 on desktop, then the rsync command should just work, right?  Maybe even a script to run that will set up a tunnel then auto sync the 2 folders?

---

### Post by blueridgedog on 2009-03-12
From the man page, you can specify a different port for rsync over ssh with:

-e ’ssh -p 22001’

So, something like

```
rsync -av -e ’ssh -p 22001’ /foo/bar user@laptop:somedir/
```

Good luck.

---

### Post by medic8ted on 2009-03-12
found it, thanks

---

