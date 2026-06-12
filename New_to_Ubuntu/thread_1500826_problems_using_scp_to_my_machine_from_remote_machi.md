---
title: "problems using scp to my machine from remote machine"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by dagarshali on 2010-06-03
Hi,
I have installed the openssh server and am able to ssh to my laptop from remote machine. However, when i tried to copy using scp to my laptop from a remote machine, i get an error

s> cp -r dagarshali@129.186.17.133 /media/DATA/P90X/YOGA.mpg ./
cp: cannot stat `dagarshali@129.186.17.133': No such file or directory
cp: cannot stat `/media/DATA/P90X/YOGA.mpg': No such file or directory


Can anybody help me fix this problem.

Regards,
vishwa

---

### Post by RiceMonster on 2010-06-03
It's just a simple syntax error. You're missing a colon, and the command is "scp" :).
```
scp dagarshali@129.186.17.133:/media/DATA/P90X/YOGA.mpg ./
```

---

