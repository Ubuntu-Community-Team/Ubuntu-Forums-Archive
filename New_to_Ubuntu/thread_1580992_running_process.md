---
title: "running process ?"
date: 2010-09-24
forum: New to Ubuntu
---

### Post by BigDope on 2010-09-24
where can i see the total number of process that's running on my computer before i shut down ?

---

### Post by SlugSlug on 2010-09-24
to view processes I use

```
ps -ef
```

---

### Post by Gone fishing on 2010-09-24
I was thinking of:

```
top
```

---

### Post by Rubi1200 on 2010-09-24
Why do you need to know what processes are running when you shutdown the computer? If you can tell us what you are trying to achieve, we can then suggest the correct commands to use.

---

### Post by BigDope on 2010-09-24
> **SlugSlug said:**
> to view processes I use

```
ps -ef
```


thank you, but i don't understand what it shows ...

a big list....are they all running ?

> **Rubi1200 said:**
> Why do you need to know what processes are running when you shutdown the computer? If you can tell us what you are trying to achieve, we can then suggest the correct commands to use.

just to make sure that they are not forced to quit.

if any process is running, i would close it and then shut down.

---

### Post by MooPi on 2010-09-24
```
ps -u username
```
This will list only the processes by user.

---

