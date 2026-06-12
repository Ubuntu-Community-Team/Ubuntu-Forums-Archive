---
title: "the bash shell"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by mzdrojowy on 2009-05-03
so ... what I want is to use unbuntu without 90% of the GUI ..... I know this is possible 
and I know the shell's the key ... 
What I'm wondering is , what do you guy's recomend I use for a startting point to  my journey into the shell ..:guitar:

---

### Post by Iowan on 2009-05-03
Probably something you already know:
 CTRL-ALT-F1 thru CTRL-ALT-F6 will give you a terminal from which to journey.  CTRL-ALT-F7 will take you back to the GUI.

---

### Post by unutbu on 2009-05-03
Start here:
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

Also good:
[http://tldp.org/LDP/Bash-Beginners-Guide/html/](http://tldp.org/LDP/Bash-Beginners-Guide/html/)
[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)
[http://tldp.org/LDP/abs/html/](http://tldp.org/LDP/abs/html/)

When you have mastered the basics of the shell, you might want to consider moving on to Python. It has a much simpler syntax, and very powerful. Many things which are difficult to do in bash can be done more easily in Python.

---

### Post by Skrynesaver on 2009-05-03
Learn the basic commands, 
```
ls, cd, mkdir rm, less, vim, awk, sed, mount, locate, find, head, tail, grep
```Read the man pages ```
man $command
```Make a directory ~/bin and add it to your path by adding the following line to ~/.bashrc ```
PATH=$PATH:$HOME/bin
```Start writing simple scripts that do things you regularly do and save them in this directory, they are now part of **your** CLI environment
There are several online guides [this]("http://www.faqs.org/docs/Linux-HOWTO/Bash-Prog-Intro-HOWTO.html") is probably the most useful
Ask people either here or in your local [LUG mailing list]("http://www.linux.org/groups/") if you are having a problem
Finally try things out and see what happens, have fun, you'll never look back ;)

---

