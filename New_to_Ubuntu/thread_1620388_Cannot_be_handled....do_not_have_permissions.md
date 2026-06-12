---
title: "Cannot be handled....do not have permissions"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by Stephen_A on 2010-11-13
Running an IBM Thinkpad on a Live CD to retrieve some Linux files from another drive. (Long story). 

If I try to copy the files, I get the error message: 

> The folder ".mozilla-thunderbird" cannot be handled because you do not have permissions to read it.

Would anyone be so kind as to advise me how to fix this? Thanks in advance. 

Stephen

---

### Post by bryangwilliam on 2010-11-13
Try
```

chmod 755 .mozilla-thunderbird

```
That should give you the permission you need to copy it.

---

### Post by Stephen_A on 2010-11-13
Thanks, but that gives: 

> chmod: cannot access `.mozilla-thunderbird': No such file or directory


---

### Post by bryangwilliam on 2010-11-13
Are you running the command from within the directory where .mozilla-thunderbird is located?

If not, change to that directory first and it should find it no problem.

You will probably want to add a -R in there as well to make sure it grabs all the files inside too.
```

chmod -R 755 .mozilla-thunderbird

```

---

### Post by Stephen_A on 2010-11-13
No I'm not, and have a little trouble getting there. The file is on an external drive, but the drive does not appear on ls: 

> ubuntu@ubuntu:~$ ls
Desktop  Documents  Music  Pictures  Public  Templates  Videos


How do I navigate the terminal to that external drive?

---

### Post by Stephen_A on 2010-11-13
OK OK...figured that out. Let you know if it works.

---

### Post by Stephen_A on 2010-11-13
Now there is this problem. 

> ubuntu@ubuntu:/media/disk/home/stephen$ chmod -R 755 .mozilla-thunderbird -R
chmod: changing permissions of `.mozilla-thunderbird': Operation not permitted
chmod: cannot read directory `.mozilla-thunderbird': Permission denied


Any suggestions?

---

### Post by Stephen_A on 2010-11-13
Just tried the cp command and got a similar problem: 

> ubuntu@ubuntu:/media/disk/home/stephen$ cp -r .mozilla-thunderbird /media/IBM_PRELOAD/Setup
cp: cannot access `.mozilla-thunderbird': Permission denied


---

### Post by Daniel0108 on 2010-11-13
> **Stephen_A said:**
> Now there is this problem. 
Any suggestions?
Yes!
you have to add SUDO before the command :P
like:
```
sudo cp -r .mozilla-thunderbird /media/IBM_PRELOAD/Setup
```
That should work.
Yours,
Daniel

---

### Post by Stephen_A on 2010-11-13
Daniell, 
You are a scholar and a gent. That indeed did the trick. Many thanks. 

Bryan, 
Thank you too for taking the time to answer. 

Stephen. 

> **Daniel0108 said:**
> Yes!
you have to add SUDO before the command :P
like:
```
sudo cp -r .mozilla-thunderbird /media/IBM_PRELOAD/Setup
```
That should work.
Yours,
Daniel

---

### Post by Daniel0108 on 2010-11-13
> **Stephen_A said:**
> Daniell, 
You are a scholar and a gent. That indeed did the trick. Many thanks. 

No, problem :D
SOLVED :D

---

