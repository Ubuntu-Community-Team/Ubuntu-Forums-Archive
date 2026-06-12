---
title: "video card info please"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by the.phantom on 2010-07-05
i have a friend and we installed 10.4 on it, it said use the hardware driver 96 for nvidia
well that cause a big mess and a black screen
so with the linux default drivers we can almost get the video display good
 he has a wide screen, some web pages do not display the same way as firefox in windows)
so i am wondering 

if he got a newer video card ( say178) series 
i can't find a list on what the card model number is for a nvidia card that is made in this decade
can we just swap it out and bios will report it and can we easly configure it for 10.4?

and if anyone knows a inexpensive but good nvidia card ( not into graphics, just web and e-mail mostly) he has a nvidia g force 2 now
just a 2 gig amd with 1 gig of memory from 2001

lots of questions, but i do not want to get a card and have a nightmare and have the same problem ;-D

---

### Post by Frogs Hair on 2010-07-05
Hi phantom,

Can you supply some more information about your friends computer . The brand , age , and model would be helpful in locating a compatible video card.

---

### Post by the.phantom on 2010-07-05
just need a list of what model nvidia card can use higher graphic driver than the last on the list, something a higher number and  a nvidia number

not a oem 
has pci and a agp slot
2.2 gig amd duron and one meg of ddr memory (400mhz i think)
it is MSI  kt3 ultra 2 MOBO
made using good parts (name brands not top of the line but good)
in 2005.,was fast but now so much has changed in design

has xp and 10.4 on it
bout a 120 gig hard drive and one drive used for backup now ( ghost on xp)
he likes most of ubuntu ( speed, different names but equivalent programs)
 but that old g force just won't work

( i have a older box too and the 98 (recommended driver) did the same to me but i have a 17 in display so use the default drivers and is ok for me  g force 2

---

### Post by sandyd on 2010-07-05
> **the.phantom said:**
> just need a list of what model nvidia card can use higher graphic driver than the last on the list, something a higher number and  a nvidia number

not a oem 
has pci and a agp slot
2.2 gig amd duron and one meg of ddr memory (400mhz i think)
it is MSI  kt3 ultra 2 MOBO
made using good parts (name brands not top of the line but good)
in 2005.,was fast but now so much has changed in design

has xp and 10.4 on it
bout a 120 gig hard drive and one drive used for backup now ( ghost on xp)
he likes most of ubuntu ( speed, different names but equivalent programs)
 but that old g force just won't work

( i have a older box too and the 98 (recommended driver) did the same to me but i have a 17 in display so use the default drivers and is ok for me  g force 2
Its all on nvidia.com. Go to the driver's section.

---

### Post by Frogs Hair on 2010-07-05
Nividia 6 series and up use the the current 256.35 driver. It is possible to get some nice 8 series cards at a good price.

---

### Post by the.phantom on 2010-07-05
that's great
now i can do the system/admin drivers and it will install the correct driver?
my fear is i have to install drivers, then will have to do it each time a kernal change .

now i could leave the system set up using xorg drivers, swap out the card
boot the system and the bios will tell ubuntu the card so when it comes up i can get install the driver ?
or is it going to take something else to tell Ubuntu of a card change

what about ati i did find a list that have the drivers available in ubuntu like nvidia,any drawbacks?

thanks for the help!

---

### Post by sandyd on 2010-07-05
> **the.phantom said:**
> that's great
now i can do the system/admin drivers and it will install the correct driver?
my fear is i have to install drivers, then will have to do it each time a kernal change .
[B]If you install it from system -> administration -> hardware drivers, the drivers will be recompiled each time you do a firmware change

[/B] now i could leave the system set up using xorg drivers, swap out the card
boot the system and the bios will tell ubuntu the card so when it comes up i can get install the driver ?
or is it going to take something else to tell Ubuntu of a card change.
**If the card is still the same brand and is still supported by the driver, there will be no problem.**

what about ati i did find a list that have the drivers available in ubuntu like nvidia,any drawbacks?
**ATI propriety drivers are currently crap. If you have a choice, don't use one with ubuntu unless your going for using the open-source radeon drivers.**
thanks for the help!.

---

