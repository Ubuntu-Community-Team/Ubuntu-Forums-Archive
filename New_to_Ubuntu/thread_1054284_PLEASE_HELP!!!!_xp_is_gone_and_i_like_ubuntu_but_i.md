---
title: "PLEASE HELP!!!! xp is gone and i like ubuntu but i screwed up partitions"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by highhippyfun on 2009-01-29
HI Dylan here,

         I heard about ubuntu and i thought instantly Wow this is a great os but when i was installing i completely messed up my partitions and now my hard drive is only ubuntu and now it wont even read me xp boot disc.
I have already changed bios to make it so disc goes first but it starts and then disc stops making sound and then ubuntu loads so i dont know what to do i dont know how to use this os even though i think it is awesome i have finals coming up. I Am going to have ubuntu in the future but for now can someone help me please??? 

WOULD REFORMATTING MY HARD DRIVE FIX THE PROB???? 

XP IS GONE!!!!!!!!!!!!

---

### Post by JustANewb on 2009-01-29
Reformatting would definitely fix your problem.  Or just buy a new harddrive and dual boot from two different disks.  That is what I do and it is great!

---

### Post by Dougie187 on 2009-01-29
How is reformatting going to help him? Eventually he will have to reformat to reinstall windows, but if he can't even boot to the windows cd then reformatting is just going to make ubuntu not usable either.

Can you boot to the ubuntu live cd?

---

### Post by gashcr on 2009-01-29
Yes, it will do the trick, however it seems to me pretty weird that your XP disc is not booting, perhaps there's also a problem with the disc integrity, in any case, I wish that was not the case, but just in case I'd recommend you look for another XP disc right away. 

Regarding Ubuntu, once you spend a couple hours with it you'll be used, or you can play with it a while with the live cd. Another good option I would highly recommend is to use the wubi installer from windows, it'a a pretty safe option to learn the system without compromising your workflow :D

Good luck!

---

### Post by poltiser on 2009-01-29
Do you have XP in grub?
How did you partition your drive?
Is it a mbr problem?
In short what exactly happened?

---

### Post by highhippyfun on 2009-01-29
OK sorry i am really nubby but i might want to just keep ubuntu but in order to keep it i would need the links for a good repartitioner cause it says i can only download 1.5gb more and i would also need Internet explorer for school.

Also a guide for how to use would be nice and if anyone could explain exactly how to install stuff i already have wine but i think i got lucky on that one.

PLEASE AND THANK YOU VERY MUCH YOU GUYS ARE AWESOME!!!!

                     DYLAN G



OH and for what exactly happened i used live cd to install ubuntu then decided i better not when i was a partition part and quit then reboot xp was gone and i had no os so i installed ubuntu. and now since im on a laptop i cant make a floppy and for some reason even though i have my bois set to load cd/dvd drive first it ignores it.

---

### Post by HittingSmoke on 2009-01-29
> **highhippyfun said:**
> OK sorry i am really nubby but i might want to just keep ubuntu but in order to keep it i would need the links for a good repartitioner cause it says i can only download 1.5gb more and i would also need Internet explorer for school.

Also a guide for how to use would be nice and if anyone could explain exactly how to install stuff i already have wine but i think i got lucky on that one.

PLEASE AND THANK YOU VERY MUCH YOU GUYS ARE AWESOME!!!!

                     DYLAN G



OH and for what exactly happened i used live cd to install ubuntu then decided i better not when i was a partition part and quit then reboot xp was gone and i had no os so i installed ubuntu. and now since im on a laptop i cant make a floppy and for some reason even though i have my bois set to load cd/dvd drive first it ignores it.

As for a partitioner [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

If your Ubuntu disk still booted than it's probably the XP disc that's the problem. A Ubuntu install wont screw up your drive boot order, that's all dependant on your BIOS settings.

If you post the output of
> sudo fdisk -l

we can tell you if there's a chance your Windows partition is still in tact.

---

