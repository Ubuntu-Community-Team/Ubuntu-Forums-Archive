---
title: "Question about the find command and micro-SD card"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Iecur on 2011-03-02
Hi, running Ubuntu 10.10 64-bit.

I've been doing some cleaning up on my computer.  Deleting/moving a lot of stuff here and there.  And I was trying to move some files around.  No clue how to my guess is something to do with find and executing cp.  I'm sure I can figure that out.  Now my question about find.

I've been using find for quite some time now and it's been a great little program.  But now that I'm looking for files on one of my micro-SD card I get some error.

When I use it on ext4 or ntfs file system like:
$ find . -iname *.sav
It'll search no problem but when I try that exact same command on my micro-SD card using a USB adapter(FAT..32 I believe ?) I get this:
$ find . -iname *.sav
find: paths must precede expression: dummy.sav
Usage: find [-H] [-L] [-P] [-Olevel] [-D help|tree|search|stat|rates|opt|exec] [path...] [expression]

I go back to my hard drives and the command works perfectly fine.  I don't remember reading anything on the man/info pages on issues with none hard drive media ?  I think it's worked fine on thumb drives as well should check...  Sorry if something not clear..It's quite late and yeah.  If you need any more information just let me know.  Any help would be greatly appreciated.  Thanks in advance.

---

### Post by TeoBigusGeekus on 2011-03-02
Try
```
find . -iname '*.sav'
```

---

### Post by Iecur on 2011-03-03
Hmm..now it works with or without the quote what the hell was going on yesterday ?  I guess I'll mark this as solved ? o.O;

Or more like wishing I could just delete this thread..

Wait no that only worked at the root of the directory.  When I go to a subfolder I do seem to need that.  Hmm..weird.  Much appreciated though.

---

