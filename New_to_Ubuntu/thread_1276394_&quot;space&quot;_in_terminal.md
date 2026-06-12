---
title: "&quot;space&quot; in terminal"
date: 2009-09-27
forum: New to Ubuntu
---

### Post by ajdrew06 on 2009-09-27
Hello... I feel silly having to ask this question.

I have a folder "My Stuff" in my /home/drew folder..

How do I access this folder via terminal?

I tried "cd /home/drew/My Stuff", but the terminal doesn't seem to like the space.

Any advice?  It has to be something beyond basic that I am overlooking.

---

### Post by MelDJ on 2009-09-27
try typing My_Space

---

### Post by KIAaze on 2009-09-27
You need to escape the space! ^^
Seriously, you need to add a so-called ["escape character"]("http://en.wikipedia.org/wiki/Escape_character"), which is usually "\":
```
cd /home/drew/My\ Stuff
```

Another solution is to add quotes:
```
cd "/home/drew/My Stuff"
```

---

### Post by erilidon on 2009-09-27
go to the drew directory and type
```
dir
```

more than likely it is ```
My\ Stuff
```

---

### Post by ajdrew06 on 2009-09-27
The backslash works fine.  Thank you.

---

### Post by ajdrew06 on 2009-09-27
> **MelDJ said:**
> try typing My_Space

The underscore doesn't work.

---

### Post by MelDJ on 2009-09-27
edit

---

