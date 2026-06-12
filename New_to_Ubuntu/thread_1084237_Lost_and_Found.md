---
title: "Lost and Found"
date: 2009-03-01
forum: New to Ubuntu
---

### Post by thestretchman on 2009-03-01
During a recent file search I "discovered" a file called "Lost and Found" in my File System. When I clicked it told me I could not enter because I did not have the necessary permissions. This has set my spidey sense tingling. 

Is this file supposed to be there, and what is in there that someone doesn't want me to poke at?

Thanks

Stretch

---

### Post by theozzlives on 2009-03-01
In Windows you have "System Volume Information" that you can't get to. "Lost and Found" is just lost clusters found during a disk check.

---

### Post by Old_Grey_Wolf on 2009-03-01
look at [http://ubuntuforums.org/showthread.php?t=229143](http://ubuntuforums.org/showthread.php?t=229143)

---

### Post by thestretchman on 2009-03-01
Thank you both. 

Stretch

---

### Post by asmoore82 on 2009-03-01
and if you delete it off of any ext2/ext3 filesystem the next
filesystem check will throw a warning message and re-create it.

Don't ask how I know that :-\"

---

