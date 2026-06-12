---
title: "Remove Ubuntu 10.04"
date: 2010-08-12
forum: New to Ubuntu
---

### Post by komatsu100 on 2010-08-12
I installed Ubuntu 10.04 on a Acer 5251 Laptop which came with Windows 7 preinstalled.  I loaded it beside of Windows and I would like to remove and install in a partition of its own.  It was a dump mistake while I was installing and now I would like to uninstall Ubuntu and install in a partition of its own. Help please.

---

### Post by Frogs Hair on 2010-08-12
Is this a Wubi installation ? If so see this thread.   [http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by techunit on 2010-08-12
Unless you did a Wubi install it is in a partition of its own. How did you install it is the real question. Did you A: Install Inside Windows, or B: Install from the USB or CD from the bios

---

### Post by komatsu100 on 2010-08-12
[QUOTE=Frogs Hair;9711864]Is this a Wubi installation ? If so see this thread.   [http://ubuntuforums. g/showthread.php?t=1519354](http://ubuntuforums. g/showthread.php?t=1519354)[

---

### Post by komatsu100 on 2010-08-12
Sorry I didn't give that information in the original post.  I installed Ubuntu from a CD and yes it set a pertition, but I had set aside a larger partition for Ubuntu, and I would like to uninstall and reload into the larger partition.

---

### Post by brokenromeo on 2010-08-12
Depending on how your partitions are configured, you may be able to just use the free space from the other partition and allocate it to the existing installation. You would want to use something like gparted to do this and boot from the live cd...

---

### Post by earthpigg on 2010-08-12
1) backup any data you want to keep. easiest way for the ubuntu install is to backup the entire /home folder on the current install.
2) run gparted from an ubuntu live cd.
3) do your partitioning, possibly delete the old partition if you wish.
4) install ubuntu again.
5) restore your backed up data.

---

### Post by komatsu100 on 2010-08-12
How do I make a live CD?

---

### Post by jtarin on 2010-08-12
> **komatsu100 said:**
> How do I make a live CD?How did you install Ubuntu? From a Live CD/DVD is the answer? You just don't install it....you run it in trial mode.

---

### Post by the.dark.lord on 2010-08-12
> **komatsu100 said:**
> How do I make a live CD?

Just download Ubuntu(the default option), and burn it on a CD.

---

### Post by komatsu100 on 2010-08-13
Thanks I can most likely handle it from here.

---

