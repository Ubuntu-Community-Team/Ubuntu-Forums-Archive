---
title: "re a dell poweredge 800 debain build"
date: 2010-02-14
forum: New to Ubuntu
---

### Post by marlene1950 on 2010-02-14
Can some help me with my dell poweredge 800 - has a debian build.........i am getting this continuous flashing orange light on the front of my pc........i have tried everything i know of but alas nothing seems to work. Anyone have any idea why this is still flashing even though i have removed and replaced all components on the motherboard???
 
Desperate
 
 
Marlene Huff

---

### Post by phillw on 2010-02-14
> **marlene1950 said:**
> Can some help me with my dell poweredge 800 - has a debian build.........i am getting this continuous flashing orange light on the front of my pc........i have tried everything i know of but alas nothing seems to work. Anyone have any idea why this is still flashing even though i have removed and replaced all components on the motherboard???
 
Desperate
 
 
Marlene Huff

Hi and welcome,

There is a section specially for Dell computers. Whilst I'll happily go looking, you may find the information more quickly if you pop over to [http://ubuntuforums.org/forumdisplay.php?f=342](http://ubuntuforums.org/forumdisplay.php?f=342)

Regards,

Phill.

---

### Post by tgalati4 on 2010-02-14
Some poweredge machines store faults in BIOS memory.  If you don't clear those faults, they can trigger the orange blinky.  You need the Dell Open Manage System Administrator for Debian.  Search the web, you can download a debian package and install it using:

sudo dpkg -i omsa-version-whatever.deb

Then open the OMSA webpage, log in with your username and password.  Check the hardware for fault indicators and clear them if necessary.

---

