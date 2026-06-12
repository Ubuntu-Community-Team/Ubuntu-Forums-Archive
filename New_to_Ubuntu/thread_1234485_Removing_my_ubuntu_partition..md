---
title: "Removing my ubuntu partition."
date: 2009-08-07
forum: New to Ubuntu
---

### Post by Rave Gloves on 2009-08-07
I was wondering, how dose one remove ubuntu compleatly from their system?.  I have ubuntu and vista on a duo boot. I have had lots of problems with ubuntu and i have mostly all my most used programs on vista so i havent been really using ubuntu at all. Its taking up quite alot of my memory and im running out as it is. so i have about 120gig that im not using that i would want to use. 

I would think the easiest way would be to get a vista disk, save everything to an external HD and then reinstall vista?

i dont want to dive right into this untill i know what im doing, alot of guides online seem a little vauge. Could someone give me a wee hand?

---

### Post by Dark Aspect on 2009-08-07
[GParted]("http://gparted.sourceforge.net/")

Backup your data first in case of data loss but I have never had that happen. Just a good idea when your modifying your partitions.

---

### Post by sdlynx on 2009-08-07
Just delete the ubuntu partition from Windows, and the swap partition.  Then, expand your Windows partition to fill everything unallocated.  Finally, you need to recover the MBR so if you have a Windows installer disk use that, go into recovery console and type "fixmbr" and "fixboot".  If you don't have a Windows installer disc, try this: [http://ubuntuforums.org/showthread.php?t=311908](http://ubuntuforums.org/showthread.php?t=311908) .

---

### Post by Rave Gloves on 2009-08-07
> **Dark Aspect said:**
> [GParted]("http://gparted.sourceforge.net/")

Backup your data first in case of data loss but I have never had that happen. Just a good idea when your modifying your partitions.

So i can basicly delete ubuntu from doing this yeah?. or will i still have it but it wont be using my memory?

---

### Post by Dark Aspect on 2009-08-07
> **Rave Gloves said:**
> So i can basicly delete ubuntu from doing this yeah?. or will i still have it but it wont be using my memory?

Yeah should remove whole thing, the swap partition can be stubborn but you can format that as something else with

> gksu /usr/sbin/gparted

and than boot into the [GParted]("http://gparted.sourceforge.net/") livecd or merely use the Ubuntu livecd and load gparted with above command.

---

### Post by louieb on 2009-08-08
Not a problem removing Ubuntu. Its **GRUB **- make sure your computer boots straight to windows before removing it. or your computer won't boot the hard drive at all.  [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")

---

### Post by pricetech on 2009-08-08
If you're not running Ubuntu, it's not using any memory.

Drive Space is what it's using.

I guess I woke up in a "hair splitting" mood this morning.

---

### Post by Dark Aspect on 2009-08-08
> **louieb said:**
> Not a problem removing Ubuntu. Its **GRUB **- make sure your computer boots straight to windows before removing it. or your computer won't boot the hard drive at all.  [IDBS Remove Replace Uninstal Grub]("http://members.iinet.net.au/%7Eherman546/p18.html")

Why even bother removing GRUB? you can use grub as a replacement for for window's ntldr.

Nevertheless, the OP can use [Super Grub]("http://www.supergrubdisk.org/") to fix a ntldr or a grub loader so inability to boot is not really a problem.

---

### Post by louieb on 2009-08-08
> **Dark Aspect said:**
> ... so inability to boot is not really a problem.

:evil: Might not be a problem but it is a shock if your not expecting or prepared for it. 

> Why even bother removing GRUB? you can use grub as a replacement for for window's ntldr.

GRUB can't replace ntldr - it has to be there. When GRUB boots a windows OS it chain loads the windows boot loader and quits.

---

### Post by LewRockwell on 2009-08-08
> **Rave Gloves said:**
> I was wondering, how dose one remove ubuntu compleatly from their system?.  I have ubuntu and vista on a duo boot. I have had lots of problems with ubuntu and i have mostly all my most used programs on vista so i havent been really using ubuntu at all. Its taking up quite alot of my memory and im running out as it is. so i have about 120gig that im not using that i would want to use. 

I would think the easiest way would be to get a vista disk, save everything to an external HD and then reinstall vista?

i dont want to dive right into this untill i know what im doing, alot of guides online seem a little vauge. Could someone give me a wee hand?

use Vista disk to repair MBR

check this by removing optical media and rebooting

after repairing MBR then use Vista to eliminate whichever partitions you desire to delete

.

---

