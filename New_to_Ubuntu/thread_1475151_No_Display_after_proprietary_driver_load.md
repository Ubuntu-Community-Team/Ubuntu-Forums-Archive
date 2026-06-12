---
title: "No Display after proprietary driver load"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by thaumielx72 on 2010-05-06
OK, I'm still a newb of sorts with Linux but I honestly didn't see this coming.

To be brief:  I have a new i7 (ZT from Sears) 920.  It allows for more than one graphics cards to be loaded on the motherboard.  It comes with an ATI HD 4650.  I still have my old Nvidia GeForce 8600 and slipped it in to test this ability to use multiple cards.

Again, briefly: DECENT!

I thought I would try it in my Ububtu and Kubuntu partitons.  There are both 10.4 Lucid as I like to mess around with Beta's and I usually dont have too much important data in my Linux partitions in case I need to re-load.

(I like to experiment too much - and I like how responsive and hands-on (K)Ubuntu is so I actually use them more than my Windows partition.  Keeps me out of trouble, usually)

Anyway, all was well with Ubuntu and Kubuntu until I decided to load the proprietary Nvidia driver through System - Administration - Hardware Drivers.  Rebooting into either partition results in a blank screen with no error messages.  I tried using the Ubuntu CD - I loaded the Ubuntu partiton to change Xorg.config to a copy of the xorg.conf.failsafe but that made no difference.

The monitor is attached to the (original) ATI board connection but switching to the second card (NVidia) makes no difference.

If someone can save me the trouble of having to reload both my Ubuntu and Kubuntu partitons I would really be grateful.  It seems (to me) like it shouldn't be all that much of a problem, but, yeah, what do I know?

Thanx in advance.  :guitar:

---

### Post by madjr on 2010-05-06
well a system rollback by default is in the works for linux (btrfs):

[http://www.phoronix.com/scan.php?page=article&item=fedora_13_btrfs&num=1](http://www.phoronix.com/scan.php?page=article&item=fedora_13_btrfs&num=1)

but wont be out for a few versions

unless you created a system backup yourself, then...

for now the live-cd is your friend

you can either reinstall (the easy way) or follow a set of commands to go back to your old drivers

i don't have the instructions with me, last time i did something similar was few years back from

[http://ubuntuguide.org/](http://ubuntuguide.org/)

or some other place, if i find them i'll come back

---

### Post by arpanaut on 2010-05-06
While your MB may support dual vid. cards, I highly doubt you could use one ATI one nVidia.

Check your MB documentation.... also your board has ATI Crossfire video tech. which would require ATI drivers, which would probably screw up using nVidia drivers

I don't know for sure but I think you are "barking up the wrong tree" trying to use cross branded cards.

Betcha 2 ATI cards works!


[http://ati.amd.com/technology/crossfire/charts.html](http://ati.amd.com/technology/crossfire/charts.html)

---

### Post by the.phantom on 2010-05-06
i just did a fresh install
i had limited graphics and the hardware driver was 98 for my old nevidia card
well on re3boot i had a garbage screen, and the more i tried
the worse it got, so i found it easer to just reload it

since it was a fresh install the only thing i really had to do was re configure firefox and t-bird.

kinda a bummer that you have "to take a leap of faith" on installing the drivers.  ;-(

you can check it out with a live cd, but can't install the driver unless you install, then it is too late if something goes wrong ;-(

---

### Post by thaumielx72 on 2010-05-06
> **arpanaut said:**
> While your MB may support dual vid. cards, I highly doubt you could use one ATI one nVidia.

Check your MB documentation.... also your board has ATI Crossfire video tech. which would require ATI drivers, which would probably screw up using nVidia drivers

I don't know for sure but I think you are "barking up the wrong tree" trying to use cross branded cards.

Betcha 2 ATI cards works!

I should have been more plain:  The dual card (one from ATI, one from Nvidia) did not "work" in W7, they are SWEET together.  Or, as we used to say when I was a kid: Cool, Man!

In more adult terms: they can both rock a higher overclocking with each other there for support and make some intense graphic games set at ultra high resolution truly dance.:popcorn:

---

