---
title: "Note pad ++"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by absentcrisis on 2010-12-17
I am trying to install notepad ++ and I have downloaded wine by the terminal command sudo apt-get install wine. I have downloaded the .exe for notepad and it gives me a permissions error saying it can execute. How would I change the permissions to allow wine to execute the .exe file?

---

### Post by rcayea on 2010-12-17
right click on the .exe and go to the permissions tab. be sure the box at the bottom is checked to allow you to execute the program.

---

### Post by khelben1979 on 2010-12-18
Use ```
chmod 755
``` on the file and it will get executable. Use ```
man chmod
``` if you feel uncertain about this advice.

---

### Post by aG93IGRvIGkgdWJ1bnR1Pw== on 2010-12-18
Open the terminal, navigate to the folder you've saved it in and enter

```
chmod +x <your filename>
```

---

