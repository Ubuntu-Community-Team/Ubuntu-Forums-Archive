---
title: "My Netgear WG111v2 isn't working"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by Squee3 on 2007-08-05
Ubuntu isn't even recognizing that the wireless card is plugged in.  The blue light on the card isn't lighting up.  I've tried using the software CD that has it's drivers on it, but Linux doesn't support .exe, and it won't run it.  I've tried to install NDISwrapper off of a CD that I put it on, but it says that the CD is blank.  It might be because I downloaded it using windows, and put it on a CD with Windows.  What can I do to get my wireless card working?

---

### Post by kevdog on 2007-08-05
Dont panic however you need to give some information about the chipset in your card.  Can you post the following (type at command prompt and cut and paste output)
lspci -nn | grep Network
lshw -C network

---

### Post by splintercellguy on 2007-08-05
You have to copy the driver files to hard disk before attempting to install with ndiswrapper.

---

### Post by Squee3 on 2007-08-05
neither of those commands work.  And where can I find the drive files?

---

