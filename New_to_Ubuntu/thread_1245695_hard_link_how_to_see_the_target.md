---
title: "hard link: how to see the target?"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by minsf on 2009-08-20
how do i see the target of a hard link?

more details:
i have two files: file.txt and link.txt
the latter is a hard link to the former, created by "ln file.txt link.txt".
if i did not know that, is there a way to see that file.txt is linked to link.txt? (as "ls -l" does for symbolic links)

i know that "ls -i" shows that they have the same inodes, but if i have many files in the same directory, it's hard to see which ones have the same inodes. i could probably write a script that takes the inodes from "ls -i" and find which files share inodes, but there must be a simpler way...

---

### Post by minsf on 2009-08-21
did some more research on the find manpage and found this:
```
find / -samefile file.txt
```

---

