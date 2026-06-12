---
title: "Softlink and Hardlink confirmation (cp, cp -l, ln, ln -s)"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by televisi on 2009-08-28
Hi All,
Can you please verify the following statements for me? so I can have better understanding in Linux / Ubuntu

**ln -s <source> <destination>**, 

[LIST]
[*]Similar to shortcut in Windows
[*]creating _small 'link file' under [COLOR=Red]different [/COLOR]inode_
[*]if source file content changed, the destination also changed and vice versa
[*]if source deleted / moved, it will _lose the 'link' to the destination file _
[*]Also called by [B]softlink / symbolic link
[/B]
[/LIST]
**ln**** <source> <destination>**, 

[LIST]
[*]creating _same file content under [COLOR=Navy]same [/COLOR]inode _
[*]if source file content changed, the destination also changed and vice versa.
[*]if source file deleted, it will not delete the destination
[*]Also called by **hardlink**
[/LIST]
**cp -l**** <source> <destination>** 
[LIST]
[*]totally the same as **ln** command
[/LIST]
**cp** **<source> <destination>**

[LIST]
[*]creating totally a _[COLOR=Red]different [/COLOR]same file content under [COLOR=Red]different [/COLOR]inode_
[*]if source file changed, destination file will not changed
[*]if source file deleted, destination file will not changed / deleted
[/LIST]
Thanks heaps

---

### Post by rajeev1204 on 2009-08-28
> **televisi said:**
> Hi All,
Can you please verify the following statements for me? so I can have better understanding in Linux / Ubuntu

**ln -s <source> <destination>**, 

[LIST]
[*]Similar to shortcut in Windows
[*]creating _small 'link file' under [COLOR=Red]different [/COLOR]inode_
[*]if source file content changed, the destination also changed and vice versa
[*]if source deleted / moved, it will _lose the 'link' to the destination file _
[*]Also called by [B]softlink / symbolic link
[/B]
[/LIST]
**ln**** <source> <destination>**, 

[LIST]
[*]creating _same file content under [COLOR=Navy]same [/COLOR]inode _
[*]if source file content changed, the destination also changed and vice versa.


[*]if source file deleted, it will not delete the destination
[*]Also called by **hardlink**
[/LIST]
**cp -l**** <source> <destination>** 
[LIST]
[*]totally the same as **ln** command
[/LIST]
**cp** **<source> <destination>**

[LIST]
[*]creating totally a _[COLOR=Red]different [/COLOR]same file content under [COLOR=Red]different [/COLOR]inode_
[*]if source file changed, destination file will not changed
[*]if source file deleted, destination file will not changed / deleted
[/LIST]
Thanks heaps

Maybe this will explain better.

[http://ubuntuforums.org/archive/index.php/t-287447.html](http://ubuntuforums.org/archive/index.php/t-287447.html)

A hard disk is like two names for the same file.If you change one,the other one also changes.Because even though you are seeing 2 files ,they really are the same file.You could even move their locations and edit one to see same changes in the other.

The rest of the stuff is correct i suppose.
But iam not sure about the cp -l, i think its same as ln -s, that means a soft link.

---

### Post by televisi on 2009-08-29
Is that correct that hardlinks cannot be created under 2 different partitions / drives / disks?

---

### Post by gsocker on 2009-08-29
> Is that correct that hardlinks cannot be created under 2 different partitions / drives / disks?
Yes. 
A hardlink does not create a duplicate  file; it creates another reference to the same inode.

More detailed explanation: In Windows filesystems the basic reference is the filename. Each file has different one - and only one.

However, in Unix filesystems the basic reference is the inode. This has one(or more) filenames "linked" to it. When you run ln without the -s option, it creates another filename "linked" to the same inode. Since it is merely another link to the same inode, it cannot span different partitions. 


Symbolic links can, since they are usually nothing more than a string pointing to the destination file name that are treated as a special case by the OS.

---

