---
title: "Trouble with Python 'for' loop."
date: 2009-02-24
forum: New to Ubuntu
---

### Post by addowannapeea on 2009-02-24
I'm trying to make a program in python that will compute a list of 4-digit numbers in which the 4 digits multiply out to 120. my attempt looks a bit like:

def num_count(a,b,c,d):
    for a in range(1,10):
        for b in range(1,10):
            for c in range(1,10):
                for d in range(1,10):
                    if a*b*c*d==120:
                        print "%d,%d,%d,%d" % (a,b,c,d)
            
num_count(a,b,c,d)


(ignore lack of indentation)

the error i'm getting says:

File "numbercount.py", line 11, in <module>
    num_count(a,b,c,d)
NameError: name 'a' is not defined


Any help would be much appreciated.

---

### Post by Captain_tux on 2009-02-24
You should post this in the Programming forum... it's hardly a beginner topic.

Oh, and sorry that I cant help!

---

### Post by addowannapeea on 2009-02-25
dun n dun.

---

### Post by The Cog on 2009-02-25
You don't need to pass a,b,c and d into the num_count function. If you lkk again, you will see that num_count ignores the passed-in values anyway.

What's more, a, b, c and d don't even exist outside the num_count function which is why you get an exception when you try and pass them into num_count. Try:
```

def num_count():
    for a in range(1,10):
        for b in range(1,10):
            for c in range(1,10):
                for d in range(1,10):
                    if a*b*c*d==120:
                        print "%d,%d,%d,%d" % (a,b,c,d)

num_count()

```

---

