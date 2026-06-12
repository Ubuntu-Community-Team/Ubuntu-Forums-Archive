---
title: "Unable to read ntfs file system on other HDD partition. GRUB??"
date: 2010-01-26
forum: New to Ubuntu
---

### Post by Jefferythewind on 2010-01-26
Hi everyone,
  I just did a fresh install of 9.10, and I like it, after I installed it I installed a fresh version of XP on the other partition.  Naturally XP took over the authority to boot at startup, but after some searching i found out how to set up Grub2, and now i get the grub menu.  Ubuntu works fine, so thats good, but the choice for booting windows returns an 

error: device not found
press any key to continue

  Also in GParted, there is an exclamation mark next to the NTFS partitions (see attached picture).

  Does anyone know what the problem might be.  I used Windows XP a couple times, even after I got GRUB working again.  This malfunction seems a little spontaneous to me, although it probably isn't.[ATTACH]145070[/ATTACH]

---

### Post by hhlp on 2010-01-26
to read ntfs file in ubuntu install :

```
ntfs-config
``` find in synaptic after that you can find in system - administration

how to recover grub2 :

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by themusicalduck on 2010-01-26
You could try running the command ```
sudo update-grub
``` to see if any errors come up, or to see if it manages to detect XP again.

---

### Post by Jefferythewind on 2010-01-28
Hey the musicalduck and hhlp, 

  I already had ntfs-config installed, i thought that would do it too, but i am still not recognizing the file system.  However I did run update-grub and not I can boot up the other windows partition.  Thanks a lot.  It is embarrassing that I didn't know of such a simple solution.  What does that command do?

---

