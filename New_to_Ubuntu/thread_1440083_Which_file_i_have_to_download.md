---
title: "Which file i have to download?"
date: 2010-03-27
forum: New to Ubuntu
---

### Post by karthick87 on 2010-03-27
I like to install **truecrypt **package,but i found two packages in their website for ubuntu named "**Ubuntu -x86.deb**" and "**Ubuntu -x64.deb**" So can anyone tell me the difference between these two packages..?

---

### Post by Gixxy on 2010-03-27
x86 is for a 32bit system and the x64 is for a 64bit system.

---

### Post by karthick87 on 2010-03-27
How to check my system to find whether it is 32bit or 64 bit?

---

### Post by infinitejones on 2010-03-27
Open a terminal and type in

```
uname -a
```

A string of data will appear when you press enter. If it's got either x86_64 or ia64 in it, you're on a 64bit machine, and if it's got i686, you're on a 32bit machine.

Chances are you're 32bit but it's worth checking. If you get really stuck, type that command and copy/paste the output here.

---

### Post by karthick87 on 2010-03-27
Ya i found its 32 bit..


```
karthick@Learners-desktop:~$ uname -a
Linux Learners-desktop 2.6.28-11-generic #42-Ubuntu SMP Fri Apr 17 01:57:59 UTC 2009 i686 GNU/Linux
```

---

### Post by Gixxy on 2010-03-27
> **getyourkarthick said:**
> How to check my system to find whether it is 32bit or 64 bit?

```
uname -a
```

mine is 32bit and gives an output of 

> 2.6.31-20-generic #58-Ubuntu SMP Fri Mar 12 05:23:09 UTC 2010 i686 GNU/Linux


---

