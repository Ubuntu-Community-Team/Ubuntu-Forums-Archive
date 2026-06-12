---
title: "how do you know what commands do what?"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by insanity99 on 2009-07-01
i have often asked how to run a program i installed or how to install something through terminal, and the first reply usually is the answer. how do people know what these commands are?

---

### Post by alphacrucis2 on 2009-07-01
> **insanity99 said:**
> i have often asked how to run a program i installed or how to install something through terminal, and the first reply usually is the answer. how do people know what these commands are?

Reading tutorials, books, tech forums... The basic linux commands go back to the early versions of unix so many of these commands have been around for nearly forty years.

---

### Post by WRDN on 2009-07-01
A great resource is the linux man pages. Just type "man [command]" in the Terminal to get information on it.

---

### Post by alphacrucis2 on 2009-07-01
> **WRDN said:**
> A great resource is the linux man pages. Just type "man [command]" in the Terminal to get information on it.

Yes but that doesn't help if you don't know a command exists.

---

### Post by insanity99 on 2009-07-01
ok thanks, it will be nice to be a bit more independent on linux :D 

but it has the best community in the world. really helpful people so it's barly ever a big problem even though i grew up using windows.

---

### Post by credobyte on 2009-07-01
Some commands can be found ( explored ) by executing **help** ( you'll see a list of *arguments* which can be used in combination with **man** ) ! 
Additionally, take  a look at this page : [http://www.ss64.com/bash/](http://www.ss64.com/bash/) .. tons of commands :)

---

### Post by alphacrucis2 on 2009-07-01
> **credobyte said:**
> Some commands can be found ( explored ) by executing **help** ( you'll see a list of *arguments* which can be used in combination with **man** ) ! 
Additionally, take  a look at this page : [http://www.ss64.com/bash/](http://www.ss64.com/bash/) .. tons of commands :)


Also **info** <command>

---

### Post by snakeman21 on 2009-07-01
A lot of it just comes from the experience of tinkering with Linux.  When I started using Linux two years ago, I was very intimidated by the idea of running a command from a Terminal.  But as you learn, you start to remember commands, and you begin to become more comfortable with it.  You start to realize that very often, doing things from the Terminal can be easier, more efficient, and faster.  Now I find myself using the Terminal just about every time I use my computer.  Just give it time and be willing to learn.  A lot of us (like me) started out as n00bz, using this site to answer our questions.  

To give you a simple example, let's say you don't know how to install Wine.  So you look through the forums and see that typing
```
sudo apt-get install wine
```
will do the tick.  Later, you want to install gtkpod.  Armed with the knowledge you learned earlier, you try opening a Terminal and typing
```
sudo apt-get install gtkpod
```
to see if it works.  When it does, you begin to gain confidence.  You just used a Terminal command without having to copy and paste!  As you build confidence, you're going to start using the Terminal more often.  eventually, you'll get to the point where you can pretty much use the Terminal to do anything.  It just takes time :)

---

### Post by mcduck on 2009-07-01
> **alphacrucis2 said:**
> Yes but that doesn't help if you don't know a command exists.

in that case you can use the handy "apropos"-command. It allows you to search for commands based on keywords.

```
$ apropos -a resize image
convert (1)    -convert between image formats as well as resize an image, blur, crop...
mogrify (1)    - resize an image, blur, crop, despecle, dither, draw on, flip, join...
```

Of course a simple search with google or from these forums will also help finding out  what commands to use for the task you want to do.

After a while you'll simply learn the commands and their syntax, just like you learn the words and syntax of any language.

---

### Post by insanity99 on 2009-07-01
ok thanks for all the help guys

---

### Post by boof1988 on 2009-07-01
> **insanity99 said:**
> i have often asked how to run a program i installed or how to install something through terminal, and the first reply usually is the answer. how do people know what these commands are?

Another useful tool is *apropos* (I'm not sure if the program has to be installed already... Probably)...

```

user@host:~$ apropos temperature
hddtemp (8)          - Utility to monitor hard drive temperature
user@host:~$

```

References:
[http://manpages.ubuntu.com/manpages/hardy/man1/apropos.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/apropos.1.html)
[http://linux.about.com/library/cmd/blcmdl1_apropos.htm](http://linux.about.com/library/cmd/blcmdl1_apropos.htm)

---

