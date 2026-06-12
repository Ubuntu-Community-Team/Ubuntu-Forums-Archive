---
title: "Best way to learn terminal?"
date: 2010-11-17
forum: New to Ubuntu
---

### Post by jimijames on 2010-11-17
New ubuntu user here, and I'd like very much to learn terminal so I can navigate more easily and efficiently.  I also feel as though it is a good introduction into the architecture of ubuntu and how it operates, and feel as though it is a good starting point for a relatively inexperienced user such as myself.

What resources would be best for learning how terminal operates?  Or should I just open up terminal and start looking around?  Would it be better to look up beginner's linux guides and go from there?

Thanks for any and all help, I'd like to learn more about ubuntu, as well as the GNOME and KDE desktop environments, Xubuntu, and so forth.  I understand that it is a long and arduous road ahead, but I'm a tinkerer and I just don't know any better to be honest.

---

### Post by GabrielYYZ on 2010-11-17
check this out: [http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/](http://fosswire.com/post/2008/04/ubuntu-cheat-sheet/)

some useful commands you might need every once in a while and a nice explanation for each one. i'd say that's a good starting point...

edit: here's another one, for unix/linux in general: [http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/)

---

### Post by Enigmapond on 2010-11-17
The best way to learn is just by doing...here, these will be a good start:

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

good luck..:) The CLI ROCKS!

---

### Post by jmszr on 2010-11-17
jimijames,

Welcome Aboard!

Here are a few links that should be useful: [http://www.stat.tamu.edu/~dahl/teaching/605/1.20/shell-tutorial/html/index.html](http://www.stat.tamu.edu/~dahl/teaching/605/1.20/shell-tutorial/html/index.html)  and: [http://ubuntuforums.org/showthread.php?t=714338](http://ubuntuforums.org/showthread.php?t=714338)  (Newbie Terminal Intro) . Also: [http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)   (Terminal for Beginners)

---

### Post by JamButty on 2010-11-17
CliCompanion can be helpful. It functions as a terminal, but allows you to build up a reference list of useful/often used commands, which can save a bit a of  time thrashing around in manuals.

---

### Post by Enigmapond on 2010-11-17
Here's another tip...if you type "history" (no quotes) in the terminal it will give you that last 500 or so things you typed in. Just look for what you want, and enter:

```
!{line number}
```

this will save you from typing the line...:)

---

### Post by Old_Man_Unix on 2010-11-18
The 'terminal' is essentially the Linux shell  - which is ***bash*** by default.

If you do a Google search on "*bash tutorials*" , you will come up with thousands of suggested sites.  Some very good, and some not so good.  Try a few and I'm sure you will find some  to your liking.

I hesitate to recommend one in particular because I may be coming from a different background than you and what I find useful you might not.

I will say that the following tutorial is very well done.

[http://learnbyexamples.org/linux/bash-programming-tutorial-1-a-quick-introduction.html](http://learnbyexamples.org/linux/bash-programming-tutorial-1-a-quick-introduction.html)

There is also an entire book devoted to bash:* Learning the bash Shell*,                    2nd Edition by O&#8217;Reilly & Associates, Inc.

Whatever you do, however, please heed the following:

> **Warning!!!!**
 Do not practice scripting as the root                    user!  Anything could happen! I will not be held responsible                     if you accidentally make a mistake in the coding and screw up                     your system. You have been warned! Use a normal user account                     with no root privileges. You may even want to create a  new user                    just for scripting practice. This way the  worst thing that can                    happen is the user&#8217;s directory  gets blown away.


Good luck.

---

### Post by alienprdkt on 2010-11-18
> 
Warning!!!!
Do not practice scripting as the root user! Anything could happen! I will not be held responsible if you accidentally make a mistake in the coding and screw up your system. You have been warned! Use a normal user account with no root privileges. You may even want to create a new user just for scripting practice. This way the worst thing that can happen is the user’s directory gets blown away.

Reason why I do all testing inside of VirtualBox!

and agree Bash is what you are looking for:

[http://www.gnu.org/software/bash/manual/bashref.html]("http://www.gnu.org/software/bash/manual/bashref.html")

[http://tldp.org/LDP/abs/html/]("http://tldp.org/LDP/abs/html/")

---

### Post by weasel fierce on 2010-11-18
There's a few decent books out there as well, to help with this sort of thing, if you prefer dead-tree to screen.

Ive found Sobell's "A practical guide to linux" incredibly useful. Its also the size of a brick so you can use it to beat away an attack bear

---

### Post by jimijames on 2010-11-18
Wow, thank you guys so much - I'll take a look at as much of that as I can when I get a chance.  I'm studying for the lsat and I'm going to be on the road a lot, and on top of that I have other interests that take time as well (cars and guitars mostly).  I do appreciate it and I'm sure I will come back with more questions once I get further into it.  This looks like a great community and I'm excited to have the opportunity to learn from all of you guys.

---

### Post by chamira on 2010-11-19
> **Enigmapond said:**
> The best way to learn is just by doing...here, these will be a good start:

[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)



Thanks for this link, absolutely the best intro I found so far and the free 522 page book is amazing :[http://www.linuxcommand.org/tlcl.php](http://www.linuxcommand.org/tlcl.php)

:popcorn:

---

### Post by tacantara on 2010-11-19
I have attached a PDF that contains four pages of terminal commands. I downloaded it from Scribd.com.  This should give you a nice reference to peruse and/or print.  Have fun with it :)

---

### Post by Kir_B on 2010-11-21
> **Enigmapond said:**
> Here's another tip...if you type "history" (no quotes) in the terminal it will give you that last 500 or so things you typed in. Just look for what you want, and enter:

```
!{line number}
```this will save you from typing the line...:)

That's awesome!

Thanks Enigmapond.

Good day all. Kirby

---

### Post by tolf242 on 2010-11-21
[SIZE=2]Hi, there some free e-books available for downloading if you wish to try that(some are very heavy on the printer).

[http://www.linuxconfig.org/free-ebook-linux](http://www.linuxconfig.org/free-ebook-linux)

Regards Tolf242.
[/SIZE]

---

### Post by duanedesign on 2010-12-02
> **JamButty said:**
> CliCompanion can be helpful. It functions as a terminal, but allows you to build up a reference list of useful/often used commands, which can save a bit a of  time thrashing around in manuals.

There has been a new release of [CLI Companion]("http://okiebuntu.homelinux.com/blog/?p=238"). One improvement inn this release is that it comes with a lot more commands in the 'Command Dictionary' by default. This gives people new to the Terminal a wider range of commands to play with to show them what the command line can do.

thank you,
duanedesign

---

### Post by maryalesia on 2010-12-03
> **weasel fierce said:**
>  Its also the size of a brick so you can use it to beat away an attack bear

I was laughing for a good minute

---

