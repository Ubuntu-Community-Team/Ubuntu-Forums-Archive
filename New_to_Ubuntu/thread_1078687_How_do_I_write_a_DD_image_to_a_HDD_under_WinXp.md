---
title: "How do I write a DD image to a HDD under WinXp?"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by alexisantonakis on 2009-02-23
Hi,

I was using the TestDisk utility on a damaged HDD I have Ubuntu installed on.
I made a Disk Image of the drive onto my WinXP machine which I believe uses the dd command.

I am trying to find out how I can 'restore' the image back to the HDD, but under WinXP....I can find various commands in Linux to do this, but not under XP.
One trouble is the HDD I am trying to write back to is not recognised under XP, although TestDisk displays it as '/dev/sdd'
So How do I refer to this path under XP as well?

Many thanks
Alexis

---

### Post by era86 on 2009-02-23
Perhaps you can look into rawrite(2).exe or fdimage.exe.  I believe these are used to do what you are describing.

Edit: I think these only work on floppy images from what I've read.  Make sure to do research.

---

### Post by bumanie on 2009-02-23
Look [here]("http://www.insanelymac.com/forum/lofiversion/index.php/t378.html") for ways to use dd in windows. To get windows to read the ext3 partition you will have to install [this]("http://www.fs-driver.org/index.html"). I can't tell you any more as I have only used dd commands from within linux.

---

### Post by The Cog on 2009-02-23
Why not use an Ubuntu live CD or memory-stick and run dd from there?

---

