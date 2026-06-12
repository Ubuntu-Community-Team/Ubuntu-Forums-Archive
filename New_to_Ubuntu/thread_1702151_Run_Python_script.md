---
title: "Run Python script"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by hdanap on 2011-03-07
Hi Everyone,

Pls can any one tell me what is wrong with this script?

why its not working


#!/usr/bin/env python

import time

def absolute_value(x):
      if x < 0:
                   return -x
          return x

num=input("Please enter a number: ")    
    
absolute_value(num)

time.sleep(5)

The script stops at "num=input("Please enter a number: ")    " when it is passed to function call. nothing happens it only sleeps then end after 5sec

Thanks

---

### Post by turtle153 on 2011-03-07
Use```
print(absolute_value(num))
```to put the number into the terminal.

---

### Post by hdanap on 2011-03-07
Sweet, sweet.
Thanks bro

---

