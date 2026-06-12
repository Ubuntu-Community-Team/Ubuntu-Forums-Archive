---
title: "Can't copy files to /etc/skel"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by fatality_uk on 2010-10-04
I am trying to copy files into /etc/skel in an OEM install but every time I try I get an error message "Operation not supported"

I am using gksudo nautilus so sure it's not a permissions issue.

Anyone have an idea how I might be able to do this?

---

### Post by da burger on 2010-10-04
Can you post the output when you try and do the copy from the command line? The command would be:
```
sudo cp /path/to/file /etc/skel
```

That will give us a better idea about what is failing. Also if it is a nautilus issue that will provide a workaround.
Angus

---

### Post by fatality_uk on 2010-10-04
Never mind! For some reason my USB drive wasn't mounting properly so failing to read.

---

