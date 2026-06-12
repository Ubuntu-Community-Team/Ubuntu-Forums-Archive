---
title: "Please help me figure out this directory."
date: 2009-05-09
forum: New to Ubuntu
---

### Post by magnoliasouth on 2009-05-09
Okay, I know this should be simple, and I've read and read and read about Ubuntu file structures, but I still can't figure this out. I've come across several things where I need to find particular directories and I can't find them.

One example is on [this page]("http://www.jejik.com/gnome-hearts/developers/#4_2_1"). It says I need to access the *_/scripts_* and *_/src_* directories for my gnome-hearts game. So where in the world are those directories? I cannot find them at all. I even did a search for them and there are just so many folders that I can't possibly figure out how to tell which are the ones I need. 

Is there a hint on where to look? Any direction is greatly appreciated.

---

### Post by Pjotrovitz on 2009-05-09
Well, on that page the wrriter talks about modifying the source code before you compile the program. If you have installed it from the repository you have installed the binary version, and the source code is not included in that. Search wikipedia for 'source code' if this confuses you.

---

### Post by magnoliasouth on 2009-05-09
Aha. Okay thanks much. So that means that I'm only half crazy and not fully crazy since I missed the whole source code thing. Phew! ;)

---

### Post by nhasian on 2009-05-09
the *locate* command is your friend. open a terminal and type

```
locate scripts
```

and it will show you every file that has the word scripts in it.  if there are too many to list you can have it paginate with this command:

```
locate scripts | less
```

locate uses a database that is updated every morning so if you added new files since the last update it wont display them in your search results.  to force it to update the database you simply type:

```
sudo updatedb
```

---

### Post by Alterax on 2009-05-09
Well, these are all good hints, but the thing they all assume is that the source has been downloaded already.  I'm going to assume not.

This isn't the same as installing a program; the source code are the instructions that people write, which are then changed to binary code (like runnable programs) by a compiler.

To get the source code for gnome-hearts, use this command.  Do not use sudo; if you do it can make it difficult to work with the source code:
```

apt-get source gnome-hearts
```

Happy Hacking!

---

