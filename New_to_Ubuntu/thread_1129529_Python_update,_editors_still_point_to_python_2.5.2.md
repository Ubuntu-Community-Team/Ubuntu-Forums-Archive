---
title: "Python update, editors still point to python 2.5.2"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by sanubie on 2009-04-18
I cannot get IDLE to install for Python3. I'm trying to start off with learning 3 because it just seems more logical. I installed and I can call the python 3 interpreter with the command 

```
joshua@Lattie:~$ python3
```
---
```
Python 3.0rc1+ (py3k, Oct 28 2008, 09:23:29) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
```

Thus I can run python programs by calling the interpreter and the name of the file.

python3 pyeXamp.py

That works fine. However, it becomes quite tedious after awhile. I have downloaded a number of text editors and ide's, but they all point to Python 2.5.2. So I cannot run my python3 programs with these ide's unless I figure out how to point them to the python3 interpreter in my usr/bin directory. I looked all over and I can't figure out an easier way to run python3 programs without using the terminal method. It just takes too long. I want to be able to click or push a button and my files runs through the interpreter. 

I suppose I could write a python program to automate some of the terminal typing. Like maybe it could just execute whatever .py file is in the current directory. That doesn't sound too hard to implement. But I'm looking for an easy way out, without having to write a program to help me write programs. Any ideas?

---

### Post by amingv on 2009-04-19
Just do

```
sudo aptitude install idle3
```

Then open IDLE 3 from the menu, you get this:

```
Python 3.0.1+ (r301:69556, Apr 15 2009, 15:59:22) 
[GCC 4.3.3] on linux2
Type "copyright", "credits" or "license()" for more information.
==== No Subprocess ====
>>> print "Hello"
SyntaxError: invalid syntax (<pyshell#0>, line 1)
>>> print("Hello")
Hello
```

But honestly, learning python3.0 first makes no sense to me. Sure, it's ok to check it out after you have a general gist of the current version to stay up-to-date, but if you're learning the language from scratch I suggest you stick with 2.6. (Just my opinion, of course).

---

### Post by sanubie on 2009-04-19
Yea, but the same question applies. Even if I just want to stick with 2.6 everything still points to python 2.5.2. I don't even see Python 2.6 in the depositories. 

Two questions: How to I obtain python 2.6, and then how do I use IDLE and other ide's with the latest 2 edition (2.6)? Right now I have IDLE for 2.5.2 and all the ide's I have use 2.5.2 by default. I'd much prefer 2.6 anyway because I have 4 books on it already.

---

### Post by amingv on 2009-04-19
It was updated by itself when I updated to jaunty (hadn't updated in a while, so I'm not sure if it's a jaunty update or just an accumulated update, though I'd put my money on the former), but you should have no problem running those exercises even in 2.5.

EDIT:
Yup, confirmed:
[http://packages.ubuntu.com/jaunty/python2.6](http://packages.ubuntu.com/jaunty/python2.6)

You can install python3.0 and yet not 2.6? Sounds messed up...

---

