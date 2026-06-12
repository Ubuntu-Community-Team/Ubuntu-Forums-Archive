---
title: "permissions on partition"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by patman0623 on 2009-08-27
Due to legacy issues (I once had Windows installed), I have a 147 GB partition on my hard drive. I have not to date needed access to it... however, I do now. But I can't figure out how to grant myself permissions to access the drive on startup.

Help, I need to put my files on this disk!

---

### Post by pedro3005 on 2009-08-27
You could try 'gksu nautilus' and it will let you do whatever you want. For it to be mounted at startup, edit your fstab.

---

### Post by jrothwell97 on 2009-08-27
My advice would be to add it to /etc/fstab. Instructions can be found by running

```
man fstab
```

in the terminal.

---

