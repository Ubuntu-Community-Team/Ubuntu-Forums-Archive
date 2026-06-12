---
title: "Please help me with cd command."
date: 2009-01-16
forum: New to Ubuntu
---

### Post by tahitiwibble on 2009-01-16
```
dad@dad-desktop:~$ md5sum ubuntu-8.10-desktop-i386.iso
md5sum: ubuntu-8.10-desktop-i386.iso: No such file or directory
dad@dad-desktop:~$ 
```

The file is on my desktop. Why isn't this working?

---

### Post by Crafty Kisses on 2009-01-16
Do the following:
```
cd /home/username/Desktop/filename
```

---

### Post by snova on 2009-01-16
```
cd Desktop
```

Then try it. :)

---

### Post by Son of William on 2009-01-16
Is the name of your computer dad-desktop?
the prompt usually reads [username]@[computername]:~$ if you are in your user directory.

From terminal try:

cd Desktop

You should then see something like dad@dad-desktop:~/Desktop$

**Make sure you use uppercase D at the beginning of Desktop

---

### Post by taurus on 2009-01-16
You are in a wrong directory.  You ran that command while you were in your $HOME but the file is in ~/Desktop.

```
cd ~/Desktop
md5sum ubuntu-8.10-desktop-i386.iso
```

---

### Post by tahitiwibble on 2009-01-16
Thanks very much you guys ............ I am grateful.

Now where did the little "thanks" stars go to and how can I mark the thread solved?

---

### Post by snova on 2009-01-16
> **tahitiwibble said:**
> Now where did the little "thanks" stars go to and how can I mark the thread solved?

They've been temporarily disabled for stability purposes; there's been some problems lately.

See: [http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481)

---

### Post by tahitiwibble on 2009-01-16
> **snova said:**
> They've been temporarily disabled for stability purposes; there's been some problems lately.

See: [http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481)


Oh jeez ...... hope that wasn't **my** fault :lolflag:

---

