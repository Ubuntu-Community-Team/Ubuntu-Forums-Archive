---
title: "Open source projects in c++"
date: 2011-06-28
forum: New to Ubuntu
---

### Post by tejaswidp on 2011-06-28
I can code simple console applications and a friend suggested that it would be good to read code. Can someone tell me if there are any simple open source c++ projects that i can follow.

---

### Post by seawolf167 on 2011-06-28
My best advice is to learn to read code by actually coding so you can understand what each argument does. A good place to start is [here]("http://en.wikibooks.org/wiki/Subject:C%2B%2B_programming_language"). Tons of reading and practice coding :P

My programming editor of choice in Ubuntu is Geany

```
sudo apt-get install geany
```

---

### Post by deconstrained on 2011-06-28
Before you look any further into coding I highly recommend you acquaint yourself with version control & revision tracking software like Git, CVS, Mercurial & Bazaar. All open-source projects use them, and if you ever want to eventually submit or suggest patches/revisions to the project you must use their software.

For example: ncmpcpp, a command-line ncurses-based mpd* client that I absolutely love, uses Git, and I build it from source/obtain source updates using git. I also use git for my own coding project and really like it, but that's another story (and it's more of a niche/academic/research program).

* music player daemon, an awesome and highly versatile music player based on the server-client model. If you haven't checked it out and haven't seen what it's capable of I highly recommend it.

---

### Post by nick_goodfate on 2011-06-28
> **tejaswidp said:**
> I can code simple console applications and a friend suggested that it would be good to read code. Can someone tell me if there are any simple open source c++ projects that i can follow.

Search for "c++" in [GitHub]("https://github.com/")

---

### Post by tejaswidp on 2011-06-30
i am familiar with git. i have even used it to create a simple console text editor. are there any books or tutorials you would recommend for learning gtk?

---

### Post by tejaswidp on 2011-06-30
> **seawolf167 said:**
> My best advice is to learn to read code by actually coding so you can understand what each argument does. A good place to start is [here]("http://en.wikibooks.org/wiki/Subject:C%2B%2B_programming_language"). Tons of reading and practice coding :P

My programming editor of choice in Ubuntu is Geany

```
sudo apt-get install geany
```

i have been using geany as well

---

### Post by deconstrained on 2011-07-01
> **tejaswidp said:**
> are there any books or tutorials you would recommend for learning gtk?
It would be good to start with Python. GTK is largely written in Python, and functions within its API can very easily be invoked via Python, though there's C/++ in it as well.

---

### Post by PGScooter on 2011-07-07
I am learning by reading and experimenting with LyX. See [http://www.lyx.org](http://www.lyx.org). The developer group is very open and active, and the code is very interesting. It is written in C++ and for the GUI it uses QT4. I would also recommend reading a book along the way. For beginning, try Accelerated C++ for something fast or C++ Primer (4th edition) for something in depth. Good luck!

---

### Post by wep940 on 2011-07-08
I've written a few apps in C using GTK, but I've never learned C++.  I can tell you that as with any tool, GTK can be used simply and works great, but also has some other "power" functions you can use.  The beauty is that it is easy to develop cross-platform apps with C/C++ and GTK.  I have the same code compiling and running in Windows XP and Ubuntu both.

---

