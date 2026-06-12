---
title: "rights in ubuntu"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Drenriza on 2010-01-07
what does it mean when their stand
-rw-rw-r--?
and what does each
---------- mean?

thanks on advance:KS

---

### Post by Paqman on 2010-01-07
Every file has privileges set for three groups:

1) The user that owns the file
2) The group that owns the file
3) Others

Each or these can be give permission to read (r), write (w) or execute (x) the file.

So -rw-rw-r-- means:

Owner: read and write
Group: read and write
Others: read only.

---

### Post by audiomick on 2010-01-07
Hallo
Look at the man page for chmod
```
man chmod
```in a terminal
for more explanation.

If you still have questions, let us know;)

---

### Post by Drenriza on 2010-01-07
1) The user that owns the file
2) The group that owns the file
3) Others

but how meny --- is in user/group/others?

does group have --
user ----
and others ----? or how is it setup. If you know what i mean [-o<

because their is 10 -          but how are (-) devided

---

### Post by audiomick on 2010-01-07
10 positions
first position = data type e.g. d for directory, l for link, - for text file, I think x for executable file

position 2,3,4
rights for the owner r for read, w for write, x for execute

position 5,6,7
rights for the owners group

position 8,9,10
rights for others

---

### Post by Drenriza on 2010-01-07
Thanks :)

---

