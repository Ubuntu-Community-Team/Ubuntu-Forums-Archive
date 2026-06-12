---
title: "permissions with live cd"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by DarinB on 2010-10-21
Using LM 9 10.04 lucid build my hdd died I am trying to transfer the vital stuff to a laptop via a thumb drive...some files have and X or lock, I could change some permissions manually per file...and then transfer them...I used mint user is there any way to do the entire drive? with terminal and make this process easier? I don't knwo why some files are locked and others not?

---

### Post by LowSky on 2010-10-21
open nautilus (the filemanager) using sudo, easiest way is by terminal

```
gksu nautilus
```

you should then have root access to all files, and transfer should be easier

---

### Post by AngusH on 2010-10-21
The above is best for your purposes, but for anyone who does want to change the perms of an entire directory just use chmod with the -R flag ie. ```
chmod 700 /media/backup -R
```.
Angus

---

### Post by DarinB on 2010-10-21
what will chmod 700 do and will it let me copy over files and subfiles?

---

### Post by AngusH on 2010-10-21
Like I say it's not what you want for this case but it will change the perms on every file in the specified dir so that the owner has read write execute permissions and group and others have nothing. DON'T DO THAT FOR A FILESYSTEM FOLDER. IT WILL CHANGE THE PERMS OF SYSTEM CRITICAL FILES.
For your case just open up a root file browser like LowSky suggested. 
Angus.

---

### Post by DarinB on 2010-10-21
ok I did it with gksu nautilus i can access the files but they will not copy over to the usb thumb drive or to a cd.
I am kind of stuck, any Ideas?

---

