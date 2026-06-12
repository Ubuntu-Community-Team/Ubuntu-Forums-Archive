---
title: "libc version?"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by DCanucks on 2010-09-30
How would I find out the version of my libc using the terminal. Explanations would be great, I'm fairly new to Linux and want to learn.

Thanks
-Dave

---

### Post by andrewthomas on 2010-09-30
```
 
aptitude show libc6

```

---

### Post by DCanucks on 2010-09-30
It does work with installed programs. But I get this in the terminal for libc...
E: Unable to locate package libc

---

### Post by andrewthomas on 2010-09-30
There is no package named libc

---

### Post by DCanucks on 2010-09-30
It's obvious there is no package... that is what the message says.

But when typing in whereis libc, I do get hits... so I'm assuming I have it somewhere. When I do apropos libc, I get listed gnu_get_libc_version... is there a way to access/use that?

[FONT=&quot][/FONT]

---

### Post by Bachstelze on 2010-09-30
The package is libc6.

---

### Post by DCanucks on 2010-09-30
Hey Bachstelze, thanks for clarifying, I missed that. Just have a question, where'd the 6 come from exactly?  I was just asked to find the version of libc, how'd you guys know to use libc6?

---

