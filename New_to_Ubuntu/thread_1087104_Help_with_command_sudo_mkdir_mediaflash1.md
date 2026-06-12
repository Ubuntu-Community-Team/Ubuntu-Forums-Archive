---
title: "Help with command sudo mkdir /media/flash1"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-04
I went to try something to get my card reader working, and created a directory called flash 1 in media.

This was the command used...

sudo mkdir /media/flash1


I'm new and I don't want that directory anymore...

Can someone tell me how to remove it, and explain what that code above actually did? mkdir (make directory?) if so, why can't I just delete it?

---

### Post by kanikilu on 2009-03-04
Assuming you've unmounted the media, you should be able to remove the directory (mount point) with: ```
sudo rmdir /media/flash1
```

---

### Post by bodhi.zazen on 2009-03-04
So long as the directory is empty rmdir will work.

you can also use

```
rm -rf /media/flash1
```

But be careful with that command as it will delete the directory and ALL CONTENTS (make darn sure the flash drive is unmounted ;) ).

---

### Post by Gp. on 2009-03-04
rm = remove

what does -rf do?

Thnx for the help btw.

---

### Post by kanikilu on 2009-03-04
> **Gp. said:**
> rm = remove

what does -rf do?

Thnx for the help btw.

**r**ecursive: traverses down through the directory structure beginning from the directory you specify - in other words, it goes through sub-directories and removes everything in it's wake ;-)

**f**orce: removes files without your confirmation

```
man rm
``` for all the options.

// Edit - it goes without saying, but don't be liberal with the rm -rf usage (especially when sudo is involved!), you can easily hose your system or unwittingly lose important data.

---

### Post by Nxion on 2009-03-04
> **Gp. said:**
> rm = remove

what does -rf do?

Thnx for the help btw.

-r =  delete recursively and is used to delete the directory tree starting at the directory specified i.e. it deletes the specified directory along with its sub-directory and files.

-f = deletes read-only files immediately without any confirmation.If both -f and -i are used then the one which appears last in the terminal is used by rm.

Check this out for more info:

[URL="https://help.ubuntu.com/community/DeletingFiles"]https://help.ubuntu.com/community/DeletingFiles
[/URL]

---

