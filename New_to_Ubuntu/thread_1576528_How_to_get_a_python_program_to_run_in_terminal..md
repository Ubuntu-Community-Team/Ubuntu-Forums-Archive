---
title: "How to get a python program to run in terminal."
date: 2010-09-17
forum: New to Ubuntu
---

### Post by poodoopealeoaph on 2010-09-17
I'm very new with the idea of programming and I am trying to go through some tutorials to figure it out. I have the code written in IDLE exactly how it is in the tutorial but for some reason it won't execute in the terminal. I've tried "sudo chmod +x file.py" then "./file.py" and I've tried "python file.py". I get a syntax error after each try and it wont' execute. here is the code in terminal.



adam@adam-laptop:~$ ls
Desktop    Downloads         Music     Templates                  Videos
dive.py    examples.desktop  Pictures  variables demonstrated.py
Documents  mary.py           Public    variablesdemonstrated.py
adam@adam-laptop:~$ sudo chmod +x dive.py
[sudo] password for adam: 
adam@adam-laptop:~$ ./dive.py
./dive.py: line 1: syntax error near unexpected token `('
./dive.py: line 1: `Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) '
adam@adam-laptop:~$ python dive.py
  File "dive.py", line 1
    Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56) 
             ^
SyntaxError: invalid syntax



I'm lost and would really appreciate some help on the issue. by the way, i feel pretty dumb because I'm about to start programming in college in about 3 months and I have no idea what I'm doing. lol:popcorn:

---

### Post by dv3500ea on 2010-09-17
Could you show us the whole contents of this file? 'Python 2.6.5 (r265:79063, Apr 16 2010, 13:09:56)' does not look like part of a python program. Try adding a '#' to the beginning of the line with this text in it (to make it ignored by python).

To enable the program to be run by ./dive.py, add this to the start of the file:
```

#!/usr/bin/env python

```

Please use the Programming Talk sub-forum to post programming related questions in the future. Also, wrap your code in CODE tags. You don't need to categorise your question as [lubuntu] if it is general like this.

---

### Post by poodoopealeoaph on 2010-09-17
Here's the code that is written in python. 

def approximate_size(size, a_kilobyte_is_1024_bytes=True):
    '''Convert a file size to human-readable form.

    Keyword arguments:
    size -- file size in bytes
    a_kilobyte_is_1024_bytes -- if True (default), use multiples of 1024
                                if False, use multiples of 1000

    Returns: string

    '''
    if size < 0:
        raise ValueError('number must be non-negative')

    multiple = 1024 if a_kilobyte_is_1024_bytes else 1000
    for suffix in SUFFIXES[multiple]:
        size /= multiple
        if size < multiple:
            return '{0:.1f} {1}'.format(size, suffix)

    raise ValueError('number too large')

if __name__ == '__main__':
    print(approximate_size(1000000000000, False))
    print(approximate_size(1000000000000))


Using the code to ignore python didn't do anything. it's just giving me an invalid command prompt in the terminal.

---

### Post by tgm4883 on 2010-09-17
Please use code brackets when posting code.

---

### Post by dv3500ea on 2010-09-17
You need to replace the ```
'''
``` quotes with ```
"""
```.
Also, the code needs to be indented properly, otherwise it doesn't make any sense; even to a human. The python interpreter can't tell what code is part of an if and what code is part of a for and neither can I.
```

for x in y:
    # some code
    if expression:
        #some code 

```
is different to
```

for x in y:
    #some code
if expression:
    #some code

```
and
```

for x in y:
#some code
if expression:
#some code

```
is meaningless.

---

### Post by poodoopealeoaph on 2010-09-17
ok, thanks for the help guys. I just ran in terminal with the "python file.py" and debugged the coding issues. It works fine for me now. Thanks for bearing with me. Also, just to know for the future, how do you make those code boxes on your posts?

---

### Post by scorchgeek on 2010-09-17
The little hash mark in the editor will insert the required "[ CODE]""[ /CODE]" brackets, which you type between, or you can type them yourself. (The spaces are so they didn't get expanded and are not actually used.)

---

