---
title: "How to roll back  BIOS?"
date: 2010-12-04
forum: New to Ubuntu
---

### Post by Urban Taco on 2010-12-04
I updated the BIOS on my Dell Optiplex from A00 to the latest A07 in Ubuntu Server 10.10 by following this thread: [http://ubuntuforums.org/showthread.php?t=475100](http://ubuntuforums.org/showthread.php?t=475100)

Everything installed fine. But now when my Rosewill RC-218 SATA controller card is plugged into the PCI Express slot, the computer won't boot. I get no picture on the monitor and the fans spin out of control.  

 I changed the video settings in bios from Auto to OEP when I first   installed the card, under A00. This prevented the computer from thinking   the PCI Express card was a video card. The setting remains the same   now. I've toggled it several times, but still I get a dark screen, the   monitor not recognized and no boot. When I pull the PCI Express card everything   works fine, video wise, leading me to believe the system thinks that the  PCI Express SATA card is a video card. 
 
 I really, really, really need this card working as I'm setting up RAID on this system. Does anyone know what I can do to get the SATA card working OR know how I can roll back my BIOS to A00?  

Thank you. Thank you. Thank you.

---

### Post by MooPi on 2010-12-04
Most if not all motherboards have a reset function on the bios. It generally involves changing pins on a jumper switch or pulling the battery from the motherboard while powered off. You'll have to research your board to get a definitive solution. But a reset of the bios might be your solution. I've had bios selections get stuck on the wrong setting before and a reset was my solution.
  You may even be able to reset  to default inside the bios, but I would have doubts. but that may be the first and easiest choice.
I would document the settings currently in use so you can replicate the needed settings afterward. This doesn't roll back the bios just to default settings. I would try the reset first before attempting to roll back to a previous bios control.

---

### Post by Urban Taco on 2010-12-04
Very cool. Thanks. I'll give it a shot.

---

### Post by Urban Taco on 2010-12-08
This motherboard has pins to reset the BIOS password, but nothing to rollback the BIOS version ... 

Any other ideas? 

All the Dell flasher programs say I can't upgrade with an older version of BIOS ... Are there any third party or independent flashers I can use with the Dell .hdr files?

---

### Post by Grenage on 2010-12-08
You can't 'roll-back', but you should be able to flash the BIOS with an older version. I doubt the version would get checked if you used the 'bootable floppy' angle.

---

### Post by iponeverything on 2010-12-08
> **Urban Taco said:**
> This motherboard has pins to reset the BIOS password, but nothing to rollback the BIOS version ... 

Any other ideas? 

All the Dell flasher programs say I can't upgrade with an older version of BIOS ... Are there any third party or independent flashers I can use with the Dell .hdr files?

if the flasher program is using file name to determine the version, you might try renaming it. if it is pulling from somewhere inside, you might use a hex editor to change it. 

Doing any of these things probably carries a risk of bricking you motherboard.

---

### Post by Urban Taco on 2010-12-08
> **iponeverything said:**
> if the flasher program is using file name to determine the version, you might try renaming it.

AWESOME! That did it. I hooked up a Windows drive, renamed the A00.EXE file A07 and it loaded fine. Thanks! :D

---

