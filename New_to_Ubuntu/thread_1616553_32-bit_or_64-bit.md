---
title: "32-bit or 64-bit?"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by col48 on 2010-11-08
I know I'm using a 32-bit system, but someone else has asked me what their Ubuntu is. How do I ask the system whether it is 32-bit or 64-bit?

---

### Post by howefield on 2010-11-08
Have a look at the output of the terminal command

```
uname -a
```

If it has x86_64 somewhere in the output, it is 64 bit, otherwise it is 32 bit.

---

### Post by col48 on 2010-11-08
Brilliant.  Thanks.

---

### Post by yiannis66 on 2010-11-08
install the hardinfo from synaptic and run it ```
 hardinfo
```
with this you will have lots of others informations

---

### Post by natravis on 2010-11-08
> **howefield said:**
> Have a look at the output of the terminal command

```
uname -a
```

If it has x86_64 somewhere in the output, it is 64 bit, otherwise it is 32 bit.

+1 to using tools already available to the system

---

### Post by WRDN on 2010-11-08
To be precise, "**uname -m**" lists the "machine hardware name" (architecture).

---

