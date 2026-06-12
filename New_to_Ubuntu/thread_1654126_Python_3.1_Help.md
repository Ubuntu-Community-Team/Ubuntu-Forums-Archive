---
title: "Python 3.1 Help"
date: 2010-12-27
forum: New to Ubuntu
---

### Post by Akoscura on 2010-12-27
I'm new to python, and can only seem to input strings, not numerical values, when using the input function.
ex:[INDENT]x=input()
[/INDENT]and then when I input a number, it automatically converts it to a string...

---

### Post by Cheesehead on 2010-12-28
That's right.

To make it an integer, 

x=int(input())

Or, since you might want to check for bad input:

```
def get_integer_input(label):
    try:
        return int(input(label))
    except:
        return False

a = False
while not a:
    a = get_integer_input("Gimme a number:")
print('Your number is %s' % a)
```

---

