---
title: "help building from source - e2retrieve"
date: 2009-09-05
forum: New to Ubuntu
---

### Post by emarkd on 2009-09-05
Ok, I've had a disk failure in an lvm group and need to recover the data from the other two disks.  From what I've read, e2retrieve should do just that, but I can't get it to build.  The software is at [http://www.guzu.net/linux/e2retrieve.php]("http://www.guzu.net/linux/e2retrieve.php").  I've got the e2fsprogs package installed, which is supposed to be the only dependency, but when I run 'make' I get this:

```
gcc -D_FILE_OFFSET_BITS=64 -D_LARGEFILE_SOURCE -D_LARGEFILE64_SOURCE -O2 -Wall -W   -c -o src/core.o src/core.c
In file included from src/core.c:20:
src/e2retrieve.h:31:27: error: ext2fs/ext2fs.h: No such file or directory
In file included from src/core.c:20:
src/e2retrieve.h:186: warning: ‘struct ext2_dir_entry_2’ declared inside parameter list
src/e2retrieve.h:186: warning: its scope is only this definition or declaration, which is probably not what you want
src/e2retrieve.h:234: error: expected declaration specifiers or ‘...’ before ‘__u16’
src/core.c: In function ‘user_interrupt_handler’:
src/core.c:214: warning: unused parameter ‘__unused’
src/core.c: In function ‘dump_progress’:
src/core.c:218: warning: unused parameter ‘__unused’
src/core.c: In function ‘orphans_dump_progress’:
src/core.c:226: warning: unused parameter ‘__unused’
src/core.c: In function ‘display_progress’:
src/core.c:234: warning: unused parameter ‘__unused’
make: *** [src/core.o] Error 1
```

Any C programmers out there who can help?

Thanks,
-Mark

---

### Post by unutbu on 2009-09-05
The first error appears to be:
```

src/e2retrieve.h:31:27: error: ext2fs/ext2fs.h: No such file or directory
```

packages.ubuntu.com says ext2fs.h is provided by the e2fslibs-dev package:

[http://packages.ubuntu.com/search?searchon=contents&keywords=ext2fs.h&mode=&suite=jaunty&arch=any](http://packages.ubuntu.com/search?searchon=contents&keywords=ext2fs.h&mode=&suite=jaunty&arch=any)

So perhaps check if you have e2fslibs-dev installed.

---

### Post by emarkd on 2009-09-05
You're right.  I should've seen that.  Thanks for the help.  Now I just hope the software does what it claims to be able to do.

Thanks again,
-Mark

---

### Post by unutbu on 2009-09-06
Good luck. Please let us know how it goes.

---

