---
title: "Save Terminal Input?"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by ConradSL on 2009-08-06
Hey,

So I'm learning how to program in python and I was wondering if there was a way to store my input in console to like a document? That way when I'm slowly writing out scripts and write something I like, I can just copy the code I like from this 'document' and make it into a .py file.

Thanks,
Stu

---

### Post by nothingspecial on 2009-08-06
Use nano

```
nano my_python_program.py
```

Ctrl+O to save
Ctrl+X to exit

---

### Post by CatKiller on 2009-08-06
Every command that you enter into a Terminal is already saved, in .bash_history (so that you can easily use them again). I don't think it holds things indefinitely, but it does hold a lot of commands.

---

### Post by ConradSL on 2009-08-06
Ah thanks, but, bash_history doesn't save stuff while I'm in 'python mode', like:

Terminal
```

conrad@Conrad:~$ echo Hello
Hello
conrad@Conrad:~$ python
Python 2.6.2 (release26-maint, Apr 19 2009, 01:56:41) 
[GCC 4.3.3] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> print "Hello world!"
Hello world!
>>> 
conrad@Conrad:~$ echo Done
Done

```Will get me this in bash_history:

bash_history.txt
```

echo Hello
python
echo Done

```And I'm really just interested in what I typed in during the python session.

Thanks for bash_history though, didn't know about that,
Stu

---

### Post by Wim Sturkenboom on 2009-08-06
Why not directly write python files? Start your file with something like
```

#! /usr/bin/python

```
Next make it executable and you can run it straight away.

You can find the path to python with the command
```

root@btd-techweb01:/etc/X11# **which python**
/usr/bin/python

```

---

### Post by ConradSL on 2009-08-06
Yea, I do that sometimes, it's just, I was wondering if there was a way to do both at the same time.
I'm guessing it's more trouble than it's worth though.

---

### Post by credobyte on 2009-08-06
```
user@ubuntu:/etc# python

```

Upon executing, you are no longer working with bash - it's a Python interpreter. As previously said, write your code into python files ( <file.py> ) ;)

---

### Post by ConradSL on 2009-08-06
kk, I guess I'll just do that, thanks the help everyone.

---

### Post by The Cog on 2009-08-06
> **ConradSL said:**
> kk, I guess I'll just do that, thanks the help everyone.

You can copy/paste from the terminal into a text file of course, provided your input hasn't scrolled off the top so the scrollbar can't reach it.

Beyond the very simplest things, you soon get tired of re-typing a lot of stuff over and over. It soom gets less tiresome to have what you are trying in a python file instead. I like using geany, which has an **execute** button that saves your work and launches the python interpreter on it in a single click. It makes trying things out sooo much quicker.

---

### Post by mikechant on 2009-08-07
You could try the 'script' command, it sounds like it's exactly what you want:

[http://ayaz.wordpress.com/2006/11/19/script1-logging-terminal-sessions-to-files/](http://ayaz.wordpress.com/2006/11/19/script1-logging-terminal-sessions-to-files/)
[http://linux.die.net/man/1/script](http://linux.die.net/man/1/script)

I used to use it to produce output for 'homework' back in the early 1980's at Uni, on a Vax mini running Unix.

I always remember this command because it used to produce the following error:
"ioctl: Not a typewriter, where are you?"
Which seemed rather amusing because if it didn't know where I was, how did it know to send me the message?

Then despite the error it would work OK.

---

### Post by The Cog on 2009-08-08
> **mikechant said:**
> You could try the 'script' command, it sounds like it's exactly what you want:

Wicked! You learn something new every day.

---

### Post by JatimLex on 2009-09-03
I'm a newbie but this is what I found that worked with the same problem. I installed Geany using Synaptic. To execute Geany once installed use terminal and just type it in. Type your Python program as text, once you save it as (xyz).py you can run the compiler, if there are no errors to run your program press F5 or click execute, Through Geany you can "Save As." Always .py Also there will be another file saved with the extention .pyc you'll need that one its the code. I hope this clears up your problem, no you don't have to re-type over and over again.

---

