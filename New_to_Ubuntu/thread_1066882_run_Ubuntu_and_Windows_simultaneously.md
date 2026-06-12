---
title: "run Ubuntu and Windows simultaneously"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by rgb96 on 2009-02-11
hey guys and girls,

I am writing a glue-type program right now that, among other things, has to run two separate programs. That's easy enough. However, one of the programs is only compatible with Linux, and the other is only compatible Windows. At least, how they are compiled now, and no I don't have source to re-compile.

Anyways, the machine I'm on has 2 hard drives, one with Ubuntu 8.10, and the other with Windows XP. My question is this, is there any way to run Ubuntu and Windows simultaneously so that I can actually write this program without creating a virtual machine?

Thanks for any insight.

---

### Post by 0bso on 2009-02-11
> **rgb96 said:**
> hey guys and girls,

IMy question is this, is there any way to run Ubuntu and Windows simultaneously so that I can actually write this program without creating a virtual machine?

To the best of my knowledge, no. What is your aversion to running a VM?

Only other option might be running the windows program in wine or similar while booting linux or vice versa (linux emulator while running windows). But either of those options would probably make bug tracking a nightmare.

---

### Post by crho85 on 2009-02-11
one of your best solutions may be to find a linux alternative to the windows program. 

what program do you "need" windows for

you could always us WINE if it is compatable

---

### Post by rgb96 on 2009-02-11
> **crho85 said:**
> what program do you "need" windows for

It's a program that controls the abacus 5000 machines in the lab. Those are Beowulf class supercomputers that are basically bulk call generators.

My aversion to a VM machine is that I have very limited space on the hard-drive that I am writing the program on. although I might end up having to do a VM anyways.

What is wine exactly?

---

### Post by 0bso on 2009-02-11
[http://en.wikipedia.org/wiki/Wine_(software](http://en.wikipedia.org/wiki/Wine_(software))

It simulates(translates?) the windows API so you can run most windows programs.
.

---

### Post by crho85 on 2009-02-11
> **rgb96 said:**
> It's a program that controls the abacus 5000 machines in the lab. Those are Beowulf class supercomputers that are basically bulk call generators.

My aversion to a VM machine is that I have very limited space on the hard-drive that I am writing the program on. although I might end up having to do a VM anyways.

What is wine exactly?

WINE is a windows emulator, it works well with most basic programs. 
[URL="http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true"]
Application Database[/URL]

You can look it up here, if it is not there feel free to try it out

---

### Post by 0bso on 2009-02-11
> **crho85 said:**
> WINE is a windows emulator

WINE = **W**ine **I**s **N**ot an **E**mulator :)

---

### Post by rgb96 on 2009-02-11
> **0bso said:**
> WINE = **W**ine **I**s **N**ot an **E**mulator :)

lol.  Thanks guys, I'll look into that.

---

