---
title: "Updating ATI Drivers?"
date: 2009-06-11
forum: New to Ubuntu
---

### Post by connorh123 on 2009-06-11
Hi.
I'm just wondering how I could update my ATI 7500 driver on an IBM Thinkpad, with Ubuntu. Also would like to know how to update a graphics card. 
Thanks in advanced.

---

### Post by connorh123 on 2009-06-12
Bump.

---

### Post by gradinaruvasile on 2009-06-12
If you are using 9.04 you just stick with the ati drivers that are installed by default. There are newer updates in some PPA but those can be buggy.
It is an old computer, i dont think you can upgrade it... 
I have a dell c640 with the same card as yours and it is perfectly fine for browsing and such (even compiz is working...)

---

### Post by connorh123 on 2009-06-12
Mine does too, but I think it's causing my game to crash.

---

### Post by gradinaruvasile on 2009-06-12
What game it is?

---

### Post by connorh123 on 2009-06-12
Counter-Strike 1.6

---

### Post by markharding557 on 2009-06-12
ati no longer support older gpu's,yours is one,so you are most likly using the open source driver which is not very good on 3d which is why your game struggles.
hardy and intrepid still have ati support jaunty does not

---

### Post by gradinaruvasile on 2009-06-12
Did it work before?
I tried the ati free ubuntu 9.04 drivers with CS 1.6 on wine on a dell 520 with core2 duo at 2.2 ghz/ Ati X1600/256MB DDR3 and it was slow... barely got to 30 fps when alone (on the other hand with a nvidia gf7600 worked flawlessly on an athlon 3200). I dont know how a 7500 could do...

---

### Post by connorh123 on 2009-06-12
In hardy, it worked perfectly. I'm not so sure if it's the drivers now, because I cleaned the dust out of my computer, because I think that's what caused the over-heating. It only froze up once today. So maybe that worked.

---

### Post by connorh123 on 2009-06-12
> **markharding557 said:**
> ati no longer support older gpu's,yours is one,so you are most likly using the open source driver which is not very good on 3d which is why your game struggles.
hardy and intrepid still have ati support jaunty does not

I was thinking about that also, perhaps I should switch back.

---

### Post by gradinaruvasile on 2009-06-12
In this case might be a good idea. Or try 8.10 see if u can install the restrictrd drivers there.

---

### Post by connorh123 on 2009-06-13
I'll look into it.

---

### Post by Mark Phelps on 2009-06-14
> **gradinaruvasile said:**
> In this case might be a good idea. Or try 8.10 see if u can install the restrictrd drivers there.

You can use the ATI restricted driver in Ubuntu releases prior to 9.04 for the following reasons:
1) Catalyst 9.3 includes restricted drivers and supports the older cards
2) Ubuntu versions prior to 9.04 still use the older version of Xorg which is compatible with Catalyst versions prior to 9.4.

---

