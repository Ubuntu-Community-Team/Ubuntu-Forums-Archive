---
title: "No sound dell vostro a90 latest ubuntu netbook remix"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by jmitche1 on 2009-09-20
Hello all,
I made a search and found others having the same problem as me but the solutions were too advanced for someone new to linux as myself. 

My Dell Vostro A90 is loaded with Ubuntu 9.04 netbook remix and currently has no sound at all. No start ups, no music, nada. 

Does anyone know a solution to this problem? What other information is needed to help solve it. 

Thanks a lot and sorry as again I am very new to Ubuntu/Linux.

---

### Post by Liolikas on 2009-09-20
We need info about your sound card you can get it with command:
```

sudo lspci|grep audio

```
And paste output here.

---

### Post by jmitche1 on 2009-09-21
It must be me doing something wrong as when I open the terminal and paste your command nothing happens. I enter my password and Another line comes up identical to the one above it asking me to re enter the command. This is what I see:

guest@guest-laptop:~$ sudo lspci|grep audio
[sudo] password for guest: 
guest@guest-laptop:~$ sudo lspci|grep audio
guest@guest-laptop:~$ 

Any ideas?

---

### Post by kambrik on 2009-09-21
Try this [http://www.compuhowto.com/linux/ubuntu/ubuntu-no-sound/]("http://www.compuhowto.com/linux/ubuntu/ubuntu-no-sound/")

---

### Post by jmitche1 on 2009-09-22
Got really far in the last post but still no luck. I'll search google some more but if you guys have any other ideas please and thanks!

---

### Post by jmitche1 on 2009-09-22
[http://ubuntuforums.org/showthread.php?t=1153272](http://ubuntuforums.org/showthread.php?t=1153272)
This solved the problem.. Thanks all for your help.

---

