---
title: "using cd command"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by ZiaSonNAS on 2010-10-08
In terminal mode, why can't I cd into a directory I just created? If I enter *ls *I can see the directory (practicefiles) but when I type *cd /practicefiles* it returns "no such file or directory" What am I doing wrong? Sorry for such a silly question and thanks for the help.

---

### Post by holiday on 2010-10-08
> **ZiaSonNAS said:**
> In terminal mode, why can't I cd into a directory I just created? If I enter *ls *I can see the directory (practicefiles) but when I type *cd /practicefiles* it returns "no such file or directory" What am I doing wrong? Sorry for such a silly question and thanks for the help.

Did you create the directory under /?

I suspect you didn't. So while in the directory you were in when you created the new one, then go 

$ cd practicefiles

---

### Post by llamabr on 2010-10-08
Also, go to the directory where you think it is, and post:

```
ls -lh practicefile
```

and if nothing comes back:

```
ls -lh
```

I suspect you didn't make it, or didn't put it where you think you did.  How did you create this folder?

---

### Post by l-x-l on 2010-10-08
> **holiday said:**
> Did you create the directory under /?

I suspect you didn't. So while in the directory you were in when you created the new one, then go 

$ cd practicefiles

+1. When you put /in front of a filename you're telling it to change to a subdirectory in the root directory.

Just do a cd practicefiles.

---

### Post by ZiaSonNAS on 2010-10-08
Thanks folks...problem solved. Just a question of getting to the right directory.

---

