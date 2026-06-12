---
title: "GUI / Terminal Program Structure"
date: 2011-07-02
forum: New to Ubuntu
---

### Post by jkurtisr32 on 2011-07-02
Hey everyone,

I was wondering if there was anyone who could tell me how some of the unix-based programs are structured.

To be specific, I was wondering how a program (Unison, for example) has both a terminal interface and a graphical interface. The way that I imagine it working in my head is that there is a terminal-driven application which is then controlled by a GUI on top of it. Is that even close to correct?

I would love to be able to build a terminal application that can be driven by different interfaces (local QT and/or web HTML)

Any insight would be greatly appreciated.

Thanks,
Kurt

---

### Post by jkurtisr32 on 2011-07-03
Bumpers

---

### Post by CatKiller on 2011-07-03
> **jkurtisr32 said:**
> To be specific, I was wondering how a program (Unison, for example) has both a terminal interface and a graphical interface. The way that I imagine it working in my head is that there is a terminal-driven application which is then controlled by a GUI on top of it. Is that even close to correct?

Not really. Most programs aren't interactive at all - you'd just use the command line to start them, and then they stop when they're finished. Other programs can start and stop these programs, which is how you get "front ends" for programs. These front ends could be text-based or graphical and you can make other programs that act as front ends for these front ends, which is how you can end up with Synaptic being a front-end for apt-get, which is itself a front-end for dpkg.

Often these front ends are able to invoke several different programs to do combinations of things, for example EasyTag can modify the tags of many different types of audio file even though the different types of file have very different tag structures. It does this by invoking a different specialised program for each type of file. Sometimes the front ends are very simple and just invoke one program with a particular set of options. These exist largely to help users who don't want to use the command line and don't want to read man pages to find out how to specify the options for that particular program (or indeed to find out what the options are).

Front ends would probably be written using some kind of framework. That might be curses for a text-based front end, or GTK+ or Qt for graphical ones.

Hope this helps.

---

### Post by jkurtisr32 on 2011-07-05
> **CatKiller said:**
> Not really. Most programs aren't interactive at all - you'd just use the command line to start them, and then they stop when they're finished. Other programs can start and stop these programs, which is how you get "front ends" for programs. These front ends could be text-based or graphical and you can make other programs that act as front ends for these front ends, which is how you can end up with Synaptic being a front-end for apt-get, which is itself a front-end for dpkg.

Often these front ends are able to invoke several different programs to do combinations of things, for example EasyTag can modify the tags of many different types of audio file even though the different types of file have very different tag structures. It does this by invoking a different specialised program for each type of file. Sometimes the front ends are very simple and just invoke one program with a particular set of options. These exist largely to help users who don't want to use the command line and don't want to read man pages to find out how to specify the options for that particular program (or indeed to find out what the options are).

Front ends would probably be written using some kind of framework. That might be curses for a text-based front end, or GTK+ or Qt for graphical ones.

Hope this helps.

This is good stuff. Thanks for the input, dude.

-Kurt

---

