---
title: "How can I know which Ubuntu, x86 or x64, I installed?"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by Hukei on 2010-05-12
How can I know which Ubuntu, x86 or x64, I installed?

I can't recall which one I installed...  x.x

I want to know because I want to do a clean install of 10.04 but I can't recall if this Ubuntu is x86 or x64.

---

### Post by bodhi.zazen on 2010-05-12
Open a terminal and enter:

```
uname -m
```

i686 = 32 bit
x86_64 = 64 bit

---

### Post by Irony on 2010-05-12
In terminal issue;

```
uname -a
```

Mine is;

```
Linux ubuntu 2.6.31-21-generic #59-Ubuntu SMP Wed Mar 24 07:28:27 UTC 2010 x86_64 GNU/Linux
```

Which indicates 64 bit. Also if you look in your filesystem you will see a folder called;

```
/lib64
```

Indicating 64 bit.

---

### Post by tom.swartz07 on 2010-05-12
uname -a 

will tell you exactly every stat about your system that you need to know.

For example, my output would be
```
Linux gallifrey 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:28:05 UTC 2010 x86_64 GNU/Linux
```

If you run with -m, as the guy above said; it would just tell you the type x86 or x64

---

### Post by Irony on 2010-05-12
Also if your hardware is capable of 64 bit then you might as well install 64 bit.

---

### Post by Hukei on 2010-05-12
Thanks a lot guys!

I found that the ubuntu I had was the 32bit. I tried to boot up the 64 bit cd of ubuntu 9.10 and it gave me an error saying that the processor didn't support it. I'll stay with the 32 bit Ubuntu then. Thanks again!

---

