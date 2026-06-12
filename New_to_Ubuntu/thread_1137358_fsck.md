---
title: "fsck"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by sythe on 2009-04-25
I have a question about fsck. According to the ss64 man page (at [www.ss64.com/bash/fsck.html](www.ss64.com/bash/fsck.html)) for fsck, journaling file systems do not need to perform a fsck. Why then does Ubuntu perform one automatically at specific intervals? Isn't it unnecessary and a hassle for users?

Thanks.

---

### Post by ddrichardson on 2009-04-25
Really, you only need to run it when the file system is not cleanly unmounted. According to the [fsck.ext3 manpage]("http://linux.die.net/man/8/fsck.ext3"), the check only applies the journal then exits if the suberblock is OK so its not really running fsck anyway - just reapplying the journal every so many reboots.

---

