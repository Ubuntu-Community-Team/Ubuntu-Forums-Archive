---
title: "gcc /tmp folder problem"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by noidian on 2011-07-24
hi,

I am using code blocks 10.05 and i get a 5639 fatal error: can't write obj/Debug/comm.o : No space left on device.


I tried df /tmp which give me 65% usage i.e. there is still space.
Nevertheless, I changed the TMPDIR in .bashrc to another directory with space.

Anyone with an idea how to change any setting in Codeblocks maybe? Since I feel it keeps accessing /tmp still even though I changed in .bashrc or is my environment vairbale change wrong.

Thanks

---

### Post by noidian on 2011-07-24
well, I was working on a mounted file system i.e. the compilation directory was on a NTFS drive mounted.

If I copy it to the native home directory and run there is no error.

anyways to overcome the error?

---

