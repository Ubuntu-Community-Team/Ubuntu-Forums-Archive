---
title: "Does it matter where I save a program?"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by listerdl on 2009-04-23
Hi, I have recently downloaded and am about to install a .bin program and I am being asked by Ubuntu where I would like to save the program....does it matter? I think that the answer will be no it doesnt - but just wondered if there is a 'sensible' place to save a program that will be used quite a lot...

Thanks!

---

### Post by RedSingularity on 2009-04-23
Best place is /usr/share for custom software.

---

### Post by steve101101 on 2009-04-23
+1

and also usually the default place that it recommends makes sense aswell.

---

### Post by Thelasko on 2009-04-23
Just to be sure you are doing everything correctly, [please read this.]("http://www.psychocats.net/ubuntu/installingsoftware")

---

### Post by RedSingularity on 2009-04-23
+2

Thats what i always do.......let it choose.

---

### Post by benj1 on 2009-04-23
it depends what it is. downloading is not the same as installing 
i would suggest downloading to somewhere convienient, the Desktop?
if its a .deb file double click on it and an installer will launch.
if its a tar.gz or something extract it and see whats in side, most apps with have a README, which will probably just tell you to ./configure, make, install which will sort out installation for you.
if its just a simple script without an installer then either in the terminal.
cd to the correct directory and
```
sudo cp app /usr/bin 
```
or for a graphical way type
```
gksu nautilus
```
in a terminal which will open up the nautilus file manager and allow you t copy it across to /usr/bin

---

### Post by Simian Man on 2009-04-23
Best place for custom software is in /usr/local/bin.  Then it will not be overwritten in updates.

---

