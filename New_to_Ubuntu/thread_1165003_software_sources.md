---
title: "software sources??"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by faraz_k86 on 2009-05-20
Ive used gnome till now and loved the synaptic installer in it. 

But im on a friends computer here and have installed kubuntu for him and am using it for the first time.. I tried installing apps into it such as wine and gstreamer plugins.. but the adept installer sucks.. I checked all the software sources but still i get veryu few apps listed..

How do i get the complete debian list?? or better still how can i use synaptic in kubuntu??

I did search for this before posting, found this one here: [http://ubuntuforums.org/showthread.php?t=1146206&highlight=adept+installer](http://ubuntuforums.org/showthread.php?t=1146206&highlight=adept+installer) but the guys mentions a kpackagekit for 9.04.. but im using 8.10

i dont have the time or bandwidth to update to 9.04 niw.

Help please

---

### Post by s.fox on 2009-05-20
Hi,

Try System/Adept.

Adept is basically the same thing as synaptic but for kubuntu. 

Synaptic will still work if you want it, just do: 

```

sudo apt-get install synaptic (I think)
```

Hope this helps.

-Ash R

---

### Post by amingv on 2009-05-20
It's as easy as

```
sudo aptitude install synaptic
```

or installing it from Adept Package Manager (which, however choppy, should be showing you the complete "debian list", have you enabled all extra repositories/updated the package lists?)

---

### Post by DLG102282 on 2009-05-20
If all the packages aren't listed type in sudo apt-get update in a terminal to update the repos. Now they should all be there.

---

### Post by faraz_k86 on 2009-05-20
k thx guys.

i did all that, i even installed synaptic, but even then searching for wine gives me no results, i even added wines source ```
deb http://wine.budgetdedicated.com/apt intrepid main #WineHQ - Ubuntu 8.10 "Intrepid Ibex"
```.

ille evtually download and istall it via terminal or getdeb.net but im just asking why isnt it working this way?

---

