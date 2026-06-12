---
title: "weird firefox problems"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by 13b on 2009-04-19
all of a sudden one day last week, firefox started acting funny.

the buttons in the upper right hand corner to maximize/minimize/close the window are gone and when firefox is open, i can't see the bottom bar that contains other windows i have open.  so i can't do anything but use firefox.

to close firefox, i actually have to file/close it, because i can't do it any other way and i can't minimize it.

there has to be an extremely simple solution to this.

---

### Post by unutbu on 2009-04-19
What happens when you press F11?

---

### Post by 13b on 2009-04-19
it's a temporary fix, but it reverts right back to the way it was when i open it again.

i also can't see the top bar when firefox is open, whatever it's called.  the one with all of my pull-down menus.

basically, when firefox is open, it's the only thing i can see/operate on.

---

### Post by ddrichardson on 2009-04-19
From a terminal```
firefox -P
```Will let you mess around with your profiles, create a new one and if the problem persists its something non-profile.

Incedently, does this happen on every web page?

---

### Post by 13b on 2009-04-19
yep, as long as firefox is open, it'll do this.

---

### Post by radar2020 on 2009-04-19
If you have compizconfig installed try this:  

Exit Firefox.
	
SYSTEM>PREFERENCES>COMPIZCONFIGSETTINGMGR>UTILITY>CLICK ON THE WORD WORKAROUNDS which brings up an new screen and deselect the first box LEGACY FULL SCREEN SUPPORT. Exit

Open Firefox.

---

### Post by 13b on 2009-04-19
creating a new profile seems to have worked for now, but i will keep that in mind.

---

