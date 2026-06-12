---
title: "Symbolic Link Help"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by 3rr0r on 2010-12-13
Hello.  I am currently running Lucid 10.04 and I noticed that it has python 2.6.5 by default.  An application I use requires the use of python 2.6.2.  As such, I found directions to install python 2.6.2 but now I don't know how to invoke it without giving the full path to the interpreter.  How do I make a symbolic link so that I can just type "python262" to invoke it?

The path to the python 2.6.2 interpreter is located at 

/usr/local/src/Python-2.6.2/python


Thank you all :)


EDIT: I think this is called, "adding to my PATH" ?

---

### Post by low_rider on 2010-12-14
If it is a program that needs to run python you'll need to make sure you create the sym-link in the right place and that you name it the same.  Either way you create sym-links using:
 ln -s TARGET DIRECTORY
where target is /usr/local/src/Python-2.6.2/python in your case and DIRECTORY is where you want the sym-link to go.

If what you want is to be able to run python from the command line you'll want your directory to be something like /usr/bin/python

---

### Post by 3rr0r on 2010-12-14
I have a python program (script?) that requires the use of python 2.6.2

I want to be able to execute this tool (used to analyze pdf files) using python 2.6.2 without clobbering the installed 2.6.5.

I want to be able to run
```

python262 pdftool.py file.pdf
```

right now when I run 
```

pdftool.py file.pdf
```

it executes with python 2.6.5.  Did that make sense?  Can you expand on your answer a bit more please?

---

### Post by AngusH on 2010-12-14
Seems to me that it would be easier to use a bash alias (assuming your only going to be launching this thing from within the terminal and scripts). To do that you want to add something to the tune of ```
alias python262='/usr/local/src/Python-2.6.2/python'
```
Let me know if that's not clear.
Angus

---

### Post by 3rr0r on 2010-12-14
> **AngusH said:**
> Seems to me that it would be easier to use a bash alias (assuming your only going to be launching this thing from within the terminal and scripts). To do that you want to add something to the tune of [CODE]alias python262='/usr/local/src/Python-2.6.2/python/'[CODE]
Let me know if that's not clear.
Angus

YES!  This would always only be run from the terminal.  So, where would I add this alias?  .bashrc?

---

### Post by AngusH on 2010-12-14
Either to .bashrc or .bash_aliases (it's a bit neater to put it there I think).
Angus

---

