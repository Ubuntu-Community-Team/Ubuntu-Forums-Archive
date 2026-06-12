---
title: "How do I find the 'path'"
date: 2010-11-04
forum: New to Ubuntu
---

### Post by DayLite on 2010-11-04
How do I find the complete path to a program. Looking at the properties doesn't tell me.

---

### Post by jwalling on 2010-11-04
This might help you
[https://wiki.ubuntu.com/Bugs/FindRightPackage](https://wiki.ubuntu.com/Bugs/FindRightPackage)
go to **Determining the Executable Path** section

If the executable is not in the menu sytem, follow the instructions for using "xprop WM_CLASS"

Cheers

---

### Post by sully101 on 2010-11-04
> **DayLite said:**
> How do I find the complete path to a program. Looking at the properties doesn't tell me.

From a terminal type

which nameofprogram

eg.

$ which wget
/usr/bin/wget

---

### Post by sikander3786 on 2010-11-04
whreis command will be better.

```
whereis wget
```

locate is another powerful command. It will search all the files containing wget

```
locate wget
```

---

### Post by DayLite on 2010-11-04
> **sikander3786 said:**
> whreis command will be better.

```
whereis wget
```locate is another powerful command. It will search all the files containing wget

```
locate wget
```

thank you.

---

