---
title: "Terminal Information"
date: 2009-09-24
forum: New to Ubuntu
---

### Post by Goveynetcom on 2009-09-24
Well, I have had to do things in the terminal and now I want to make sure I understand it really well. As far as I'm concerned the terminal reminds me of the Command Prompt in Windows. Where is a place I can learn how to work with the terminal?

---

### Post by tuxxy on 2009-09-24
Try the terminal guide for the basic commands and also specific man pages 

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by jerome1232 on 2009-09-24
Learn how to navigate the file system, and learn how to read man pages. After that learn how to use pipes and how to redirect output from a program.

After that you are really just learning how to use the various command line programs. If you really want to dig in deep you can begin learning about bash scripting.

---

### Post by QIII on 2009-09-24
You can get some info about what is available like this (you'll get more than you could possibly want to know...)

```
apropos "" -s <number> |less
```using the following numbers:

           1   Executable programs or shell commands
          2   System calls (functions provided by the kernel)
          3   Library calls (functions within program libraries)
          4   Special files (usually found in /dev)
          5   File formats and conventions eg /etc/passwd
          6   Games
          7   Miscellaneous (including macro  packages  and  conven&#8211;
            tions), e.g. man(7), groff(7)
          8   System administration commands (usually only for root)
          9   Kernel routines [Non standard]

But before you actually do anything, look at the man pages so you know what you are doing. I.e.:

```
man grep
```

---

### Post by jmszr on 2009-09-24
Goveynetcom,

This is useful as a simple introduction to the terminal: [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338) and this is more thorough: [http://beginlinux.com/desktop_training/ubuntu/1094-the-beginners-guide-to-the-ubuntu-terminal](http://beginlinux.com/desktop_training/ubuntu/1094-the-beginners-guide-to-the-ubuntu-terminal) .

Hope that helps.

Edit: And this: [http://gd.tuwien.ac.at/linuxcommand.org/index.php](http://gd.tuwien.ac.at/linuxcommand.org/index.php)

---

