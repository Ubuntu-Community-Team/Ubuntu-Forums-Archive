---
title: "Why is Xarchiver broken?"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by brawnypandora0 on 2011-07-20
I downloaded a video .rar file. When I right click "Extract" I get a message that says:

An error occurred! Please check the 'Store Archiver Output' option to see it.

What does this mean? How do I fix it?

---

### Post by frankbooth on 2011-07-20
Might sound stupid, but...

Do you have *unrar* installed? :-k

---

### Post by jtarin on 2011-07-20
> **frankbooth said:**
> Might sound stupid, but...

Do you have *unrar* installed? :-kNo it's not stupid to have unrar installed.:P

---

### Post by brawnypandora0 on 2011-07-20
What do you mean?

---

### Post by cjazz on 2011-07-20
Um, did you actually check the "Store Archiver Output" option and view the error, as suggested?

---

### Post by jtarin on 2011-07-20
Using a terminal change to the directory your .rar file is stored.
Once in the directory issue the command ```
unrar e <filename>
```now your terminal will show any error encountered.Post full error here.
Is this a multi-part archive?

---

### Post by brawnypandora0 on 2011-07-22
> **jtarin said:**
> Using a terminal change to the directory your .rar file is stored.
Once in the directory issue the command ```
unrar e <filename>
```now your terminal will show any error encountered.Post full error here.
Is this a multi-part archive?

~ $ unrar e smith

UNRAR 3.90 beta 2 freeware      Copyright (c) 1993-2009 Alexander Roshal

Cannot open smith.rar
No such file or directory
No files to extract


It's still not working.

---

### Post by brawnypandora0 on 2011-07-22
> **cjazz said:**
> Um, did you actually check the "Store Archiver Output" option and view the error, as suggested?

Where do I find that option?

---

### Post by jtarin on 2011-07-22
> **brawnypandora0 said:**
> ~ $ unrar e smith

UNRAR 3.90 beta 2 freeware      Copyright (c) 1993-2009 Alexander Roshal

Cannot open smith.rar
No such file or directory
No files to extract


It's still not working.Let's say your file you want to extract is on the Desktop. In a terminal you would type ```
cd Desktop
```Once you are there type the command ```
ls
```this will list all files on the Desktop....do you see your file listed? 
If yes issue the .rar command I gave....if not you either don't have the file or you have placed it somewhere else. Pay attention to error messages.....that's what they are for. 
Try to be a little more intuitive. If it says it's not there......it's not there. 
Make sure you type the file name correctly.
If everything is done accordingly it should extract.....if not you might have a corrupted file or one that needs a password.

---

