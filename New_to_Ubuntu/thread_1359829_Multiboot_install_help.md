---
title: "Multiboot install help"
date: 2009-12-20
forum: New to Ubuntu
---

### Post by Jumper2.0 on 2009-12-20
I am a total newbie to ubuntu... want to give it a try after my friends suggested it :-)

I have a dual boot of windows 98( need it cause' i have some stuff on it that i need - installed applications ) and windows XP on my P4 1.8GHz, 512MB of RAM , an 80 Gb harddisk.

As would seem clear from the specs my pc is quite old. 

Can't seem to install Ubuntu on my pc... tried it a while ago ... gave up on the idea. 

Now I want to try it again. ;)

I have a couple of questions...

1. Do I have to create a partition(Ext3 file system) before booting from the CD? : I mean it works fine till the CD check but then hangs.. :( (and the same Cd was used by my friend on his new Core 2 Duo, it worked fine.)

2. Is it some sort of boot sector problem that i could hope to resolve by trying some boot manager perhaps?

Please help...
Thanks in Advance...

---

### Post by florus on 2009-12-20
You cannot create a linux partition using windows, although you can use windows to shrink its own partition to create unused space which linux can then use.
If you boot from the CD and choose 'try without installing' you can use gparted to see the existing partitions on your drive and work out what your options are.

---

### Post by Jumper2.0 on 2009-12-21
Thanks a lot, am trying it now...
Btw, this message was posted using ubuntu ;):)\\:D/

---

### Post by Jumper2.0 on 2009-12-21
:( i tried all the partition options(excluding overwrite windows XP) and it got stuck at 56%:(

---

### Post by muteXe on 2009-12-21
When your machine was just an 80Gb windows disk, how much free space did you have?

---

### Post by candtalan on 2009-12-21
> **Jumper2.0 said:**
> Thanks a lot, am trying it now...
Btw, this message was posted using ubuntu ;):)\\:D/

Welcome! 
Good to hear that the live CD runs ok. How much RAM memory does your machine have? If you have a lot you can install ok by using the icon on the desktop, however, I usually use the Install option from the Live CD boot up menu, it takes less RAM. 

It is possible that your machine is marginal and does not have quite enough ram to complete the graphical method install quickly.

Another option for lower resource PCs is the so called 'alternate CD' which is install only, not live CD.

If your attempted install processes have been incomplete then beware if they have created any partitions already on your hard drive. You could examine this, using the live CD which does work in your PC (gparted partition editor). 

Avoid more install attempts until you have verified that the partitions are still as you expect - which sounds like just a couple of partitions one for win98 and the other for winXP.

If you arrange that the rest of the hard rive is unused, no partitions at all, just space, then ubuntu can be told to use the option 
'Use the largest unused space on the drive' which I find to be a very convenient option.

hth

---

