---
title: "Programming applications for Ubuntu"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by mag1strate on 2008-12-07
Hey guys, I want to start learning how to program, are there any open source applications I can get to start, If you know any books that might help me learn that would be great!:KS

---

### Post by jamesrl on 2008-12-07
I'd suggest learning emacs as an editor, and try python as a first language but use ipython for better interactive mode.  A good tutorial is located at [http://docs.python.org/tutorial/](http://docs.python.org/tutorial/)

---

### Post by genus_001 on 2008-12-07
gcc and g++ are what I recommend, they are the free versions of c and c++.  Python is a really good one to start with because it has a good interactive help program, and the documentation is really really good.
It also depends on what you plan to do with programming.  If you want to do some good old fashioned hacking, I'd say start with c or c++(gcc and g++). But python is a little easier to understand, and you can whip out some pretty simple programs, really quick.

---

### Post by Bölvaður on 2008-12-07
I do not suggest you to start playing with Java like most schools teach as first programming language. But if you are going to do that, get Eclipse, it might be strange but it corrects your mistakes ;)

There are also simpler languages to learn like scheme that is interesting (but perhaps not the most useful language there is)

---

### Post by jamesrl on 2008-12-07
I guess you need to clarify why you are trying to learn to program.  If you have some ideas you want to program efficiently and quickly with a quick learning curve, I'd suggest python.  Its powerful and fast and has tons of modules written to do nearly anything you want to do, and is object-oriented (but you don't have to put everything into classes unlike say java).  By being very high-level you spend less time debugging silly things like forgotten braces or semi-colons or type-mismatching or memory management or worry about memory leaks or programs crashing from pointing to meaningless memory locations.  It also forces good, consistent spacing habits which makes the code easier to read (and spotting incorrect indentation (when using a good editor), is simpler than counting nested levels of parentheses).

If you want to become a computer scientist or programmer, I'd learn a good object orientated language like java and ultimately learn C++.  You can find countless tutorials in all these languages.  Languages such as C++ make you keep track of a lot more things as you program, which ultimately is good if you do it right (e.g., in general if done optimally a C++ program will work faster than a python program), and have a deeper  understanding of what truly is going on (allocating/freeing memory from the heap, performing type checks yourself, etc.)

I wouldn't suggest learning C, personally I learned many bad habits programming in C that took me time to unlearn in programming in C++ (e.g., C doesn't support object-oriented programming, or generic programming, so the way you learn to think to program doesn't involve things like encapsulation, polymorphism, inheritance, exception handling, etc.).   When you write a C++ based on C-type algorithms, you miss the benefit of being able to access the fancy C++ features.

I should note that when speed is really necessary and the high-level nature of python slow you down, you can get ~99% of the efficiency of the C++ program, by having the complex parts actually run as C++ code through say [boost.python]("http://www.boost.org/doc/libs/1_37_0/libs/python/doc/tutorial/doc/html/python/exposing.html").  And python already has many modules written that have the C++ side of things already written, to give you the execution speed of C++ without the hassle.

---

### Post by anewguy on 2008-12-07
Indeed, with C you can learn some things that are hard to "unlearn" when you move to an object oriented language.  You will see Python mentioned a lot, and since I have no knowledge of it I can't offer any advice on it.  Personally, and this is just my opinion, if you just want to learn to program, pick an "easy" language first".  If you really want to be productive, then take the plunge and go for C++ and use GTK for building your GUI's.  Why?  Well, I know there are other languages such as Java and it's GUI which are transportable to other operating systems, but I have found it relatively easy to program something in C or C++ with GTK in Linux and then port it to Windows.  Yes, the Windows system will need GTK for Windows installed, and if you want to compile on the Windows machine you will probably need something along the lines of Mingw or another such tool that offers gcc for Windows.

Again, just my opinion - there are many others as well.  It begins with knowing just what you want to do - that can make a difference in which language to pick to learn.

Hope that helps a little.

Dave ;)

---

### Post by cheetaux on 2008-12-07
There are several very good C++ (Thinking in C++) and Java (Thinking in Java) books written by Bruce Eckel that are available for free online at his website:

[http://www.mindview.net/Books]("http://www.mindview.net/Books")

I learned a lot from both of these books and highly recommend them.

---

