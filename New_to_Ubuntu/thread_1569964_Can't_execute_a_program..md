---
title: "Can't execute a program."
date: 2010-09-07
forum: New to Ubuntu
---

### Post by shawnic on 2010-09-07
I got an ISO to CSO converter through the Ubuntu Software Center. At first, I couldn't find where it installed to. but once I found it, it doesn't do anything when I try to open it.
What am I doing wrong?

---

### Post by TeoBigusGeekus on 2010-09-07
Do you get any error messages when you try to open through terminal?

---

### Post by shawnic on 2010-09-07
I didnt try that, but once I did it just says:

Usage: ciso level infile outfile
  level: 1-9 compress ISO to CSO (1=fast/large - 9=small/slow
         0   decompress CSO to ISO

oh. thanks, I get it now.

EDIT:
how do I put the infile and outfile? do I put the filepath or what?

---

### Post by CharlesA on 2010-09-07
It should be this:

```
ciso level /path/to/infile /path/to/outfile
```

---

### Post by shawnic on 2010-09-07
Thanks so much. It seems so simple I feel foolish for asking.

---

