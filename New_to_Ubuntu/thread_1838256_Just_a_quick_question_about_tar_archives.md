---
title: "Just a quick question about tar archives"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by BK Baal on 2011-09-03
How many files can a tar archive handle?

For filesystems, i know that only a limited number of files can stay inside a single directory. What about tars?
For example, i have a tar archive with thousand of files (no folders), and sometimes i append newer files at the end of the archive. I can append how many files i want, or there's a limit to that?

---

### Post by Leshrac on 2011-09-03
I remember reading somewhere that in ancient times the tar format used to have a 8GB size limitation on individual files, however current versions of GNU Tar do not have this limitation.

As far as I know the tar format just concatenates files appending an individual header to each file, so there is no theoretical limit to how many files a tar file can contain.

You should however keep in mind that tar does not suport random access so accessing a single file in the middle of tarball with an arbitrarily large number of files could prove time consuming.

---

### Post by BK Baal on 2011-09-03
Yes, when i tried opening tar archives with a large amount of files various slowdowns occurred. However, i was using a GUI to view the archive, i rarely need to view (or extract) contents from the archive. I simply want a single file where i can put inside various files (by simply appending them without rewriting the archive every time).

Thanks for the reply. Also, i used 7zip back to WIndows XP for create the archive, there are no problems regarding compatibility, right?

---

### Post by Leshrac on 2011-09-03
There should not be, I think GNU tar is not entirely compatible with standard POSIX tar, but nowadays it looks like no one really cares about POSIX anymore ;)

---

### Post by BK Baal on 2011-09-03
Ok, thanks again for the answer!

---

