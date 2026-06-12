---
title: "Crossover and Steam."
date: 2009-02-08
forum: New to Ubuntu
---

### Post by nibbler491 on 2009-02-08
I installed Steam using Crossover, and everything went well with the install, but when I finally tried to run the program, the window flashed onto the screen, then flashed off. I could see the steam bar at the bottom of the screen, but if I tried to click on it or unminimize it wouldn't pop up. I tried restarting and reinstalling, but to no avail. Any help?

---

### Post by nibbler491 on 2009-02-08
bump

---

### Post by nibbler491 on 2009-02-08
bump

---

### Post by nibbler491 on 2009-02-08
Any help at all?

---

### Post by nibbler491 on 2009-02-08
:(

---

### Post by Tony Flury on 2009-02-08
Try running Steam using the terminal - and see if any errors are generated. 

You should ideally leave a post at least 24 hours before bumping, most people have other jobs and real lives, and they don't get paid to help here, they help if they can, where they can.

---

### Post by nibbler491 on 2009-02-08
I completely understand that, and I'll try what you said and post the results, but I simply bumped this topic everytime it fell of the front page, as I know people rarely search through the later pages which would mean my question is much less likely to get answered.

---

### Post by nibbler491 on 2009-02-08
I can't run Steam in terminal(or rather, I don't know how), because it's not a regular linux program, so I can't use the normal commands.

---

### Post by nibbler491 on 2009-02-08
bump

---

### Post by Tony Flury on 2009-02-09
Ok - you must have a menu entry for steam - if you inspect that menu Entry (use System -> Preferences -> Main Menu to look at all your menu Entries) you will find the command that is run when you choose the Steam Menu Entry.

That is what you run in the terminal - for me it is :
```

env WINEPREFIX="/home/tony/.wine" wine "C:\Program Files\Steam\Steam.exe"

```

yours will be similar I guess.

BTW : there is no reason to bump when something goes off the main page - a lot of people will go back several pages to help people, when they have the time. Imagine if everyone bumped when their items dropped off the main page - we would rapidly get to a point where stuff fell of the first page within minutes - pushed off by loads of bumps.

---

### Post by rockstone on 2009-03-26
I also installed steam using crossover and am having the same problem. Anyone know the cause/how to fix it?

---

