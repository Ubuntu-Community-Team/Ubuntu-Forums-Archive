---
title: "Video Issues"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by dabellator on 2009-01-06
Hey guys, I'm still having video issues.  I decided the Savage8 chipset just wasn't going to work with 8.10, so I picked up a little 32mb MATROX card from free geeks here in Portland, put it in and now my system will boot.  Problem is, it only recognizes the display as 800 x 600.  I really want to learn Ubuntu so giving up is not an option!  What can I do to get my video card and display recognized?

Please, if you need me to give you specs on my system, let me know what commands to use.  Thanks!
-JB

---

### Post by Shazaam on 2009-01-06
System>Administration>Hardware Drivers. Does it give you the option of installing drivers for the ATI card?

---

### Post by dabellator on 2009-01-06
No, unfortunately it doesn't.  That's the place I checked a couple times hoping I could get some information, but it just says "no proprietary drivers are in use on this system," and the window just has the two empty white boxes.  Is there anything I could download?  I just updated the system with the software updates.
-JB

---

### Post by dabellator on 2009-01-06
Ok, try not to shoot me here, but I totally gave you the wrong information!  I put the ATI in a different machine, this one is running a Matrox 32mb MGA G400/450.  I found some linux drivers at their site, but am not sure how to install them.  What command do I run?
-JB

---

### Post by overdrank on 2009-01-06
> **dabellator said:**
> Ok, try not to shoot me here, but I totally gave you the wrong information!  I put the ATI in a different machine, this one is running a Matrox 32mb MGA G400/450.  I found some linux drivers at their site, but am not sure how to install them.  What command do I run?
-JB

Hi and have you tried booting into recovery mode which is usually the second choice from the grub and using the xfix option to correct the graphics issues. After the xfix option you should be given the option to boot normally.

---

### Post by dabellator on 2009-01-06
I like the sound of that, let me give it a try, I'll get back to you.
-JB

---

### Post by dabellator on 2009-01-06
Doesn't seem like I had any luck with the xfix, everything is still the same...
-JB

---

### Post by dabellator on 2009-01-06
I'm running into a new wall, the drivers I downloaded seem to work up to x.org 7.0.0, and it seems like I have 7.4.  Could this be the issue, drivers are no longer compatible?  I need to buy another, newer card?
-JB

---

### Post by overdrank on 2009-01-06
> **dabellator said:**
> I'm running into a new wall, the drivers I downloaded seem to work up to x.org 7.0.0, and it seems like I have 7.4.  Could this be the issue, drivers are no longer compatible?  I need to buy another, newer card?
-JB

I have no experience with the Maxtor graphics but have seen threads in the forums. And users have had success with them on earlier versions of Ubuntu. 
You may try 8.04 Hardy as it has a tool to help with the graphics. 
```
gksu displayconfig-gtk
```

---

### Post by dabellator on 2009-01-07
Thanks Overdrank, that worked.  I'm soaring with the Heron and video is decent enough, thanks again!
-JB

---

