---
title: "How do I know if I have X64 Ubuntu?"
date: 2009-08-13
forum: New to Ubuntu
---

### Post by rlhoman on 2009-08-13
I recently installed Ubuntu 9.04 (under Windows Vista).  I am trying to download a program (Trucrypt) which asks if I have the 64 bit version of Ubuntu installed.  How do I figure out if I do?

---

### Post by lisati on 2009-08-13
from the command prompt (Applications->accessories->terminal) type:
```
uname -a
```
If you see 'x86_64' in the output, you are running the 64-bit version of Ubuntu.

---

### Post by rednano12 on 2009-08-13
```
uname -a
```

---

### Post by pizza-is-good on 2009-08-13
If you didn't select to download the 64bit version, then you downloaded the 32bit one.
 
My guess is that you have 32bit. But check.

---

### Post by hibliss on 2009-08-13
or just 

```
uname -m
```

---

### Post by hibliss on 2009-08-13
> **pizza-is-good said:**
> If you didn't select to download the 64bit version, then you downloaded the 32bit one.
 
My guess is that you have 32bit. But check.

Not necessarily true. Wubi auto detects your architecture and if your processor is capable of running 64 bit version, thaty is what it gives you. The OP installed using WUBI.

---

### Post by rlhoman on 2009-08-13
Thanks everyone.  I assume i686 means I have the 32 bit version.

---

### Post by pizza-is-good on 2009-08-13
> **hibliss said:**
> Not necessarily true. Wubi auto detects your architecture and if your processor is capable of running 64 bit version, thaty is what it gives you. The OP installed using WUBI.
 
I didn't know that WUBI did that, interesting....

---

### Post by hibliss on 2009-08-13
> **pizza-is-good said:**
> I didn't know that WUBI did that, interesting....

I learned that the hard way when I tried Ubuntu for the first time.

---

### Post by bodhi.zazen on 2009-08-13
> **rlhoman said:**
> Thanks everyone.  I assume i686 means I have the 32 bit version.

yes, i686 = 32 bit.

---

