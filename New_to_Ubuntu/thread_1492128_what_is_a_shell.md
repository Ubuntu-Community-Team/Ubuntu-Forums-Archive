---
title: "what is a shell?"
date: 2010-05-24
forum: New to Ubuntu
---

### Post by noworldorder on 2010-05-24
I need to do this:

Type this into a shell alsamixer

but I am a total 100% newbie and don't know what a shell is...

---

### Post by lykwydchykyn on 2010-05-24
In common parlance, a "shell" is just another name for the terminal, command line, command prompt, console, or BASH.

---

### Post by utnubuuser on 2010-05-24
Top Left: Applications >> Accessories >> Terminal

---

### Post by doas777 on 2010-05-24
in this case they mean a terminal (Applications -> Accessories -> Terminal).

a shell is technically any user interface. it's a very old school term.

---

### Post by utnubuuser on 2010-05-24
PS. Google" Ubuntu Manual - downloadable PDF  -  free.

Or check out 'the Ubuntu Pocket Guide' - another free PDF download

---

### Post by viralmeme on 2010-05-24
> **noworldorder said:**
> I need to do this:

Type this into a shell alsamixer

but I am a total 100% newbie and don't know what a shell is...

See 'Starting a Terminal` [http://gd.tuwien.ac.at/linuxcommand.org/lts0010.php#starting](http://gd.tuwien.ac.at/linuxcommand.org/lts0010.php#starting)

You would also need to run commands as 'root` eg: sudo alsamixer

---

### Post by nmaster on 2010-05-24
> **lykwydchykyn said:**
> In common parlance, a "shell" is just another name for the terminal, command line, command prompt, console, or BASH.

for the OP, although it is the default, bash is not the only shell. this document might be helpful:  [http://consult.cern.ch/writeup/shellchoice/main.ps](http://consult.cern.ch/writeup/shellchoice/main.ps)

---

### Post by houseworkshy on 2010-05-24
This takes a newbie to competance very well;- [http://linuxcommand.org/lts0010.php](http://linuxcommand.org/lts0010.php) there is a free pdf version too for offline use [http://lcorg.blogspot.com/search/label/Book](http://lcorg.blogspot.com/search/label/Book)
That's for when you want to learn most of it.  Meanwhile the terminal has a very good built in help.  Typing "man" in front of any command will bring up it's manual page, eg try "man man", or "man ls".  This is handy for learning and also for making sure that any advice you are given is benign, I haven't seen it yet but there is a sticky warning against malicious commands.  You can open more than one terminal or "shell" so using one to do things and the other for help pages makes life easy.  To exit from the help just type "q".  One can also copy and paste.
Another useful one is "apropos" ;typing this in front of any word will search the manual pages for the term and if found list the commands.  Good for times when you know what you want but don't have a clue what the command may be.  Try "apropos find" to see how it works.
It's not as complex as it looks.  Most things can be done in the gui anyway so you can learn when you feel like it and still use the gui for most tasks.
Quotes used above are only to seperate commands from text so don't enter them.

---

