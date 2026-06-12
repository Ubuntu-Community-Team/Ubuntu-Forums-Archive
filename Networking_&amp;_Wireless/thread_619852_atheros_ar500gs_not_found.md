---
title: "atheros ar500gs not found"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by iateshaggy on 2007-11-21
first, i'm a complete linux noob, great at windows, but clueless on linux.  i just installed xubuntu 7.10 but my wireless card doesn't seem to be found.  i'm using a hp 511n pc (not a laptop).  this is a wireless card that fits in a pci slot.

---

### Post by kevdog on 2007-11-21
Can you post 

lshw -C network

This will tell you at least if the card is identified.  If it is identified, it should either tell you UNCLAIMED if there is no associated driver, or actually give you the name of the driver if it is being claimed.

---

### Post by iateshaggy on 2007-11-21
could u please dumb that down just a bit and i'll do it.

---

### Post by kevdog on 2007-11-21
Yea type the above command in the terminal and post the output.  That's about it!

---

### Post by iateshaggy on 2007-11-21
when i open terminal, my desktop reboots.

---

### Post by kevdog on 2007-11-21
You got more problems then than your wireless connection!!

---

### Post by iateshaggy on 2007-11-21
any clue how to fix the terminal issue, w/o doing a total reinstall.  i had a lot of trouble just installing the first time.

---

### Post by kevdog on 2007-11-22
Might want to try posting on a different forum.  Since youve gone through the process once -- you are kind of familar with the installation process -- partitioning of drives etc.  You might benefit from installing through the alternate CD.  Its not as pretty or intuitive, however it really works when the liveCD keeps messing up.

---

### Post by iateshaggy on 2007-11-22
i installed w/ the alternative.  thanks for your time, i gotta get some sleep.

---

### Post by iateshaggy on 2007-11-22
> **kevdog said:**
> Can you post 

lshw -C network

This will tell you at least if the card is identified.  If it is identified, it should either tell you UNCLAIMED if there is no associated driver, or actually give you the name of the driver if it is being claimed.

ok, back to this drawing board.  i ran the command and it is recognizing it but says unclaimed.  i'm guessing that means we have a driver issue.  how do i go about getting a driver for it.

---

### Post by iateshaggy on 2007-11-23
bump.

---

### Post by iateshaggy on 2007-11-24
i still can't figure this one out.  i can get the driver from another pc, how do i go about converting it for xubuntu?

---

### Post by iateshaggy on 2007-11-27
problem solved.

---

