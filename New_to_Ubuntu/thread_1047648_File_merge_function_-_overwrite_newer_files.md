---
title: "File merge function - overwrite newer files"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by seattle vic on 2009-01-22
I have a need to do spot backups from one of my (ubuntu) machines to another, usually a directory, and wonder if there's a simple way to do so, say using nautilus.  If I do a copy of a directory to a place where that same directory has been previously placed, nautilus will ask me if I want to merge.  If I say yes, then it stops when file names are identical, but only asks me if I want to skip.

What I really want it to do is overwrite on newer file date.

I don't need a complicated backup program, if this can be made to work.

Thanks in advance.

---

### Post by vhegos on 2009-01-22
I suggest giving the rsync command a try.  It will perform your backup by making a copy only of files that have changed since the last backup.

```
rsync [OPTION...] SRC... [DEST]
```

You can of course read the rsync man page for more details.

---

### Post by seattle vic on 2009-01-22
> **vhegos said:**
> I suggest giving the rsync command a try.  It will perform your backup by making a copy only of files that have changed since the last backup.

```
rsync [OPTION...] SRC... [DEST]
```

You can of course read the rsync man page for more details.

Thanks.  I got it to work, and it will do.  I was sort of looking for why Nautilus doesn't allow you to overwrite older files.  Unlike windows explorer, it doesn't even give you the dates/times of the files your're about to overwrite.

---

### Post by vhegos on 2009-01-23
Yeah, I don't know why nautilus doesn't behave exactly like windows explorer.  What I can tell you from experience is that moving, merging, copying files/folders is an order of magnitude easier/faster/more flexible than clicking, dragging, dropping, and hitting skip, overwrite, ect...but don't take my word for it.  :)

---

