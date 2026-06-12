---
title: "Shortcut to sudo chmod"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by UpSignal on 2010-05-26
Goal: Making a shortcut on my menu, to chmod +x a specific SH file.
Steps done so far:

su - username -c /sbin/chmod +x Documents/directory/subdirectory/testfile.sh

i've choosen "application in terminal", and closed. went to run it, it opens terminal and asks for my password. after i type, it closes. and the file was not chmoded...
I open up terminal and typed directly, and found out:

+x: /sbin/chmod: No such file or directory

What am i doing wrong? i need a shortcut or script to chmod that file automatically, because it changes a lot of times per week. So, i'm tired to chmod it

---

### Post by anarchywolf46 on 2010-05-26
It's /bin/chmod not /sbin/chmod

---

### Post by UpSignal on 2010-05-26
> **anarchywolf46 said:**
> It's /bin/chmod not /sbin/chmod

fixed, but now says:

/bin/chmod: missing operand

---

### Post by yetiman64 on 2010-05-26
Hi UpSignal

Try out,

```
su - username -c /bin/chmod +x /home/<your-username>/Documents/directory/subdirectory/testfile.sh
```replacing <your-username> with your actual username of course. 

It appears from your first command posted that you don't have a complete path listed. Good luck.

---

### Post by UpSignal on 2010-05-26
done. thanks guys, i missed the " " , XD

---

