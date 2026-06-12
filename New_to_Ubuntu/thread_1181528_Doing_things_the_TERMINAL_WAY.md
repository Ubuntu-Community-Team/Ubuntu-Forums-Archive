---
title: "Doing things the TERMINAL WAY"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by raziiq on 2009-06-08
Hi there.

Well i have gone through this forum and learned alot of things, some of them were GUI based some of them were Terminal based.

I would like to know how can i do everything using Terminal, For example Mounting drives, changing GUI etc. I know these things are available on the Forum in different threads but is there any tutorial about terminal where i can get all these things altogether at one place using some examples.

---

### Post by CJ Master on 2009-06-08
I'm not sure why you would want to do things using only the terminal, but these links may be of help:

[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)

[http://www.ss64.com/bash/](http://www.ss64.com/bash/)

---

### Post by ad_267 on 2009-06-08
This is usually a good place to start: [http://linuxcommand.org/](http://linuxcommand.org/)

Once you know the basics you can learn to read man pages and figure out commands yourself. So to learn how to mount stuff you can use "man mount"

---

### Post by raziiq on 2009-06-08
i m a windows user and want to learn more and more about Linux, so thats why trying to start it from Terminal, as doing things GUI way is not new to me.

BTW thanks for those links, i ll go through them

---

### Post by CJ Master on 2009-06-08
> **raziiq said:**
> i m a windows user and want to learn more and more about Linux, so thats why trying to start it from Terminal, as doing things GUI way is not new to me.

BTW thanks for those links, i ll go through them

Once you learn enough, I recommend that you try an Ubuntu minimum command line install. You can then pick and choose your own packages installing, giving you more control. After you're very comfterable with that, you may want to try [Arch Linux](http://www.archlinux.org/), which is the ultimate in reasonable customization. In the far future, you may then want to try Linux From Scratch, to create your own Distrobution.

Take it with a grain of salt :P

---

### Post by raziiq on 2009-06-08
ya thanks for that.

I have gone through those commands of installing apps using terminal n using apt-get command, these days learning scripts, wish me luck ;)

---

### Post by x33a on 2009-06-08
one more thing:

always look at the man pages of the stuff you try, you can learn many unknown options.

```
man name_of_software/command
```

e.g.
```
man man
```

another useful command to find the location of installed software
```
whereis option
```

option = name of software.

---

### Post by raziiq on 2009-06-09
thanks for those commands.

I have been using uBuntu for 2 months now almost, i have read 3 or 4 books also, i am getting use to it, but still knowing hardware commands is a challenge, i mean commands like glxinfo are not illustrated in any book or tutorial, so how to know about commands like these?

---

### Post by Zill on 2009-06-09
> **raziiq said:**
> I have been using uBuntu for 2 months now almost, i have read 3 or 4 books also, i am getting use to it, but still knowing hardware commands is a challenge, i mean commands like glxinfo are not illustrated in any book or tutorial, so how to know about commands like these?

A quick search on Google shows 84,300 English pages for glxinfo, the first one being the GLXINFO(1) manual page.

btw, Linux is case sensitive, particularly where terminal commands are concerned, hence "uBuntu" is not the same as "Ubuntu". ;-)

---

### Post by raziiq on 2009-06-09
> **Zill said:**
> A quick search on Google shows 84,300 English pages for glxinfo, the first one being the GLXINFO(1) manual page.

btw, Linux is case sensitive, particularly where terminal commands are concerned, hence "uBuntu" is not the same as "Ubuntu". ;-)

you didnt get me, glxinfo was just an example, i was trying to say that even reading books and tutorials wont help you know commands like glxinfo, xrand, mount etc, which are system based commands and are not explained in any book i have gone through yet.

---

### Post by Celauran on 2009-06-09
> **raziiq said:**
> thanks for those commands.

I have been using uBuntu for 2 months now almost, i have read 3 or 4 books also, i am getting use to it, but still knowing hardware commands is a challenge, i mean commands like glxinfo are not illustrated in any book or tutorial, so how to know about commands like these?

The same way you learned your way around Windows, really. Experience.

---

### Post by Mornedhel on 2009-06-09
Let me introduce you to apropos :

```
username@machine:~$ apropos glx
glxdemo (1)          - a demonstration of the GLX functions
glxgears (1)         - ``gears'' demo for GLX
glxheads (1)         - exercise multiple GLX connections
glxinfo (1)          - show information about the GLX implementation
username@machine:~$ man glxinfo
```

---

### Post by decoherence on 2009-06-09
> **Mornedhel said:**
> Let me introduce you to apropos

Darn, you beat me to it!

Use apropos to find the command that does what you want to do. Then use man to learn how to use it.

---

### Post by raziiq on 2009-06-09
> **Celauran said:**
> The same way you learned your way around Windows, really. Experience.

Ya i think the same way, its the experience and practice that will do the trick for me, spending time with uBuntu and exploring different files is the way to go. Like for example i never knew there is something like gconf-editor, its an amazing thing.

---

