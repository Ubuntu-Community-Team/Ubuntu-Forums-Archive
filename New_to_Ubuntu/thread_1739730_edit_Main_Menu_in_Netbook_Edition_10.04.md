---
title: "edit Main Menu in Netbook Edition 10.04"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by matzemhl on 2011-04-26
Hey everybody,

i used google and the forum search but haven't found anything matching to my case (that makes me think the solution must be simple).

First of all i'm totally new to Linux. I always wanted to try it. At the beginning of the year i bought a new netbook (Lenovo ideapad S10-3) and installed Maverick Meerkat on it. But the performance was really bad and some friends gave me the hint to try lucid lynx. So today i downgraded from 10.10 to 10.04. performance was better but the "main menu" panel on the left side (the one containing favorites, files & folders, office, internet, system...) was bothering me, since it uses one quarter of my netbook screen. i wanted to hide it but haven't found a way.

QUESTION NR. 1:
is there a way to hide the "main menu"-panel? if yes, how?

now comes the stupid part. after searching a little bit, i tried "System -> Main Menu" and was very happy to see a list containing all symbols shown in the side-panel. i was so happy, that i unchecked them all. bad thing about that: now i have a "Main Menu"-Side Panel containing "favorites" and "files & folders" but no "system"-entry (which means i can't even get to the Main Menu options to add all deleted entries). I've tried ALT+F2 with "gmenu-simple-editor" and it shows me the menu list with the entries "Applications" and "System" but nothing happens, when i click on them :(

QUESTION NR. 2:
How do i edit the entries of the Main Menu without reinstalling ubuntu completely?


thanks for helping the n00bs :)
Matze

---

### Post by Paqman on 2011-04-26
> **matzemhl said:**
> 
QUESTION NR. 1:
is there a way to hide the "main menu"-panel? if yes, how?


No, I don't believe there is. You can switch to the default Gnome interface that has small panels at top and bottom if you prefer. Log out and select "Gnome" as the session at the bottom of the log in screen.

> 
QUESTION NR. 2:
How do i edit the entries of the Main Menu without reinstalling ubuntu completely?


Try Alt-F2 and:
```
alacarte
```

If you don't get it fixed, instead of a reinstall, i'd just create a new user account and delete your old one.

---

### Post by matzemhl on 2011-04-26
> **Paqman said:**
> Log out and select "Gnome" as the session at the bottom of the log in screen.


Yes that's exactly what i was looking for.


> **Paqman said:**
> 
Try Alt-F2 and:
```
alacarte
```If you don't get it fixed, instead of a reinstall, i'd just create a new user account and delete your old one.

alacarte was the magic key :)
thank you for your quick support.

---

