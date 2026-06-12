---
title: "cant enable visual effects"
date: 2009-06-25
forum: New to Ubuntu
---

### Post by amir aljaberi on 2009-06-25
hi 
i cant enable visual effect it gave me ' you could not enable visual effect'
my laptop graphic: [FONT=Arial]VIA        Chrome9 HC IGP

what should i do ?:(
[/FONT]

---

### Post by halitech on 2009-06-25
there is info here on that chip

[http://ubuntuforums.org/showthread.php?t=967198&highlight=Chrome9](http://ubuntuforums.org/showthread.php?t=967198&highlight=Chrome9)

---

### Post by amir aljaberi on 2009-06-25
do u have another idea ?
thx

---

### Post by halitech on 2009-06-25
get an Nvidia card?

---

### Post by amir aljaberi on 2009-06-25
is there anyway to install this chip ?

---

### Post by 3rdalbum on 2009-06-25
You got jipped when you bought that laptop - VIA graphics are not very good overall, and VIA is extremely lazy about writing drivers for Linux. From what I've just read, you're lucky to have 2D graphics support.

Compiz is not important. It's mostly just some useless eye candy. You may have some success with Ubuntu 9.10 when it comes out, or the compositor in KDE 4 might work - it has many similar effects to Compiz (you'd need to run KDE 4 though).

---

### Post by amir aljaberi on 2009-06-25
> **3rdalbum said:**
> You got jipped when you bought that laptop - VIA graphics are not very good overall, and VIA is extremely lazy about writing drivers for Linux. From what I've just read, you're lucky to have 2D graphics support.

Compiz is not important. It's mostly just some useless eye candy. You may have some success with Ubuntu 9.10 when it comes out, or the compositor in KDE 4 might work - it has many similar effects to Compiz (you'd need to run KDE 4 though).

so there is no way to install chrome video card :(:(
bad luck:(

thx for ur help

---

### Post by waspbr on 2009-06-25
fraid not, tho you can improve the look of your desktop by enabling the metacity composite manager. You can do this so you can use more complex textures, this enbles you to use docks and window shadowing. 

anywho,if you are interested, do the following, press alt + F2 then paste this :

```
gconf-editor
```

then go to apps >> metacity >> general 

tick the box that says "compositing manager"

close the window

gl

---

### Post by amir aljaberi on 2009-06-25
> **waspbr said:**
> fraid not, tho you can improve the look of your desktop by enabling the metacity composite manager. You can do this so you can use more complex textures, this enbles you to use docks and window shadowing. 

anywho,if you are interested, do the following, press alt + F2 then paste this :

```
gconf-editor
```then go to apps >> metacity >> general 

tick the box that says "compositing manager"

close the window

gl

thx i tried it. however i was interesting in visual effects :(
also why ubuntu is slow and lagging ? is this related with video card

---

### Post by amir aljaberi on 2009-06-25
hi 
if i install wine, can i after that install driver of via chrome9 from original cd ?

thx

---

### Post by halitech on 2009-06-28
unfortunately there is no way of using windows video drivers like we can with NDSIWrapper and windows wireless network drivers.

---

### Post by DPJ93 on 2009-06-28
What if you first update all the software in Ubuntu, and then go to System - Administration - Hardware drivers? Now you might see the name of your graphic card and will be able to activate them simply by pressing "Activate" while the card is marked. Notice that this might take some time.

If it doesn't work, sorry in advance.. :)

---

