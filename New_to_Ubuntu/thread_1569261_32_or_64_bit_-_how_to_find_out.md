---
title: "32 or 64 bit - how to find out?"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by adolfo158 on 2010-09-06
I tried downloading Chrome for x64 but the install complained I had the wrorng version. I have lucid Linx on a Athlon 64 machine. How do I check  if I have the 32 or 64 bit version?

Appreciating your help

Adolfo
[email]aguirre.adolfo@gmail.com[/email]

---

### Post by louis--taylor on 2010-09-06
try:
```

uname -a
```

in a terminal

---

### Post by Windows Nerd on 2010-09-06
> **adolfo158 said:**
> I tried downloading Chrome for x64 but the install complained I had the wrorng version. I have lucid Linx on a Athlon 64 machine. How do I check  if I have the 32 or 64 bit version?

Appreciating your help

Adolfo
[email]aguirre.adolfo@gmail.com[/email]

```
uname -a
```

This should be moved to Beginners help.

---

### Post by Joeb454 on 2010-09-06
*Thread moved to **Absolute Beginner Talk**.*

I usually go with ```
uname -m
``` to find this out.

For example, my 64 bit system returns **x86_64**, however I imagine most 32 bit systems would return **i686**

---

### Post by TNT1 on 2010-09-06
> **Joeb454 said:**
> *Thread moved to **Absolute Beginner Talk**.*

I usually go with ```
uname -m
``` to find this out.
  most 32 bit systems would return **i686**

Mine does, but I have a 64bit cpu, and enough RAM to make it worthwhile, I'm just happy with PAE support for now.

---

