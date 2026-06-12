---
title: "electricsheep not working"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by werecatomega on 2010-02-20
i've downloaded the electricsheep screensaver from [http://community.electricsheep.org/](http://community.electricsheep.org/) and i've followed the instructions. after i selected it for my screensaver but it doesn't work!

it works when i run electricsheep in the terminal or using the alt-f2 and when i preview it in the gnome-screensaver but not when my screensaver actually starts!

can somebody help?

---

### Post by RedSingularity on 2010-02-20
Look at this package in synaptic.......it may contain what your looking for. 

xscreensaver-gl-extra

---

### Post by werecatomega on 2010-02-21
i appear to have it already installed (probably when i tried out xscreensaver)
i used the command 
```
sudo apt-get install xscreensaver-gl-extra 

```

thanks for the suggestion though

---

### Post by mighty_falcon on 2010-02-21
I had a similiar problem and here is what i did to fix it:

1. first try typing electricsheep --debug 1 in the terminal. At this point I was getting failed to connect to the server, and from a bit of googling it seems that it was an outdated version.

2. Uninstall the one you have installed and get the the latest one, just head over to [http://community.electricsheep.org/node/51](http://community.electricsheep.org/node/51) and grab the makesheep.sh and execute that and you should be good to go. I would suggest to again run it from the terminal the first time as it takes a bit to download all the files and this way you can see whats going on.

---

### Post by werecatomega on 2010-02-21
thanks for the suggestion, but i installed it from there and using it through the terminal works.

the only thing that doesn't work is, for example, if i press control+alt+L when it is selected for the screensaver, it is just a blank screen

---

### Post by werecatomega on 2010-02-21
omg it works:D

i didn't do anything and my screensaver worked! sorry for brothering you guys

---

