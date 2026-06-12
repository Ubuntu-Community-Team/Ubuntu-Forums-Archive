---
title: "Edit Application Install Directory"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by kogger on 2009-02-10
Applications are installed to /bin, right? Is there a way to edit where applications are installed?

---

### Post by yeats on 2009-02-10
Most applications end up in /usr/bin, actually.  /bin is more for system-level binaries.  That said, is there a particular reason you want them in a different directory?

---

### Post by kogger on 2009-02-11
I probably won't make any final changes, but I have a separate 150 GB partition on my hard drive that I would like to be able to install applications to if more space is needed.

---

### Post by yeats on 2009-02-11
Ah.  Are you short on space now?  One option would be to use the /opt directory (which is its intended purpose, as far as I understand things).  That's where I unpack source tarballs for programs and that's sometimes where the programs themselves live.

I understand your thinking here, but I wouldn't mess around with the default directories until you really know what you're doing.  You could also consider using gparted to adjust your existing partition sizes if you begin to feel cramped.

---

