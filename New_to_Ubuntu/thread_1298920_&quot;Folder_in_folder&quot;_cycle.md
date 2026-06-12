---
title: "&quot;Folder in folder&quot; cycle?"
date: 2009-10-23
forum: New to Ubuntu
---

### Post by uncleV on 2009-10-23
In Ubuntu 9.04 32 bit when I go to the directory /usr/X11R6 there's a "bin" which is "Link to folder (inode/directory)" with target "../bin". If I open that link there's a huge amount of executable files and one X11 which is "Link to folder (inode/directory)" with target "." . 
If I open that X11-link I come to folder absolutely the same like the previous. And clicking on the new X11-link I would repeat this many times.

The attached screen shot illustrates the situation.

This happens also if I search a file placed in this link - the file is shown under many X11/, X11/X11/, ... , X11/X11/X11/X11/..............X11/ directories.

What causes this error and how did it happened on my system? Or it is a bug?

Thank you in advance.

P.S. My Ubuntu is clear install from md5sum'ed and checked LiveCD.

---

### Post by diesch on 2009-10-23
It's not a bug, it's a feature :-)

On some Unix/Linux version the folders /usr/X11R6/bin  and /usr/bin/X11 contain some files that Ubuntu has in /usr/bin/. 

To increase compatibility  /usr/X11R6/bin  and /usr/bin/X11 are symbolic links ("symlinks") to /usr/bin/ in Ubuntu. That is they are no real folders but just link to /usr/bin/.

So if you go to /usr/bin/X11/ it's the same as going to  /usr/bin/ - which means there is a folder X11 that is a symlink to /usr/bin/ that contains a folder X11 that is a symlink to /usr/bin/ that contains a folder X11 that is a symlink to /usr/bin/ that contains a folder X11 that is a symlink to /usr/bin/ that contains a folder X11 that is a symlink to /usr/bin/ that contains a folder X11 ... ;-)

---

### Post by uncleV on 2009-10-23
Thank you so much, sir!

Now I now the difference between "bug" and "feature":)

Edit: saw I missed a "k" up there. I'll leave it as is because it looks and sounds slightly like the cycle mentioned.

---

