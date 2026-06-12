---
title: "installing ubuntu on HD removed from PC"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by marvellous_matt on 2008-12-16
hi, i cant get my old compaq pentium III to boot from the cd, it is first in the boot order, Ive put a new dvd drive in, increased the memory (512 is the max i think) still no luck. Ive got another second had HD, I would like to install ubuntu onto that directly then put it in the PC. I currently have it installed in a external case and there is plenty of space. can i do this from my Mac?
thanks for any help you can provide.
cheers from Matt

---

### Post by jbrown96 on 2008-12-16
Is the drive connected properly. I would imagine on a system that old that it is using an IDE connection, right? Did you set the jumper properly?

I'm not sure about the Mac part, but I think that it is difficult to boot from a disk because they don't have a standard BIOS. I really don't know though

---

### Post by marvellous_matt on 2008-12-16
sorry I dont know what IDE is or jumper is. 
in BIOS the boot order is cd drive, a, c, then internet. unfortunately with the original HD it keeps booting windows from the HD. I cant get it to boot with the seccond hand HD plugged in, Im pritty sure i have it connected ok, it starts, I can access BIOS, then it starts and just hangs, freezes with a cursor on the screen. i dont know what PC the HD came from, it does have windows programs on it.

---

### Post by jerome1232 on 2008-12-16
IDE is the type of connection it uses to connect to the motherboard.


There should be a wide 40 pin ribbon going from the cdrom to a slot on the motherboard.

Is the HDD on the same ribbon as the CDROM or are they on seperate ribbons?

Also on the backs of the HDD's and the CDROM there will be 6-8 pins with or without a jumper (just a small piece of plastic with a piece of metal in it, it shorts the pins) and drawn on the cdrom/hdd there should be a chart that tells you how to set them to master, slave, or cable select. Can you find all that and determine what the cdrom and HDD's are set to?

---

### Post by marvellous_matt on 2008-12-16
I*s the HDD on the same ribbon as the CDROM or are they on seperate ribbons?*
**seperate ribbons**

*Also on the backs of the HDD's and the CDROM there will be 6-8 pins with or without a jumper (just a small piece of plastic with a piece of metal in it, it shorts the pins) and drawn on the cdrom/hdd there should be a chart that tells you how to set them to master, slave, or cable select. Can you find all that and determine what the cdrom and HDD's are set to?[/QUOTE]*

old HD jumper is J48, , cable select on,(pins 7&8 shorted) 
newish HD says J8 Jumper settings,  diagram shows pins 1&2 shorted

old cdrom has cable select shorted
new dvdrom has master shorted.

should I change the newish hardware to the same settings as the ones Im replacing. think I should. 
HHmmm, there is a rather large void in my knowledge base!

cheers from Matt

---

### Post by jerome1232 on 2008-12-16
Okay well since they are both on separate ribbons either Master or Cable Select will work. Cable Select automatically determines if the drive needs master or slave. You'll want them both on the last connector on the ribbon and set to either master or cable select.

```

[COLOR="Lime"]motherboard [/COLOR]           [COLOR="Red"]slave[/COLOR]      [COLOR="Blue"]master[/COLOR]
           [COLOR="Lime"]|[/COLOR]_____________[COLOR="Red"]|[/COLOR]_______[COLOR="Blue"]|[/COLOR]
```


If that doesn't help then make sure the cd has been burnt as an image not as a data cd. When you insert it in to the mac does it have a single file on the cd or several folders? If it's a single file then it was burnt as a data cd and won't work, here's a how-to for burning images [https://wiki.ubuntu.com/BurningIsoHowto](https://wiki.ubuntu.com/BurningIsoHowto) ; If you have multiple folders then it was burnt correctly and I can't be of any further help.

---

