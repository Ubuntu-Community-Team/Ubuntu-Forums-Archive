---
title: "Ubuntu install cd keeps loading"
date: 2011-09-03
forum: New to Ubuntu
---

### Post by DesignTrice on 2011-09-03
So, i insert the install cd (Ubuntu 11.04), boot up my computer and the loading screen of my install cd starts loading, loading andd loading.. What am i supposed to do? Thanks :)

---

### Post by Rubi1200 on 2011-09-03
Hi and welcome to the forums :-)

Please post the specifications for the computer, especially RAM and graphics card.

Thanks.

---

### Post by DesignTrice on 2011-09-03
Intel Celeron D Cpu @ 3,20 Ghz. 223 MB Ram on ATI-RADEON XPRESS 200 SERIES. There you go! :P

---

### Post by DesignTrice on 2011-09-03
So, i insert the install cd (Ubuntu 11.04), boot up my computer and the loading screen of my install cd starts loading, loading andd loading.. What am i supposed to do? Thanks

---

### Post by sanderd17 on 2011-09-03
It is very normal that it takes some minutes (certainly wait 10 minutes). CD's are slow.

If it still doesn't load, press a key when you see this  screen: 

[IMG]http://pricklytech.files.wordpress.com/2010/07/ubuntu-boot-01.png[/IMG]

This will bring you to a text menu. See if you can load ubuntu from that menu.

---

### Post by Rubi1200 on 2011-09-03
Did you set BIOS to boot from the CD/DVD drive as first priority?

Have you tried adding any boot parameters?

Have you tried other CDs and do you get the same result?

---

### Post by DesignTrice on 2011-09-03
I'm talking about the loading screen of ubuntu itself. The one with the 5 dot loading states. Also, there are green messy borders at the logo and the dots.

---

### Post by bapoumba on 2011-09-03
Threads merged.

---

### Post by themusicalduck on 2011-09-03
223MB of RAM is below the minimum requirements of Ubuntu - [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I once tried to do the same. Loaded a live CD session on a laptop with 256MB and it never got to the desktop. I'd give Lubuntu a try instead.

---

### Post by sanderd17 on 2011-09-04
> **bapoumba said:**
> Threads merged.
Oh, Ok. That why I didn't see the system requirements. Below is what the answer should be:

> **themusicalduck said:**
> 223MB of RAM is below the minimum requirements of Ubuntu - [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

I once tried to do the same. Loaded a live CD session on a laptop with 256MB and it never got to the desktop. I'd give Lubuntu a try instead.

---

### Post by Flashyman on 2011-11-08
> **sanderd17 said:**
> It is very normal that it takes some minutes (certainly wait 10 minutes). CD's are slow.

[...]
Damn if I wouldn't have read that I would have broken another ubuntu disc into pieces... the other one was kubuntu on a dvd which loaded in less then a minute... now i've been watching this ubuntu splash screen for over 5 minutes...
Though I barely understand why it makes so much of a difference, since my pc should be fast enough for a smooth and quick install... guess not.

MoBo: P5QL-Pro
GFX-card: NVidia GeForce GTX 460
Mem: 2×2GB DDR2-800 (running at 1066Hz) Dual-channel
CPU: Intel Core 2 Duo E8400 @ 3Ghz (OC'd @ 3.6Ghz)
-now comes the funny part-
HDDs:
  1× PATA 160GB drive (with win7)
  1× PATA 15GB drive (wanting to install ubuntu on this)
DVD:
  1× SATA DVD-burner
PSU: unknown brand, modular 550W.

While typing this the 10th minute has passed, seems so hopeless, but when I hit [DEL] at the loading splash screen I get text info telling me that it's still doing something!

Anyway this is by far the slowest live / install cd I've ever encountered. I don't even remember Win95 taking that long to load from CD.

Btw, when I hit [DEL] now, it says: "Checking for running unattended-upgrades:" and I believe it's been sitting there for more then 5 minutes, can't be good...

edit1: News: the red dots below the Ubuntu logo stopped moving, hitting [DEL] doesn't do anything anymore... the HDD led indicator is flashing as well as the DVD led indicator, sooo is it still doing something? let's just wait another 10 minutes and see what happens...

edit2: It didn't come any step further, I'm trying to see if the disc has issues, I loaded BIOS defaults and disabled both my harddrives, it seems that this doesn't change anything, which makes me think that maybe something went wrong in the downloading / burning of the ubuntu iso file, or maybe the iso file is buggy, but in that case I would expect way more people with problems.

Currently nothing works, ubuntu11.10 live-cd, grub (from previously installed kubuntu), and also windows bootloader is gone.
Any suggestions before I download 11.04 and try that?

---

### Post by Flashyman on 2011-11-08
Not sure why or what went wrong, but I assume my laptop has a crappy dvd-burner.
So I boot my other PC with Windows (the pc where I want to install ubuntu also), and burn the iso with imgburn.
Seems to work perfectly now.

---

