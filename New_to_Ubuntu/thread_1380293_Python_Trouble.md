---
title: "Python Trouble ?"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by MrAnsell on 2010-01-13
Hello i am just learning the basics of python and i have a problem running a small simple prgram i have written here is what happens in terminal :   
admin2@admin2-laptop:~$ cd Documents
admin2@admin2-laptop:~/Documents$ chmod +x heloo.py
admin2@admin2-laptop:~/Documents$ ./heloo.py
./heloo.py: line 1: syntax error near unexpected token `('
./heloo.py: line 1: `x=raw_input ("enter name: ")'
admin2@admin2-laptop:~/Documents$ 

Here is the code :

 x=raw_input ("enter name: ")
print "helo " + x
raw_input("press<enter>")

Is there something i am doing wrong ? thanks

---

### Post by da burger on 2010-01-13
If that is the whole code you have not told ubuntu to run your script in python. It is trying to run the script with bash.

Either run:```
python heloo.py
```

or add to the beginning of the script: ```
#! /usr/bin/python
```

---

