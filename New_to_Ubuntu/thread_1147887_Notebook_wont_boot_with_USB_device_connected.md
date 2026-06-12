---
title: "Notebook wont boot with USB device connected"
date: 2009-05-03
forum: New to Ubuntu
---

### Post by Snipershot on 2009-05-03
[https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6Km](https://wiki.ubuntu.com/LaptopTestingTeam/AsusA6Km)
I found this testing my laptop, now I'll quote the part I'm curious about.
> Boot hangs on ACPI: Setting ELCR to 0200 (from 0c30) if an USB mouse is connected. This is caused by a BIOS bug. Use a patched ACPI DSDT from [http://acpi.sourceforge.net/dsdt/index.php](http://acpi.sourceforge.net/dsdt/index.php) to work around this problem. Downgrading to BIOS release 0202AS is also reported to work. 
Replacing this ACPI, will it have any negative effects? Can it cause problems when updating and such? Basically is there anything negative about it?

Also a smaller question, on all the versions listed there the "other special keys" work. I'm using Jaunty and none of the buttons seem to do anything. Is there anything I can do about this?

---

### Post by Mark Phelps on 2009-05-04
> **Snipershot said:**
> [Also a smaller question, on all the versions listed there the "other special keys" work. I'm using Jaunty and none of the buttons seem to do anything. Is there anything I can do about this?
Unfortunately, probably NOT.  I ran into the same situation trying to upgrade a Fujitsu tablet.  None of the tablet bezel keys worked after that and no one has been able to tell me how to get xev to see the keys again.  Pressing the keys produces no responses -- in xev, dmesg, or acpi-support.  It's like 9.04 just can't see them, period.

---

### Post by Snipershot on 2009-05-04
Thats a shame, really hate accidentally sliding my hand over the touchpad when I got a mouse attached. An addition to my original question, I looked over that DSDT website and found that they didn't have my exact model (A6KM-Q056H) is there a chance that some of the others for A6Km ones might work or am I guaranteed that the system wont boot if I make an error with this thing?

---

