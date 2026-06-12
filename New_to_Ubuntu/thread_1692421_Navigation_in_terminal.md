---
title: "Navigation in terminal"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by laurisplus on 2011-02-21
Hi!
I would like to know how to navigate in terminal. For example, what should I press to navigate to folder "Games" which is into my "Download" folder.
Is there any instructions in terminal itself? Like some kind of "man"

---

### Post by vanadium on 2011-02-21
There are some nice tutorials on the terminal on the web: try a google search, or some friendly soul will post some for you.

To navigate in a folder, you use "Tab completion". this means that you type part of the name, then <tab>: the terminal will complete with an existing match. In your example, it could work with

cd Dow<tab><tab>Gam<tab>

---

### Post by Frogs Hair on 2011-02-21
Here is a start , a search will provide many resources. [https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by howefield on 2011-02-21
cd is the change directory command.

When you open a terminal you'll start off in /home and to get to your Games directory, type

```
cd Downloads/Games
```

Linux is case sensitive, so "Games" would be different to "games".

Try this youtube video for a basic tutorial

[http://www.youtube.com/user/thisweekinlinux?blend=2&ob=1#p/search/1/4Zx7UE70Ehs](http://www.youtube.com/user/thisweekinlinux?blend=2&ob=1#p/search/1/4Zx7UE70Ehs)

or read more at [http://linuxcommand.org/](http://linuxcommand.org/)

---

### Post by thinkinhurtz on 2011-02-21
> **howefield said:**
> cd is the change directory command.

When you open a terminal you'll start off in /home and to get to your Games directory, type

```
cd Downloads/Games
```

Linux is case sensitive, so "Games" would be different to "games".

Try this youtube video for a basic tutorial

[http://www.youtube.com/user/thisweekinlinux?blend=2&ob=1#p/search/1/4Zx7UE70Ehs](http://www.youtube.com/user/thisweekinlinux?blend=2&ob=1#p/search/1/4Zx7UE70Ehs)

or read more at [http://linuxcommand.org/](http://linuxcommand.org/)

Just to add a few things... You can also use the ls and pwd commands to see the contents of a directory.
$ ls - the list command
$ pwd - print working directory

---

### Post by puntigamer on 2011-02-21
Download the "_***The Linux Command Line***_" free PDF book, and study the first 3-4 chapters!
This is how I learned to use the shell ;)

[ftp://csl.tfc.kg.ac.rs/**Linux**/The%20**Linux**%20**Command**%20**Line**.**pdf**]("ftp://csl.tfc.kg.ac.rs/Linux/The%20Linux%20Command%20Line.pdf")

---

### Post by laurisplus on 2011-02-21
Friends, thank you very much for the help!

---

