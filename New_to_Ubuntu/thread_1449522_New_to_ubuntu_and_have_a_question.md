---
title: "New to ubuntu and have a question"
date: 2010-04-07
forum: New to Ubuntu
---

### Post by v.capp on 2010-04-07
I am new to ubuntu, actually just started using it today. I had a friend who is an avid lover of ubuntu help me, and we both got stuck when it came to one application. My husband plays on Full Tilt Poker.Net, which is a Windows based app. I installed wine 1.2 and playonubuntu (or something like that) in my games, but the fonts still aren't right. If someone knows how I can fix this, I would really appreciate it.
Thanks in advance. 

V.capp

---

### Post by undecim on 2010-04-08
Do you have the msttcorefonts package installed?

---

### Post by -humanaut- on 2010-04-08
open a terminal &
[C] sudo apt-get install ubuntu-restricted-extras [C]
That will install the Microsoft Core fonts for you

---

### Post by lisati on 2010-04-08
> **-humanaut- said:**
> open a terminal &
```
 sudo apt-get install ubuntu-restricted-extras 
```
That will install the Microsoft Core fonts for you

Tags fixed. (It's [noparse]```
 and 
```[/noparse])

---

### Post by -humanaut- on 2010-04-08
oh yeah, thanks man

---

### Post by sandyd on 2010-04-08
im on my cell, but download winetricks, run it, and install the "allfonts" option and "fontsmooth-rgb"

---

### Post by sandyd on 2010-04-08
> **-humanaut- said:**
> open a terminal &
[C] sudo apt-get install ubuntu-restricted-extras [C]
That will install the Microsoft Core fonts for you

humanaut, the ttf-mscorefonts package that ubuntu-restricted-extras is only for ubuntu, but not wine. a program called winetricks can download the necessary fonts for the program.

---

### Post by -humanaut- on 2010-04-08
oh i see I didn't realize it wouldn't apply to wine thanks

---

