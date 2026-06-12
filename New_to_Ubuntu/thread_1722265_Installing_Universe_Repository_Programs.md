---
title: "Installing Universe Repository Programs"
date: 2011-04-05
forum: New to Ubuntu
---

### Post by alexis44 on 2011-04-05
I looked around in the Synaptic Package Manager and selected five programs that were listed in the Graphics "Universe" category and installed them.  I re-booted the computer and looked at the menu and could not find them listed anywhere.  After trying to find an answer, I found this:
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

I followed the directions and saw that the "Community Maintained Open-Source Software" (Universe) was already checked.  It should have already been enabled.  I closed the program.  I went into the Software Center and typed in the names of the programs that I installed.  Each one came back positive that they were installed.  They're not in the menu.  Do they have to be enabled in the Terminal?  Anyone know? :)

---

### Post by oldos2er on 2011-04-05
If they are CLI programs, they will not have a menu entry. What are the names of the programs you installed?

---

### Post by coffeecat on 2011-04-05
Which applications did you install? They may not have been GUI programs. There are a lot of terminal utilities in the repositories.

---

### Post by alexis44 on 2011-04-05
I think they are all GUI type programs.  

!) gifsicle  manipulating GIF's..

2)gtkmorph  

3) libavidemux0

4)libpuzzle-bin

5) pqiv viewer

---

### Post by coffeecat on 2011-04-05
From man gifsicle:

> gifsicle  is  a  powerful  command-line  programFrom package description for libpuzzle-bin:

> This package contains the command-line tool: puzzle-diff.libavidemux0 is a library for avidemux. You can't run a library. Install avidemux.

As far as I can make out gtkmorph and pqiv are designed to be run from the terminal even though they are GUI programs. Try 'man gtkmorph' and 'man pqiv' for more.

Don't forget that Universe and Multiverse apps are not official Ubuntu-supported ones. The quality varies and you do get GUI apps where the devs haven't set the packages up to create menu entries.

---

