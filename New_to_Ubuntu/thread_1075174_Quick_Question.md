---
title: "Quick Question"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by sthrnpagan on 2009-02-20
What is the difference between Ubuntu, Kubuntu, and Xubuntu

---

### Post by Grifulkin on 2009-02-20
Desktop Environments, Ubuntu uses GNOME, Kubuntu uses the K-Desktop Environment and Xubuntu uses Xfce which is a stripped down version of GNOME basically, it is for older machines.

---

### Post by sthrnpagan on 2009-02-20
> **Grifulkin said:**
> Desktop Environments, Ubuntu uses GNOME, Kubuntu uses the K-Desktop Environment and Xubuntu uses Xfce which is a stripped down version of GNOME basically, it is for older machines.

are any of the three better than the other two?

---

### Post by Grifulkin on 2009-02-20
It is all about taste, just look up the three desktop environments with google images, or even read about them on there respective websites.  Personally GNOME is used the most but I happen to like the K-Desktop Environment if it didn't give me so much trouble trying to tweak it.  If you are use to windows you might really like KDE but GNOME is very easy to use.

---

### Post by sthrnpagan on 2009-02-20
> **Grifulkin said:**
> It is all about taste, just look up the three desktop environments with google images, or even read about them on there respective websites.  Personally GNOME is used the most but I happen to like the K-Desktop Environment if it didn't give me so much trouble trying to tweak it.  If you are use to windows you might really like KDE but GNOME is very easy to use.

thank you for the help. I have been having trouble installing Ubuntu. Maybe Kubuntu will be better for me.

---

### Post by Grifulkin on 2009-02-20
Maybe but as far as I am concerned KDE is a much prettier desktop than GNOME.  But that is just my opinion.

---

### Post by sthrnpagan on 2009-02-20
> **Grifulkin said:**
> Maybe but as far as I am concerned KDE is a much prettier desktop than GNOME.  But that is just my opinion.

i just want an OS thats not windows. Was avid Windows user and I even like Vista ( strange, i know) but i am tired of my system resources getting eaten up by programs i cant see. So, I have know about Linux for a few years now. Fiddled with RedHat that was on a friends comp a few years back. Found it interesting. But, then I bought my own brand new, high end computer (long story of why i no longer have it) and it came with Vista so i folded. never thought to put Linux on it though. silly me. hehehe. Now here I am trying to become a purely linux user. have been trying for 4 days now. I am nothing if not persistant. I shoudl also show the extent to which i dislike windows. Some people would have just stuck with windows by now. :)

---

### Post by safecracker on 2009-02-20
As mentioned each has their upsides and downsides, KDE is much more all inclusive as to the interfaces it includes, GNOME is a middle ground and XFCE is a lightweight GUI. I recommend trying each over time starting with KDE and than GNOME, after that finally XFCE, doing such should both follow the progression in learning how to efficiently use Linux in general and allow you to gauge what suits you best. 

To install other GUI's just use install xubuntu-desktop or kubuntu-desktop. Before installing them run deborphan -a > filename.txt, this will output a list of packages that have no packages that depend on them. Than when you wish to remove any of the GUI's just remove the corresponding desktop package, any automatically installed components and run the deborphan report again, compare it to your original, anything new was probably installed by the package manager, it happens.

---

