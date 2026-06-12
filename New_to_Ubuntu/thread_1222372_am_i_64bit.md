---
title: "am i 64bit?"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by ELD on 2009-07-24
I am sure i installed 64bit but i can't find anywhere that says it, how do i find out if i am or not?

---

### Post by wojox on 2009-07-24
```
uname -a
```

i686 32 bit | x86_64 64 bit

---

### Post by aesis05401 on 2009-07-24
> **ELD said:**
> I am sure i installed 64bit but i can't find anywhere that says it, how do i find out if i am or not?

```

uname -a

```

---

### Post by ELD on 2009-07-24
Got this:

Linux liam-desktop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux

I take it i am from the "_64" right?

---

### Post by LookTJ on 2009-07-24
> **ELD said:**
> Got this:

Linux liam-desktop 2.6.28-13-generic #45-Ubuntu SMP Tue Jun 30 22:12:12 UTC 2009 x86_64 GNU/Linux

I take it i am from the "_64" right?
You are running the 64bit Ubuntu version

Also it's better to use uname -m(thanks bodhi.zaren:))

---

### Post by ELD on 2009-07-24
Thanks guys.

---

### Post by LookTJ on 2009-07-24
Also, to check that your cpu is 64bit

```
cat /proc/cpuinfo | grep lm
```

just in case you run a 32bit OS ;)

---

### Post by ELD on 2009-07-24
As you can see from my signature i run a core 2 quad, which is 64bit capable ;)

---

