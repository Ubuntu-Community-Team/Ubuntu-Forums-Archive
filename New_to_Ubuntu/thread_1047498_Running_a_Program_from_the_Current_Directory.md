---
title: "Running a Program from the Current Directory"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by heavyJ25 on 2009-01-22
Hey guys, I have a fairly simple question. 

When running a program in a terminal from my current directory, I always have to type "./" before the program name, or it will not recognize it. Can I change that so I can just type in the name of the program and it will run? 

Thanks for your help.

---

### Post by lykwydchykyn on 2009-01-22
You can, but it's advised that you don't do that. The reason it is this way is for security.  

For instance, say I drop a malicious script in your home directory called "firefox".  If you run "firefox" without specifying a path (whether at a CLI or through a shortcut, etc), it's going to run the script in your home directory, not the real firefox.

---

### Post by Titan8990 on 2009-01-22
Sort of. You can make the command a system wide command two ways.

1) Add the path of the program to your PATH in ~/.bashrc

2) create a symbolic link from the program to an existing directory in your PATH

To view your current PATH:


echo $PATH


To add a custom path:

```
PATH=$PATH:/custom/path
export PATH
```

You would add that to your ~/.bashrc

---

### Post by donkyhotay on 2009-01-22
You have to change the path, but be careful doing so. As mentioned previously it's a (potential) security risk. What I do is create my own bin folder within my home folder, point my paths to that, and then create my own script in it. I wouldn't recommend pointing your path to your regular home folder for instance but on a standard personal desktop the chances of anything bad happening if you did so are practically nil.

---

