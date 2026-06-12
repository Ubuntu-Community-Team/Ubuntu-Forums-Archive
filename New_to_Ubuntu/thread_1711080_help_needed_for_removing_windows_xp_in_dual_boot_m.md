---
title: "help needed for removing windows xp in dual boot mode"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by songman79 on 2011-03-20
total beginner, using ubuntu for 3 weeks, loving it, but now I want more space and power out of my laptop (IBM thinkpad R50) how can I remove windows xp? I have already backed up my data and want to get the most out of my ubuntu os, thanks for your time and help in advance. reagrds adam.;)

---

### Post by Foxheadz on 2011-03-20
Well first of all depending on the size of your hard drive you don't necessarily have to delete xp. Also how did you install it, did you use wubi or install it from a live cd?

---

### Post by songman79 on 2011-03-20
I installed from the live cd hdd is 40gb I've already got win7 on another computer I want this as a ubuntu only machine

---

### Post by Foxheadz on 2011-03-20
Ok so your gonna need a [gparted]("http://gparted.sourceforge.net/livecd.php") live cd and possibly an ubuntu live cd. First boot into the gparted live cd and remove the partition with windows xp. Then resize the ubuntu partition make it take up the full drive (you may need to unmount the drive first). That should be all. If you can't seem to boot follow the link in my signature about restoring grub.

---

### Post by songman79 on 2011-03-20
I installed gparted onto my computer ,do I go into the part that says create partition table, or should i use the gparted live cd i downloaded

---

### Post by Foxheadz on 2011-03-21
You need to boot into the gparted live cd in order to expand the partition because that requires the drive to be unmounted. Since ubuntu is on the drive you can't be in it and working on the hard drive.

---

