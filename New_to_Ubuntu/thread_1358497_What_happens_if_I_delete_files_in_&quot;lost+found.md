---
title: "What happens if I delete files in &quot;lost+found&quot;"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by Ralph L on 2009-12-18
I had some disk problems a while back and ran fsck to clear them up.  Now I have a bunch of stuff in lost+found.  If I delete those will I damage my disk system?  I need the space.

Also, while trying to access the files I noticed that the command "sudo cd ........." did not work.  Hence I had to type in the whole path name to get to lost+found.  Is there anyway to make cd work with sudo?

Running karmic.

Thanks
Ralph

---

### Post by audiomick on 2009-12-18
Hallo.
CD and sudo do work together as far as I know.
Lost + found is a bit of a special case, I think. As I understand it, it is used by file system  admin tools ( e.g fsck ) as a parking place for broken and orphaned files. You have observed this yourself.

Don't know about erasing though. Sorry.

---

### Post by halitech on 2009-12-18
as far as I know, you don't need sudo to change to any directory. As audiomick has stated, Lost+found is a locked folder and is protected. If you really need to see whats in there, run
```
gksudo nautilus
``` and browse to the directory. [color="red"]Word of warning, you can really mess up your system using nautilus as sudo so be very very careful[/color]

---

