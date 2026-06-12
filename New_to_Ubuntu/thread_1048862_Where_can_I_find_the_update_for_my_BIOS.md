---
title: "Where can I find the update for my BIOS?"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by pluckypigeon on 2009-01-23
I'm trying to find an upgrade for my firmware but so far it has been unsuccessful.

```
BIOS Information
        Vendor: American Megatrends Inc.
        Version: JH.01.04
        Release Date: 12/18/2001
        Address: 0xF0000
        Runtime Size: 64 kB
        ROM Size: 512 kB

System Information
        Manufacturer: Hewlett-Packard
        Product Name: Compaq EVO
        Version: D310
        Serial Number: FR24910689
        UUID: 6C700E21-0616-11D7-980C-7FE73ED4FF16
        Wake-up Type: Other

Base Board Information
        Manufacturer: Hewlett-Packard
        Product Name: HP System Board
        Version: A01
        Serial Number: S631KLI005KSY02257
```

Any help will be really appreciated.

---

### Post by taurus on 2009-01-23
Check with HP.  Type in the model of your machine and see if there is a latest firmware.  Just be real careful when you update the BIOS because if the power goes out or something goes on, you would have an expensive paperweight.

---

### Post by halitech on 2009-01-23
there are different models of the D310, go here and select the proper one and you will get the BIOS download link.

[http://h10025.www1.hp.com/ewfrf/wc/swPfinder?lc=en&dlc=en&cc=us&docname=c00007682&tool=softwareCategory&query=evo](http://h10025.www1.hp.com/ewfrf/wc/swPfinder?lc=en&dlc=en&cc=us&docname=c00007682&tool=softwareCategory&query=evo)

---

### Post by pluckypigeon on 2009-01-23
> **taurus said:**
> Check with HP.  Type in the model of your machine and see if there is a latest firmware.  Just be real careful when you update the BIOS because if the power goes out or something goes on, you would have an expensive paperweight.

> **halitech said:**
> there are different models of the D310, go here and select the proper one and you will get the BIOS download link.

[http://h10025.www1.hp.com/ewfrf/wc/swPfinder?lc=en&dlc=en&cc=us&docname=c00007682&tool=softwareCategory&query=evo](http://h10025.www1.hp.com/ewfrf/wc/swPfinder?lc=en&dlc=en&cc=us&docname=c00007682&tool=softwareCategory&query=evo)

Thanks for the info guys

---

### Post by pluckypigeon on 2009-01-23
Do you know if I can get a linux version?

---

### Post by halitech on 2009-01-23
I have my doubts. chances are you will have to create the floppies (I'm guessing) on a windows based machine to do the update.

---

### Post by pluckypigeon on 2009-01-23
> **halitech said:**
> I have my doubts. chances are you will have to create the floppies (I'm guessing) on a windows based machine to do the update.

Ok. Thanks anywho. It's not that important anyway. 

I don't have windows or a floppy drive :(

Maybe I can do it some other time.

I only wanted to update it so I could have the graphics chip memory allocation option in BIOS.

Thanks again.

---

### Post by halitech on 2009-01-23
you could try downloading it and running it in WINE to see if it will create the floppies on your ubuntu machine. not sure if it will work but worth a shot

---

### Post by pluckypigeon on 2009-01-23
> **halitech said:**
> you could try downloading it and running it in WINE to see if it will create the floppies on your ubuntu machine. not sure if it will work but worth a shot

I did already try opening it in wine... slightly reluctantly.

I got an error message.."The Driver Failed to Load"

I'm not going to delve any deeper in to it using wine.

---

### Post by 73ckn797 on 2009-01-24
If there are any updated BIOS that can be flashed, you would want to see their info about what changes have been made to the BIOS. If there is nothing that would really benefit your use then I would not bother with it.

I flashed my BIOS recently. I do not have a floppy drive but found, from within the BIOS flash utility, that I could designate using a USB flash drive instead of a floppy.

---

