---
title: "Program to sync files with external disk"
date: 2009-09-03
forum: New to Ubuntu
---

### Post by Unstuck on 2009-09-03
I'm looking for a program that allows bi-directional sync-ing.  I'd like to share folders on my computers and an external drive.

---

### Post by unutbu on 2009-09-03
To copy everything in directory "source" to the "target" directory on the external disk:
```

rsync -a /path/to/source/ /media/external/target/
```

To copy everything in directory "source" to the "target" directory on the external disk and delete any files in target which are not in source:
```

rsync -a --delete /path/to/source/ /media/external/target/
```

And to reverse the sync'ing:
```

rsync -a --delete /media/external/target/ /path/to/source/ 
```

---

### Post by Unstuck on 2009-09-03
I should have known it could be done through the terminal.  It worked well...I was surprised there wasn't any kind of output, though.

Thanks, unutbu!

---

### Post by unutbu on 2009-09-03
You can get "verbose" output by using the -v flag. For example:
```

rsync -av --delete /path/to/source/ /media/external/target/
```

Or even
```

rsync -av --progress --stats --delete /path/to/source/ /media/external/target/

```
--progress tells rsync to show progress during transfer
--stats tells rsync to give some file-transfer stats.

---

### Post by MrWES on 2009-09-03
> **Unstuck said:**
> I should have known it could be done through the terminal.  It worked well...I was surprised there wasn't any kind of output, though.

Thanks, unutbu!

if you run it from a crontab you'll get a system email. Or you can use the GUI to rsync, grsync

---

