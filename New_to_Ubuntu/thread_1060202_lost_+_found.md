---
title: "lost + found"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by mhh91 on 2009-02-04
what is this directory doing on my partitions?


and is it like "system volume information" in windows?


thanks in advance :)

---

### Post by jerome1232 on 2009-02-04
When fsck recovers file-system errors sometimes it finds partially recoverable files. fsck sticks these partial files in lost+found  hoping that there's a chance they can still be recovered.

---

### Post by ridetheteapot on 2009-02-04
If your partition get bungled (ie shutdown during massive write session) and you fsck is run afterwards it might be finding lots of files that basicly lost their names. fsck will ask you if you want to reconnect the file or something like that, and if you say yes then it will put the file in the lost + found folder with its inode being the new file name.
Its not a good situation... and it could be me but i have found that ext3 is a pro at making this bad situation worse (so i use reiser)

---

### Post by mhh91 on 2009-02-12
thanks 4 the info :)

---

