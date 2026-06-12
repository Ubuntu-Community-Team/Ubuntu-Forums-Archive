---
title: "How Do I Start Programming in Python?"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Martin Marshalek on 2009-02-22
I posted a thread to help me choose the programming language for a simple game I  want to make for a project in a month. Thanks to those who posted, I learned that Python with the Pygame libraries would be the easiest and best for my needs. However, now I'm confused, how to I write my code? Do I need a special program or can I use Gedit for this?

Also, when I go to download programs, I find downloadable source codes that can be compiled with a simple command for your native OS (Widows or Linux). How do I code my game so I end up with a source code so I can code it for Linux and test it in Linux, but use it a school under Windows? Is that possible (without wine since I dual boot)?

---

### Post by karlr42 on 2009-02-22
Python is an interpreted language. so assuming it's installed on the Windows machine, just take the source code(which, yes, you write in any editor you like, it's just text afterall), then run it with that machine's Python installation.

---

### Post by Armor Nick on 2009-02-22
check pygame.org and python.org for tutorials. They're pretty good. You can program with any text editor, but to make it easier, try to find a formatting option and set it to python.

there's a program called py2exe which bundles all your files and the python runtime into an executable file which you can use under windows. Under linux, python is installed by default.

---

### Post by Martin Marshalek on 2009-02-22
So I need to have a Python interpreter installed in Windows?

Edit:I saw your post Nick, thanks for the py2exe. I have to use this on the school computers so I won't be able to install many programs to get just one game to work. Also, how do I enable the pygame libraries?

---

### Post by freak42 on 2009-02-22
there are excellent documentations and tutorials for python: 
[http://python.org/doc/](http://python.org/doc/)

python is an interpreted language (not compiled) with working interpreters on a multitude of os's. So basically your python code should work on any python-supported os. (Testing is key!)

hth

---

### Post by Martin Marshalek on 2009-02-22
I just found that Python is already in version 3 but Ubuntu has only 2.5 installed, how do I update?

---

### Post by karlr42 on 2009-02-22
You'll prob have to use py2exe then, if you can't install a python intepreter AND there's not one already installed.

---

### Post by linux_tech on 2009-02-22
Try writing a few simple scripts to get used to python

---

### Post by Barriehie on 2009-02-22
I use DrPython, mostly, for my editor.  Sometimes Gedit.  DrPython is in the repos'.

Barrie

---

### Post by MrWES on 2009-02-22
You can set the highlight mode on Gedit to Python.

Bill

---

### Post by snova on 2009-02-22
> **Martin Marshalek said:**
> I just found that Python is already in version 3 but Ubuntu has only 2.5 installed, how do I update?

You don't, at least, not exactly. Py3K is incompatible with the 2.x series, so you cannot replace one with the other. You can, however, install them side-by-side. Simply install the **python3** package.

'python' will continue to invoke the 2.5 interpreter, and this should not be changed (it could potentially break something in your system). Run the 3.0 interpreter with 'python3'.

---

### Post by raydeen on 2009-02-22
Python 2.x is still pretty much the standard. I wouldn't worry too much about 3 just yet. I did read somewhere that there will be some sort of program that will auto-translate the old 2.x code to 3 when the time comes to upgrade it.

---

### Post by snova on 2009-02-22
> **raydeen said:**
> Python 2.x is still pretty much the standard. I wouldn't worry too much about 3 just yet.

True. And you'd probably be better off using 2.x for now, as a lot of libraries have not been ported yet (few, if any). I, for one, would like PyQt4 and Twisted!

> I did read somewhere that there will be some sort of program that will auto-translate the old 2.x code to 3 when the time comes to upgrade it.

There is (2to3), and it seems to work quite well, but I don't think it should be relied on.

---

### Post by raydeen on 2009-02-22
For the OP, I'm beginning to learn Python myself. Depending on how experienced you are with programming in general, I'd like to recommend the following e-books: (they're pretty basic stuff but I'm not embarrassed. Gotta start somewhere. ;) )

[http://www.briggs.net.nz/log/writing/snake-wrangling-for-kids/](http://www.briggs.net.nz/log/writing/snake-wrangling-for-kids/)

[http://pythonbook.coffeeghost.net/book1/](http://pythonbook.coffeeghost.net/book1/)

I also purchased Beginning Python from novice to professional

[http://www.amazon.com/Beginning-Python-Novice-Professional-Second/dp/1590599829/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1235337781&sr=8-1](http://www.amazon.com/Beginning-Python-Novice-Professional-Second/dp/1590599829/ref=pd_bbs_sr_1?ie=UTF8&s=books&qid=1235337781&sr=8-1)

It covers just about everything including some Python 3 in that it shows what functions and syntax will eventually replace what's in Python 2.x. I bought it but have turned to the ebooks for right now as they're good for those first baby steps. As an example, the second ebook as a good 'Hangman' game in it that shows how dictionaries are used which was a concept I was having trouble understanding in the big book. As a result of the ebooks, I was able to write a flashcards program that my daughter could drill with for her math.

Good luck to you.

---

### Post by simeon87 on 2009-02-22
When you have questions, there's always [this subforum](http://ubuntuforums.org/forumdisplay.php?f=39) ;)

---

### Post by Martin Marshalek on 2009-02-22
Thanks everyone for the suggestions. I downloaded the ebooks and will teach myself from those. I've decided on gedit and will enable the pygame package. I'll keep the thread open in case there are people who need help in the same field.

---

### Post by MrWES on 2009-02-23
+1 on those web sites. Like you said, basic information, but you have to start somewhere.

Thanks,
Bill

---

