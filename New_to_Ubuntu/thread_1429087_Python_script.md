---
title: "Python script"
date: 2010-03-13
forum: New to Ubuntu
---

### Post by ScottinSoCal on 2010-03-13
I got myself a Sony Touch ebook reader this morning, and am now trying to run a program to convert the pdb file I purchased and downloaded from Barnes & Noble to a format that my Sony reader can work with. I downloaded and installed an application called Calibre, and it'll probably work great, but I have to do something else first. I have a python script that is reported to be able to help me with the something else, but I can't get the script to run. I downloaded IDLE and installed it to create the script. I set the executable flag on the file. When I try to just run the script I get errors.

```
user@computer:~$ ls
Books    Desktop    examples.desktop  My BN eBooks  runthis.py  ttfonts
Calibre  Documents  Firefox backup    Pictures      Storage     Videos
dell     Downloads  Music             Public        Templates

user@computer:~$ runthis.py
runthis.py: command not found

user@computer:~$ python runthis.py
  File "runthis.py", line 1
    Python 2.6.4 (r264:75706, Dec  7 2009, 18:45:15) 
             ^
SyntaxError: invalid syntax

user@computer:~$ 

```

Can anyone help?

---

### Post by lavinog on 2010-03-13
add a # in front of that line:
```

#Python 2.6.4 (r264:75706, Dec  7 2009, 18:45:15)

```

It wasn't part of the script I am assuming.

For future reference there is a programming section for these type of questions, and it helps to post your script so we can see what is wrong.

---

### Post by Method X on 2010-03-13
Hello
I'm not shure, but maybe you get error because of python's version.
Pay attention to it.

---

