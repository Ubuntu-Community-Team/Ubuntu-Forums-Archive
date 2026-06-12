---
title: "fusermount"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by Vincent De Groote on 2009-04-12
Hello,

I followed the page 

[https://help.ubuntu.com/community/FolderEncryption](https://help.ubuntu.com/community/FolderEncryption)

to setup an encrypted directory.  This page tells that

fusermount -u ~/visible

should unmount the encrypted folder.  But I have an error

fusermount: entry for /xxx not found in /etc/mtab 

where /xxx is the visible folder.

What should I write in /etc/mtab to make it work ?

Thanks for your replies

Vincent De Groote

---

### Post by The Cog on 2009-04-12
I suspect that you didn't mount the encrypted folder properly in the first place. That's the error message I get if I try to unmount it when it's not mounted.

If you mounted the directory properly in the forst place, two thongs should happen:
1: An icon for the directory appears on your desktop, and
2: the command **mount** shows it being mounted.

---

