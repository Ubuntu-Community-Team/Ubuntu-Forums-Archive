---
title: "Wining over Wine, after compling what now?"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by jonpon on 2010-02-09
Hi I'm having trouble installing Wine
I tried the synaptic way but the version didn't work, so I download the 1.0.1 version

then,
```
jonpon@jonpon-laptop:~$ cd wine-1.0.1

jonpon@jonpon-laptop:~$ ./configure

jonpon@jonpon-laptop:~$ make depend && make
 
```
But what now?

---

### Post by warfacegod on 2010-02-09
Is it installed? If so, download the Windows program you want and double click it. You may have to right click it and select Open With...then select Wine.

---

### Post by anaconda on 2010-02-09
why do you want to install so OLD version of wine. You should get a new one. it will work a LOT better. I am currently using version 1.1.37 I think even office2007 wont work with 1.0.1

But. before running windows programs you should open a terminal and type:
winecfg
It will open a wine configuration editor, and it will create the virtual c-drive on your home directory (a hidden folder named .wine) You can just close the window after it starts. the .wine folder will be created, and that is waht you wanted.

And I would definitely prefer installing wine from a repository over compiling it myself:

Here is the offical wine repository for hardy heron. If you have a newer version of ubuntu just replace the hardy with your version eg. jaunty...

#WineHQ - Ubuntu 8.04 "Hardy Heron"
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) hardy main

or for easier instructions for adding the wine repository:
[http://www.winehq.org/download/deb](http://www.winehq.org/download/deb)

---

### Post by jonpon on 2010-02-09
I was using the a newer version (the one in the repos) but it didn't work. would just crash when I opened anything or when I pressed any of the buttons in winecfg, as root it worked a bit better, only crashed by openning anything.

---

