---
title: "I cannot open or browse my hard drive."
date: 2010-03-09
forum: New to Ubuntu
---

### Post by Fläsh on 2010-03-09
Alright this quite stupid inserted a disk (orange box) i did 

```
mkdir /home/<myusername>/Desktop/Orange_Files
``` to copy them over i did 
```
cp /media/cdrom/* /home/<myusername>/Desktop/Orange_Files
```

---

### Post by Psumi on 2010-03-16
So... what's the error that comes up in terminal?

---

### Post by NickJones on 2010-03-16
I don't see a problem, you created a directory, you pasted into it, fin?

---

### Post by aeiah on 2010-03-16
you didnt really ask a question, but i think what you should have done was:

```
cp -R /media/cdrom/* /home/<myusername>/Desktop/Orange_Files/
```

so you get all the folders as well as files.

---

### Post by fatality_uk on 2010-03-16
> **aeiah said:**
> you didnt really ask a question, but i think what you should have done was:

```
cp -R /media/cdrom/* /home/<myusername>/Desktop/Orange_Files/
```

so you get all the folders as well as files.

FYI The -R tells the copy command to recusivly look through the directories. [http://linuxmanpages.com/man1/cp.1.php](http://linuxmanpages.com/man1/cp.1.php)

---

