---
title: "Convert  ISO"
date: 2011-04-04
forum: New to Ubuntu
---

### Post by bj218 on 2011-04-04
Is there a program to convert a Linux ISO to a CD that will allow me to control the conversion speed?

---

### Post by bodhi.zazen on 2011-04-04
There are several, I have always preferred K3b

---

### Post by fela on 2011-04-04
If you're on windows, check out imgburn.

If you're on Ubuntu, right click the file and choose 'write to disc'.

---

### Post by dnairb on 2011-04-04
> **fela said:**
> If you're on Ubuntu, right click the file and choose 'write to disc'.

There is very little control on the write-speed with this method.

---

### Post by fela on 2011-04-04
OK, open up a terminal, cd to the directory of the ISO file, and type:

```
wodim speed=8 filename.iso
```

Where 8 is the speed you want, and filename.iso is the name of the file you want to burn.

It might just be that your drive has limited hardware control options.

---

