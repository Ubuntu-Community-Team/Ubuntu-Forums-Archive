---
title: "View hidden file in terminal"
date: 2010-11-27
forum: New to Ubuntu
---

### Post by slgtheindividual on 2010-11-27
Just wondering how to view a hidden file in the terminal; I have a file called ".example" in my current working directory which I can view using Nautilus using the show hidden files toggle but when I use "ls" from the terminal it doesnt list it, anybody know how to make it list it in the terminal?

Thank you in advance

---

### Post by Vaphell on 2010-11-27
```
ls -a
```
there is a chance that you got an 'la' alias configured by default, which is equivalent to ls -a, so
```
la
``` should work too

```
grep alias ~/.bashrc
``` to see aliases already configured, you can add your own

**ls --help** to get more info on available options
always try --help option, 99% of command line tools has it

---

### Post by slgtheindividual on 2010-11-28
thankyou =]

---

### Post by TurtleKing on 2011-09-20
Can a moderator please delete this post? I posted by accident thinking I was in the correct tab of the web browser (sorry for inconvenience).

---

### Post by Paqman on 2011-09-20
> **TurtleKing said:**
> It shows up on the terminal, but in nautilus it does not show up.

Hit Ctrl-H (for "show hidden files")

---

