---
title: "Brasero not working for me."
date: 2010-03-01
forum: New to Ubuntu
---

### Post by georgep1993 on 2010-03-01
So i want to dual boot with WinXP, ive downloaded the files, gone onto brasero and it just keeps saying "preparing to write to cd", i googled it and it said to run brasero as root? i dont know how to do this, can anyone tell me? thanks

---

### Post by alexandari on 2010-03-01
```
sudo brasero
``` in the terminal

---

### Post by r-senior on 2010-03-01
You could ...

$ gksudo brasero

But shouldn't have to and you'd be better checking your permissions ...

System -> Administration -> Users and Groups

Click on Properties and then the User Privileges tab. Presumably "Use CDROM Drives" is the key? If you want to make changes, click on the "Click to make changes" button and it will ask you for your password.

---

