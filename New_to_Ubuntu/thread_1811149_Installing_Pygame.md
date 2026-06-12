---
title: "Installing Pygame"
date: 2011-07-24
forum: New to Ubuntu
---

### Post by Pyprokid on 2011-07-24
Hello! :D

I am new to Ubuntu -- just installed it yesterday, and I am new to all these concepts... I was wondering how to install Pygame? On the official website when I click the link it says bad URL :confused: 

If it helps, I am using the newest version, I thought it was 11.04?

Any help is GREATLY appreciated. 

- Matt

---

### Post by Pyprokid on 2011-07-24
:popcorn:

---

### Post by realzippy on 2011-07-24
Welcome to UF !
You mean python-pygame ?
Open *synaptic* or *software-center*,search for
python-pygame and install it.
Or open a terminal,paste in:

```
sudo apt-get install python-pygame
```

and you are done.
BTW,please wait 24 hours before bumping your thread.

---

### Post by Pyprokid on 2011-07-24
Thank you so much! :D
And the bumping rule noted ;)

---

### Post by realzippy on 2011-07-24
So you can mark your thread as "solved" (Threadtools)...have fun !

---

### Post by EriktheAwful on 2012-05-06
I've been working my way through Al Sweigart's [Invent Your Own Computer Games with Python](inventwithpython.com) book. I've been trying to relearn programming - I got interested in cars when I was a teenager and never moved past BasicA. The book is amazing!

Now I'm to Chapter 17, where pygame is introduced, so I installed pygame with the Synaptic Package Manager. Then I inputted and saved the gui 'Hello world' program. I hit F5 and got:```
Python 3.2.2 (default, Sep  5 2011, 21:17:14) 
[GCC 4.6.1] on linux2
Type "copyright", "credits" or "license()" for more information.
==== No Subprocess ====
>>> 
Traceback (most recent call last):
  File "/home/erik/Python/pygame Hello World.py", line 1, in <module>
    import pygame, sys
ImportError: No module named pygame
>>> 
```I completely removed pygame and used terminal to sudo apt-get install it. Same thing. What am I doing wrong? Everything I've seen shows that pygame is compatible with Python3, including 3.2.2.

---

### Post by EriktheAwful on 2012-05-06
Never mind! [Found this.](pythonfun.wordpress.com/2011/08/08/installing-pygame-with-python-3-2-on-ubuntu-11-04/) Works now.

---

### Post by llamabr on 2012-05-06
Please don't dig up year old threads.  Start a new one if you have something important to add.

---

