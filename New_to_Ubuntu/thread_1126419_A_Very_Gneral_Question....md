---
title: "A Very Gneral Question..."
date: 2009-04-15
forum: New to Ubuntu
---

### Post by Swenghk on 2009-04-15
When game designers and people make games and stuff...How do they combine what everyone has done, like the sprites and level and game engine and all of that stuff, into one file?

---

### Post by llamabr on 2009-04-15
Probably depends on the game.

In general, it helps to get more comments by having a more explicit subject line.

Probably you could join a game programmers forum, and ask there.

---

### Post by Jakey_TheSnake on 2009-04-15
The answer is they don't. All the things are not in one file. There are the models/images all over the place, then scripts that call up each one as and when it is needed and define its behavior. 

I'd ask at a developers forum.

---

### Post by Paqman on 2009-04-15
You might get one file for an installer (for example a Windows .exe, or a Linux .deb) but the actual game will unpack into a ton of different files. The installer is created right at the end of the development process.

---

### Post by Nepherte on 2009-04-15
Even when you have installed the game, they often use .cab archived files that are loaded when the game requires it.

---

### Post by Murrquan on 2009-04-15
> **Paqman said:**
> You might get one file for an installer (for example a Windows .exe, or a Linux .deb) but the actual game will unpack into a ton of different files. The installer is created right at the end of the development process.

A lot of Linux distros use .rpm files instead. ^.^ Like Fedora and SUSE.

---

