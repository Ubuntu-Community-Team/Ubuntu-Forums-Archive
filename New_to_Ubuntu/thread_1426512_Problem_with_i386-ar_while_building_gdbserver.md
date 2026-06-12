---
title: "Problem with i386-ar while building gdbserver?"
date: 2010-03-10
forum: New to Ubuntu
---

### Post by Fanatico on 2010-03-10
I am running Ubuntu 9.10 and trying to build gdbserver for ARM target using the instructions from
[http://bhagwat-masalkar.blogspot.com/2008/05/remote-debugging-for-arm-target-board.html](http://bhagwat-masalkar.blogspot.com/2008/05/remote-debugging-for-arm-target-board.html)

The make command, cause the following error at the end of building process:

./libtool: line 1086: i386-ar: command not found
make[4]: *** [libbfd.la] Error 127
make[4]: Leaving directory `/home/magic/.local/share/Trash/files/gdb-7.3.0.1/bfd'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/magic/.local/share/Trash/files/gdb-7.3.0.1/bfd'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/magic/.local/share/Trash/files/gdb-7.3.0.1/bfd'
make[1]: *** [all-bfd] Error 2
make[1]: Leaving directory `/home/magic/.local/share/Trash/files/gdb-7.3.0.1'
make: *** [all] Error 2

Can anyone advise what is the problem with i386-ar?

Thanks

---

