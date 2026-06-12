---
title: "Does Ubuntu come with Perl, Python, or REXX?"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by deleyd on 2009-08-19
Does Ubuntu come with Perl, Python, or REXX?

How does Ubuntu identify a file to be a Perl script, Python script, or REXX script?

May I have a simple "Hello World" example file, and how to launch it?

---

### Post by alexlafreniere on 2009-08-19
Yes, Ubuntu comes with Python and Perl. A good percentage of Ubuntu's desktop application are written in, or are extended by, Python script, and Perl is a mainstay of Linux scripting and text manipulation for system administrators. I have never heard of REXX script, however, so I am not much help there. As for simple scripting in Python and Perl, you just write your script in a text editor, save it as a script and run it from the terminal. Any good Python or Perl tutorial will include information on how to do this, try any O'Reilly book on the subject, they are considered very good guides on how to learn those languages.

---

### Post by ibuclaw on 2009-08-19
Perl - hello.pl
[PHP]
#!/usr/bin/perl
use strict;
use warnings;

print "Hello World!\n";
[/PHP]

To run the application:
```
chmod +x hello.pl
./hello.pl
```
Where "hello.pl" is the filename you've saved it as.



As for other languages.

Python - hello.py
I **think** it is:
[PHP]#!/usr/bin/python
print "Hello World!\n";[/PHP]

I'm not familiar with REXX, but you initialise it in the same way. :)

edit:
To install REXX:
```
sudo apt-get install regina-rexx
```
REXX - hello.rexx
[PHP]#!/usr/bin/rexx
Say "Hello World!"[/PHP]

Regards
Iain

---

### Post by Bodsda on 2009-08-19
> **tinivole said:**
> 

Python - hello.py
I **think** it is:
[PHP]#!/usr/bin/python
print "Hello World!\n";[/PHP]


How dare you end a python print statement with a colon! :) 
[php]
#! /usr/bin/env python
print "Hello World!"
[/php]

or if you want py3k the print is a function, so enclose in brackets like this
[php]
print ("Hello World!")
[/php]

Kind regards,
Bodsda

p.s: It does still work with a colon, I have just never seen it written or suggested to use it.

---

### Post by Mighty_Joe on 2009-08-20
REXX?  Is there an old OS/2 fan in the house?  I loved stem variables. 
Python is my second-favorite language right now (I'm a professional Java dev). If you're interested, [Think Python]("http://www.greenteapress.com/thinkpython/thinkpython.html") is a great (and free!) introduction.

---

### Post by oldrocker99 on 2009-08-20
REXX was on the Amiga (remember them?) as a variety called ARexx. It was such a good scripting language that it was bought by Commode-or and made part of the OS.

I missed my Amiga until I started using Ubuntu.

:guitar:

---

