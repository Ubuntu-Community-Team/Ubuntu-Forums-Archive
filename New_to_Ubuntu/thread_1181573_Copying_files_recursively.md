---
title: "Copying files recursively"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by k_squired on 2009-06-08
I want to copy the files from a man3 folder on my desktop into the man3 folder in my /usr/share/man3 directory.  As there are dozens of files, I do not with to do this manually.  How might I do this (via the terminal, I suppose?)

---

### Post by utnubuuser on 2009-06-08
1. cd /home/yourusername/Desktop

2. sudo cp man3 /usr/share/man3

That's if man3 doesn't already exist in /usr/share

else check "man cp" at the prompt to learn to merge the files

---

### Post by amingv on 2009-06-08
Just add the '-r' (recursive) parameter to your command. That will copy all the content in the folder and subfolders.

---

### Post by k_squired on 2009-06-08
Thanks, that sounds good, but I'm not sure I can translate anything from the man into 'merge.'  Could someone be so kind as to give me the command?

---

### Post by amingv on 2009-06-08
For example:
```
cd /home/username/Desktop/man3
sudo cp -r * /usr/share/man3
```

If there are no folders, you could even drop the '-r' and just use * instead of the filename.

---

