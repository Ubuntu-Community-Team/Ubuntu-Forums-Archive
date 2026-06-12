---
title: "Not able to understand linux directory paths from terminal"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by brawd on 2010-01-22
Hi there,

I've just started delving into Python and I'm falling at the first hurdle.

First I make up the program file, in this case print "hello world" and save it. It's saved at dad/brawd/hello.py

So now I start Terminal and then python. That seems to be fine because I get:

Python 2.5.2 (r252:60911, Jan 20 2010, 23:14:04) 
[GCC 4.2.4 (Ubuntu 4.2.4-1ubuntu3)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> 
 and can do things like 2 + 2 etc.

Now to run my very first program I tried - in Terminal - ~/brawd/hello as my path and get a syntax error. I've tried various versions of this but always get a syntax error.

SyntaxError: invalid syntax
>>> ~/dad/brawd/hello
  File "<stdin>", line 1
    ~/dad/brawd/hello
     ^
SyntaxError: invalid syntax
>>> 


It's obvious that I don't understand the path structures.

Can anyone give me a lead on this please.

regards,

brawd

---

### Post by doas777 on 2010-01-22
~ maps to the users home, so if the user is 'dad' then ~ => /home/dad

it is very possible that you will have to pass in $home instead of using a ~ though. not sure python will like that, unless you expand the variable with the os.path library

hth

---

### Post by earthpigg on 2010-01-22
can you show us the exact python script, and the exact command you are using to run it?

---

### Post by Hospadar on 2010-01-22
a quick note:

~luke maps to /home/luke
~/luke maps to /home/luke/luke

---

### Post by Mornedhel on 2010-01-22
The Python interpreter doesn't exactly work like this. I'm sure any Pythoneers around will know how to do it right, but running a file like this won't work.

Just run

```
python ~/dad/brawd/hello.py
```

assuming there's a folder named "dad" in your home directory, which contains a folder named brawd which contains a Python script named hello.py.

---

### Post by brawd on 2010-01-22
I tried a few variations on that theme, and tried again after your much appreciated reply, but no go.

All I ever get is syntax error.

I'm incompetent on this topic. I'm missing something crucial that everyone else in Linux world sees as bl***dy obvious. 

This is what I get for pwd.
/home/dad

So I type 
>>> brawd/hello

and get
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'brawd' is not defined

but brawd is there.

If I exit python I can change to the directory brawd and see hello.py.
Typing hello still does nothing.

If I try /home/dad/brawd/hello I get
>>> home/dad/brawd/hello
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'home' is not defined

Just now I'm frustrated, but I feel the doggedness building inside me.

I'm going to kill my mouse after this just to make my computer suffer like I am.

So the long and the short of it is that I'm still stuck.

brawd.

---

### Post by brawd on 2010-01-22
The python script was written in text editor in Accessories.

print "Hello World!"

---

### Post by pythonscript on 2010-01-22
Don't run those commands from within the python interpreter; run them from within the terminal (before you start python). So, click Applications -> Accessories -> Terminal, and run:

```
python ~/dad/brawd/hello.py
```That should work. The errors that you're getting are the result of python not knowing what the command means. For example, the command I wrote above only means something to the *linux shell*, not to the python interpreter, which only takes *python *commands.

---

### Post by Mornedhel on 2010-01-22
OK, here's a step by step, commented how to. Keep in mind I'm not a Python user. Lines beginning with $ are my shell input, lines beginning with # are my commentary. At no point do I use the Python *interactive* interpreter, because I'm not comfortable with it (as I said, I'm not a Python user).

```
$ pwd
/home/username
# create a simple Python script, end cat with Control+D
$ cat > blah.py
print "hello world"
^D
# create a folder in /home/username called "folder", move script there
$ mkdir folder
$ mv blah.py folder
# run the script
$ python folder/blah.py
hello world
# run the script from the script's folder
$ cd folder
$ python blah.py
hello world

```

You can use your favorite text editor or Python IDE to produce the script instead of my cat one-liner.

---

### Post by brawd on 2010-01-22
I put in the pwd command to try to help.

dad@dad-Ubuntu64:~$ pwd
/home/dad
dad@dad-Ubuntu64:~$ python ~/dad/brawd/hello.py
python: can't open file '/home/dad/dad/brawd/hello.py': [Errno 2] No such file or directory
dad@dad-Ubuntu64:~$

---

### Post by earthpigg on 2010-01-22
from a regular terminal:

cd /home/dad/brawd/
python hello.py

---

### Post by earthpigg on 2010-01-22
> **brawd said:**
> I put in the pwd command to try to help.

dad@dad-Ubuntu64:~$ pwd
/home/dad
dad@dad-Ubuntu64:~$ python ~/dad/brawd/hello.py
python: can't open file '/home/dad/dad/brawd/hello.py': [Errno 2] No such file or directory
dad@dad-Ubuntu64:~$

it would be:

python ~/brawd/hello.py
or
python /home/dad/brawd/hello.py

but not ~/dad/brawd/hello.py. that would be redundant.

whenever you see or type ~, it is exactly the same as typing /home/username/.... thats why the output says 'dad' twice.

---

### Post by Mornedhel on 2010-01-22
> **brawd said:**
> I put in the pwd command to try to help.

dad@dad-Ubuntu64:~$ pwd
/home/dad
dad@dad-Ubuntu64:~$ python ~/dad/brawd/hello.py
python: can't open file '/home/dad/dad/brawd/hello.py': [Errno 2] No such file or directory
dad@dad-Ubuntu64:~$

OK, now we know for sure that you're trying to go too deep in the hierarchy. As other posters have said, ~ alone stands for /home/dad in your case. ~dad also stands for /home/dad -- you can use it for other users, for instance ~joe would stand for /home/joe if there were such an user.

So what you're trying to do is probably "python ~/brawd/hello.py".

To further clarify, "your home folder" refers to "/home/dad", not just "/home". It's *yours*.

---

### Post by Chronon on 2010-01-22
> **brawd said:**
> I tried a few variations on that theme, and tried again after your much appreciated reply, but no go.

All I ever get is syntax error.

I'm incompetent on this topic. I'm missing something crucial that everyone else in Linux world sees as bl***dy obvious. 

This is what I get for pwd.
/home/dad

So I type 
>>> brawd/hello

and get
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'brawd' is not defined

but brawd is there.

If I exit python I can change to the directory brawd and see hello.py.
Typing hello still does nothing.

If I try /home/dad/brawd/hello I get
>>> home/dad/brawd/hello
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'home' is not defined

Just now I'm frustrated, but I feel the doggedness building inside me.

I'm going to kill my mouse after this just to make my computer suffer like I am.

So the long and the short of it is that I'm still stuck.

brawd.

You should just include
```
#! /usr/bin/python
```
as the first line of your [FONT="Courier New"]file.py[/FONT].  Then you can execute your code just by doing 
```
./file.py
``` from the directory containing file.py (or else use the absolute path to the file).  I find this to be the most convenient way to execute python.

It seems like you're still typing "python" instead of "python hello.py" as Mornedhel suggests.

---

### Post by brawd on 2010-01-22
Success!

dad@dad-Ubuntu64:~$ python ~/brawd/hello.py
Hello World!
dad@dad-Ubuntu64:~$ 


Thank you, thank you everyone.

regards,

brawd.

PS. I don't know how to mark this solved.

---

### Post by pythonscript on 2010-01-22
Click Thread Tools at the top of the thread and select Mark as Solved.

---

