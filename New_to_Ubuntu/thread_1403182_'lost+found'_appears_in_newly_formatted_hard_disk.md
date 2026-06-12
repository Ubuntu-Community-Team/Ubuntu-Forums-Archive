---
title: "'lost+found' appears in newly formatted hard disk"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by SteelCore on 2010-02-09
I had an extra hard disk installed on my system. I used gparted to format it to ext4. I then accessed it via the Places menu but when opened, for the first time, I found a 'lost+found' directory inside (with an X emblem on the top). I'm positive no one put it there. Is this normal?

---

### Post by unmole on 2010-02-09
It's normal. Don't worry about it.

---

### Post by warfacegod on 2010-02-09
Perfectly normal. If you don't want it there hit Alt+F2 and type gksudo nautilus. Hit Enter. Use the file browser to navigate to it and delete it.

---

### Post by celthunder on 2010-02-09
It's for when it emergency shutdowns and recovers random bits of data I believe (that's what ends up in mine anyway)

---

### Post by Satoru-san on 2010-02-10
> **celthunder said:**
> It's for when it emergency shutdowns and recovers random bits of data I believe (that's what ends up in mine anyway)
Yes, when your computer crashes it moves the files that it could recover to it.

> Each        partition has its own lost+found directory. If you find files in there,        try to move them back to their original location. If you find something        like a broken symbolic link to 'file', you have to reinstall the file/s        from the corresponding RPM, since your file system got damaged so badly        that the files were mutilated beyond recognition.

source: [http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html](http://tldp.org/LDP/Linux-Filesystem-Hierarchy/html/lostfound.html)

---

### Post by SteelCore on 2010-02-10
If it's used for recovery then I guess I'll leave it and ignore it :)
Thanks for the replies.

---

