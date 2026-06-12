---
title: "Stupid python question"
date: 2010-02-24
forum: New to Ubuntu
---

### Post by semisquirrel on 2010-02-24
I know this will sound about as stupid as can be, but how the heck do I run Python???

I should first admit that, although I have been using computers for 20 years, I have done nothing in the way of programming, ever.

I got Python pre-installed on Karmic, and decided to try it out, largely because I can.

I found this:  [http://wiki.python.org/moin/SimplePrograms](http://wiki.python.org/moin/SimplePrograms)

Then, I tried to find Python in my applications.  No such luck.

So what do I actually open to type in the commands?

Thank you for your help!

---

### Post by Temposs on 2010-02-24
Do Applications->Accessories->Text Editor and write your commands in there. Save the file with a .py extension.

Then, open Applications->Accessories->Terminal and type:

```
python yourcodefile.py
```

where yourcodefile.py is the name of your python code file.

Alternatively, you can open the terminal and just type

```
python
```

Then, it brings up the interactive mode in which you can type python commands. This method is easier for running quick throwaway code, since it doesn't get saved.

---

### Post by undecim on 2010-02-24
In addition to what Temposs said, there is also a tool called idle available in the repositories that is much easier to work with when creating new programs or just playing around with the python prompt

---

### Post by semisquirrel on 2010-02-24
Thanks!  That worked!

This stuff is fun, kids!  Wow!

---

### Post by The Cog on 2010-02-24
I would like to recommend **geany** as an editor. It does syntax highlighting, and has a list of your functions/classes/methods in a pane on the left. It also has a "compile" button that does syntax checking without actually running the program, which I sometimes find useful. And a Run button of course.

---

### Post by doublewitt on 2010-08-04
another stupid question...!
ofcourse just starting with python...

after reading in a tutorial, again, this is very "beginner" stuff... but, when opening the terminal and typing python3, it says enter the following after the python prompt:

print "Hello world!"

however, I get a syntax error message... why would I get that for something so simple...?!

Here is what I see in the terminal:

[COLOR="Blue"]Python 3.1.2 (r312:79147, Apr 15 2010, 12:35:07) 
[GCC 4.4.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print "Hello world!"
  File "<stdin>", line 1
    print "Hello world!"
                       ^
SyntaxError: invalid syntax
>>> [/COLOR]

I really want to learn this...!

---

### Post by Temposs on 2010-08-05
python 3 does not support that syntax with the print statement. You should use this:

print("Hellow world!")

---

### Post by doublewitt on 2010-08-05
Thanks,
that's correct...!
well, off to some *studying*... ;)

---

