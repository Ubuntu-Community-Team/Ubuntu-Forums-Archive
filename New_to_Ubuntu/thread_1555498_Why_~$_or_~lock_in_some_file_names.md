---
title: "Why ~$ or ~lock in some file names?"
date: 2010-08-18
forum: New to Ubuntu
---

### Post by Wtwine on 2010-08-18
HI

I have noticed some document files in my home directory with file names which start with ~, ~$ or ~lock.  They seem to be duplicates of existing files and first few letters of original file names have been replaced by these characters in the case of ~$.

What are these and can I delete them?

Thanks

---

### Post by Vaphell on 2010-08-18
~ is probably created by gedit - when you edit original file it creates a backup. You can disable it in preferences, i think.

~$ no idea what this is

~lock - my bet would be it's a file created by some app to assure that only 1 app/instance can use some resource. Existence of this file means no other instance tries to assume control over it.

---

### Post by fatality_uk on 2010-08-18
OpenOffice and many other do this. As Vaphell said, to prevent users opening multipple instances.

---

