---
title: "HFS+J USB drive showing read only"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by tenmilez on 2011-01-04
Pretty simple, when I make my USB hard drive on my mac (Mac OS Extended (Journaled) under mac, abbreviated HFS+J) and then plug it into my ubuntu machine it will auto mount, but I can't write to it and in the terminal it gives me

touch something
touch: cannot touch `something': Read-only file system


sudo touch something
touch: cannot touch `something': Read-only file system

And if I:

/media$ ls -l
drwxrwxr-x  1          99          99    9 2011-01-03 23:14 Untitled

I also tried to chmod a+x to no success. 

Has anyone had any luck getting these file systems to work?

---

### Post by tenmilez on 2011-01-04
So, partial stupid, incredibly dumb mistake on my part. 

When dealing with permissions, w is write and x is execute...

But also I had to disable journaling to get ubuntu to be happy.

---

