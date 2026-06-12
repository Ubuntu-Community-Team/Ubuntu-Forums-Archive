---
title: "What programming language are source code files of ubuntu such as .bashrc written in?"
date: 2011-03-28
forum: New to Ubuntu
---

### Post by btf18 on 2011-03-28
The title says it all.
 
Thanks

---

### Post by oldos2er on 2011-03-28
.bashrc is an ASCII configuration file. If you meant bash, I think it's written in C.

---

### Post by btf18 on 2011-03-29
Thank you. Yes, the lines in the .bashrc file are code arent they? is it a language? It is a style of coding one must learn to add lines to configure their computer, is the style just called ASCII? Or is it a language with a name?
 
Thanks

---

### Post by rosencrantz on 2011-03-29
However, as .bashrc is to be executed by the bash shell on startup, it contains code in bash shell syntax.
Check wikipedia [http://en.wikipedia.org/wiki/Bash_(Unix_shell](http://en.wikipedia.org/wiki/Bash_(Unix_shell))
and whatever bash tutorial you find online (e.g. this one [http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html))

---

### Post by rosencrantz on 2011-03-29
Is there anything specific you need to add to your .bashrc or is this a general interest question?

Cheers,
rosencrantz

---

### Post by Telengard C64 on 2011-03-29
As rosencrantz mentioned, **.bashrc** is written in the Bash language. It is documented here:

[http://www.gnu.org/software/bash/manual/html_node/index.html](http://www.gnu.org/software/bash/manual/html_node/index.html)

---

### Post by btf18 on 2011-03-29
Thank you :-) I have been learning some bash shell, and ive moved on to making programs, though the compiling never works :-/ bash shell must be interpreted as no compiling is needed? There is no specific line i need to add to .bashrc, i just learnt to add paths to it and it got me thinking what code i was actually writing.

---

### Post by Telengard C64 on 2011-03-29
I would say Bash is an [interpreted language](http://en.wikipedia.org/wiki/Interpreted_language). The distinction between interpreted and [scripting languages](http://en.wikipedia.org/wiki/Scripting_language) is a bit blurry though.

---

### Post by Nutria on 2011-03-29
> **btf18 said:**
> Thank you :-) I have been learning some bash shell, and ive moved on to making programs, though the compiling never works :-/ bash shell must be interpreted as no compiling is needed? There is no specific line i need to add to .bashrc, i just learnt to add paths to it and it got me thinking what code i was actually writing.

Correct, bash is an interpreter.  (As are Perl, Python, sed and awk.)

Note that while bash is featureful, it's greatest strength is that it is glue for and is extended by the hundreds of CLI utilities on your machine

---

### Post by nothingspecial on 2011-03-29
Read this

[http://mywiki.wooledge.org/BashGuide](http://mywiki.wooledge.org/BashGuide)

---

