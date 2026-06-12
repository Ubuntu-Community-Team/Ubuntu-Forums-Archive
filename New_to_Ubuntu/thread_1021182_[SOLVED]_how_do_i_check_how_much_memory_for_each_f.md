---
title: "[SOLVED] how do i check how much memory for each files i've just installed?"
date: 2008-12-25
forum: New to Ubuntu
---

### Post by shiningkenmonster on 2008-12-25
i just installed a bunch of games on add/remove.

than i notice some of the games too way too much memory.(harddrive space)

is there a way to view how much the files take up on memory usage? (harddrive space)

I would like to see which files are memory hogs, and i would like to remove them.

Is there a way to view them? possibly in the terminal?

---

### Post by namdung on 2008-12-25
> **shiningkenmonster said:**
> i just installed a bunch of games on add/remove.

than i notice some of the games too way too much memory.

is there a way to view how much the files take up on memory usage? (harddrive space)

Memory (usually RAM) and Harddrive space aren't always the same thing. Where did u notice the games hogs too much memory? Was it in System-->Admin-->System Monitor-->Processes?

The games are usually installed in /usr/share/games. Right click on the folder and select Properties to know the folder size.

---

### Post by nhasian on 2008-12-25
you could also use the Disk Usage Analyzer in Applications->Accessories.  then you can scan your entire filesystem or just a particular folder like /usr/share/games

---

### Post by neu2buntu on 2008-12-25
run your game/games and in terminal type ```
top
```this will show you the memory used and swap if any

---

### Post by shiningkenmonster on 2008-12-25
yeah I have used Disk Usage Analyzer in the past before. it just has some weird numbers. it says I have: Total filesystem capacity: 21.8 GB (used 11.4 GB available: 10.3 GB)

but i am using a 7.16 GB SSD.

btw, i am not talking about RAM.

I just want to see the list of games/files that i just installed. and see which game takes up more harddrive space than others. So i can removed them and SAVE harddrive space.

---

### Post by newbee70 on 2008-12-25
> **shiningkenmonster said:**
> i just installed a bunch of games on add/remove.

than i notice some of the games too way too much memory.(harddrive space)

is there a way to view how much the files take up on memory usage? (harddrive space)

I would like to see which files are memory hogs, and i would like to remove them.

Is there a way to view them? possibly in the terminal?

Using terminal you could cd into the game folder(s) and type in the:

ls -hal .

---

