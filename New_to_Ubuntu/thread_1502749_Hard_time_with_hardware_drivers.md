---
title: "Hard time with hardware drivers"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by marshman998 on 2010-06-06
Hey, I just installed Ubuntu for the first time on my new laptop as a partition. I allocated 250 gigs to it, but I can't seem to get the hardware drivers working. Specifically, none are showing up when I go to System/Administration/Hardware Drivers. These are my specs:

Toshiba Satellite A505 series, M330
500 gig hd
4 gig ram
i3 processor

Not sure what vid card it came with, how can I check this? And let me know if you have any suggestions.
Thanks!

---

### Post by crowderd on 2010-06-06
What driver is not working. Ideally you do not want anything to show up in the Hardware Drivers.
         You can check your video card by putting this in a terminal:
          lspci | grep VGA

---

### Post by ashwinhgtx on 2010-06-06
May be you don't need any proprietary drivers. Is everything working for you? Compiz and its myriad of special effects, sound, webcam etc.? Are you able to play 3d games?

---

### Post by marcoftheknight on 2010-06-06
Linux OS is formulated to be compitible with almost everything you might not need any drivers

sudo lshw to see if linux is seeing all your hardware and copy the output for us.

Love linux

---

### Post by 3rdalbum on 2010-06-06
If it's Intel graphics, then you don't need any extra drivers for that.

If it's Nvidia graphics, then you should reload your package list (System > Administration > Synaptic Package Manager, click Reload) and then try looking in Hardware Drivers again.

---

### Post by marshman998 on 2010-06-06
I tried what everyone said, and this is what the terminal said I have for graphics:
Intel Corporation Core Processor Integrated Graphics Controller (rev 02)

I also tried going to the Synaptic Package Manager and tried reloading (even though I have Intel), and no luck.

What my problem is, is that I am not able to connect to my router using wifi. My brother does it with his ubuntu, and he has no problems. Should it connect automatically when I turn wireless on my computer, or is there somewhere I have to go to try and connect it? Because I am having no luck at all right now. I don't think it's detecting the flash drive I put in either. I am trying to transfer some stuff from my old desktop over.

Any thoughts?

EDIT - I just discovered Cheese won't recognize my webcam either. Basically nothing is working right now.

---

### Post by acrazyplayer on 2010-06-06
There is a little icon in the top right corner that is two arrows, 1 pointing up and 1 pointing down. That is where you would go for wireless. It should have already scanned for wireless access points so all you have to do is click on it and enter the password. Ask your brother how to do so because apparently he knows how. 

Sorry but I can be of no help to you about the webcam as I don't have one.

The Intel graphics do not need a driver as it is already installed in the Linux kernel like many other things so you need not worry about that.

---

### Post by marshman998 on 2010-06-06
Hey thanks guys, I found this thread, and it seems to address all my issues:
[http://ubuntuforums.org/showthread.php?p=9419063](http://ubuntuforums.org/showthread.php?p=9419063)

I'll let you know if it works out.

---

