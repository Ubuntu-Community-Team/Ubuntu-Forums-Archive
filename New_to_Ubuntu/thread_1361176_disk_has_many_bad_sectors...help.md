---
title: "disk has many bad sectors...help"
date: 2009-12-21
forum: New to Ubuntu
---

### Post by gobode on 2009-12-21
okay so i dual booted and i installed ubuntu with wubi, but when i load ubuntu it tells me one or more disks are failing. :confused:

---

### Post by ScottinSoCal on 2009-12-21
> **gobode said:**
> okay so i dual booted and i installed ubuntu with wubi, but when i load ubuntu it tells me one or more disks are failing. :confused:
Mine did the same thing when I upgraded to 9.10 from... whatever I was running before that. 8 something, I think. Anyway, I started getting all these obnoxious warnings, so I googled and found out that a LOT of people are getting these warnings, some on brand new HDDs. I chalked it up as a bug, and ignored it. A week later, my HDD failed.

I got a new drive in, managed to retrieve my data, and the new HDD works flawlessly and without warnings.

---

### Post by llawwehttam on 2009-12-21
Its better to be safe than sorry. I suggest you get a new HDD and back up to it as soon as possible.

---

### Post by bodhi.zazen on 2009-12-21
First back up your data, then see :

[http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu](http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu)

you may need to do that from the live CD (not sure if you can do it with wubi).

---

### Post by gobode on 2009-12-22
> **bodhi.zazen said:**
> First back up your data, then see :

[http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu](http://www.howtoforge.com/checking-hard-disk-sanity-with-smartmontools-debian-ubuntu)

you may need to do that from the live CD (not sure if you can do it with wubi).


okay so i try to backup, but a message is displayed reading unable to install bootloader?

---

### Post by bodhi.zazen on 2009-12-22
> **gobode said:**
> okay so i try to backup, but a message is displayed reading unable to install bootloader?

Hmm, that is an odd error.

May not be possible with wubi =)

how or what did you do to get that error ?

---

### Post by t0p on 2009-12-22
> **gobode said:**
> okay so i dual booted and i installed ubuntu with wubi, but when i load ubuntu it tells me one or more disks are failing. :confused:

I'm confused.  Did you dual-boot, or did you install with wubi?  I don't really understand why you would have done both.

A dual-boot is where you repartition your hard drive, so you have Windows on one partition and Ubuntu on another partition.  Wubi is a way of installing Ubuntu as an application inside your Windows installation.

**EDIT:**
> **gobode said:**
> okay so i try to backup, but a message is displayed reading unable to install bootloader?

Now I'm more confused.  Do you mean you can't start Windows?  Or are you trying to start Ubuntu?  I thought you said you couldn't run Ubuntu because of bad sectors on your disk...

---

### Post by gobode on 2009-12-22
> **t0p said:**
> I'm confused.  Did you dual-boot, or did you install with wubi?  I don't really understand why you would have done both.

A dual-boot is where you repartition your hard drive, so you have Windows on one partition and Ubuntu on another partition.  Wubi is a way of installing Ubuntu as an application inside your Windows installation.

**EDIT:**


Now I'm more confused.  Do you mean you can't start Windows?  Or are you trying to start Ubuntu?  I thought you said you couldn't run Ubuntu because of bad sectors on your disk...

sorry, i guess i didn't dualboot then...well i first tried to dual boot but when i installed ubuntu it deleted my windows os and ubuntu would not install nor would the livecd work. I was finally able to get it back to normal and install windows vista, in fear of the same thing happening i installed ubuntu with wubi, but when i load ubuntu it tells me there are many bad sectors. Vista and ubuntu both load but when im in ubuntu there is an icon saying there are many bad sectors, when i open it and click more info it tells me to backup all data and replace disk...when i try to backup i get the message that bootloader cannot install, sorry for the confusion. if you have any information about why there are bad sectors i would really much appreciate it. =]

---

### Post by Dvdre on 2009-12-23
I will join those saying 9.10 also gave me this message, bad sectors on the Windows partition. Well, it ended up that SOMETHING was wrong with the Windows partition, but not bad sectors. After an upgrade to Windows 7, the computer would sometimes freeze, requiring a power button off. Eventually, the laptop wouldn't boot at all to Windows, but it would to Ubuntu. 

After some pain, I managed to wipe the entire hard drive, reinstall a clean version of Windows 7 and then reinstall Ubuntu 9.04.

And now. ... the laptop works like a dream and Ubuntu sees no hard drive problems at all.

---

