---
title: "Add paths to $PATH and $MANPATH"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by .:PiXi²:. on 2009-06-07
I've searched on this topic for the last two hours and this (probably) very simple question is still unanswered.
Please can someone tell me how to add paths to $PATH and $MANPATH ?
The "solutions" I found via Google don't seem to work...

Sorry for my bad English and thanks in advance.

---

### Post by fr4nko on 2009-06-07
Hi,

it is very simple, you have to type:

export PATH=$PATH:/the/path/you/want

This is a valid command using the bash shell, but "bash" is the default on most linux installation. I will explain the command. The keyword "export" means make the change visible also for the other program that I can launch. Afterward is pretty self-explanatory, in bash to define a variable you type

export MYVAR='the value of the variable'

In the case of the PATH we have used $PATH on the right hand side of the expressions. When you have a dollar before a variable name the shell (bash) will expand it to its value.

With MANPATH I guess you can just do the same.

Francesco

---

### Post by mgol on 2009-12-28
@fr4nko
MANPATH variable in Ubuntu Karmic is empty. manpath command gives sth like that, though:
/usr/local/man:/usr/local/share/man:/usr/share/man

If one wants to change manpath output, they should either modify /etc/manpath.config file (which isn't easy) or create new MANPATH variable.

Example - recently, I replaced cdrkit packages with original cdrtools. Because of that, I had to add /opt/schily/man to manpath. A correct way is to do that:
```
unset MANPATH
export MANPATH=/opt/schily/man:$(manpath)
```
It's important to unset MANPATH first so that it actually takes real manpath output (inherited from /etc/manpath.config) before each change.

Next 'manpath' invocation informs about a change:
```
$ manpath 
manpath: warning: $MANPATH set, ignoring /etc/manpath.config
/opt/schily/man:/usr/local/man:/usr/local/share/man:/usr/share/man
```

---

