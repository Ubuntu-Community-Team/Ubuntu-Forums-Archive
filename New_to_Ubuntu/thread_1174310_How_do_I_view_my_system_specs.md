---
title: "How do I view my system specs?"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by Seishuku on 2009-05-30
Like which graphics card I have, etc?  I'm trying to find out the specs of an old desktop I recently installed Ubuntu on.

EDIT: I have some info but I need help figuring out what it means.

---

### Post by blackened on 2009-05-30
```
lshw
```

---

### Post by ymra on 2009-05-30
open a terminal and type lspci and that should give you at least some of it.

---

### Post by Seishuku on 2009-05-30
Thank you. :KS

edit: I get overwhelmed by so much information...I still can't figure out which is my graphics card.

---

### Post by UbuntuNerd on 2009-05-30
you can also install system info, in a terminal type this:
```
sudo apt-get install sysinfo
```
 after its installed you can find it under Applications > System Tools

---

### Post by Seishuku on 2009-05-30
> **UbuntuNerd said:**
> you can also install system info, in a terminal type this:
```
sudo apt-get install sysinfo
``` after its installed you can find it under Applications > System Tools

Thank you!!  That was just what I needed!

---

### Post by DeonS on 2009-05-30
You can tell lshw to return only information on your video card with following.

```
lshw -C display
```

or if you would like less information you could do this

```
lshw -short -C display
```

you can create the output as an html page as well with this

```
lshw -C display -html > display.html
```

there is also a graphical front end for lshw that you can install

```
sudo apt-get install lshw-gtk
```

I hope that helps you.

---

### Post by ctrlmd on 2009-05-30
```
**[COLOR=DarkRed][B][SIZE=5]sudo apt-get install hardinfo[/SIZE]**[/COLOR][/B]
```

its similar to *EVEREST Ultimate* on windows 

after installing you can find in in

[SIZE=1][COLOR=Black]**System >> Prefrences >> System Profiler and Benchmark**[/COLOR][/SIZE]

---

### Post by Wiebelhaus on 2009-05-30
My personal favorite , Great for GPU information btw!.


```
Sudo apt-get install sysfinfo
```

Then either type sysinfo or check your system tools under your app menu!

---

### Post by Jimmynemo2 on 2009-05-30
+1 for sysinfo being very nice- just discovered it here and its great. Thanks for the tip guys...

---

### Post by UbuntuNerd on 2009-05-30
over all of them I like system info better is just plain simple of course you can always install "Conky" and monitor you system all the time. :)

---

