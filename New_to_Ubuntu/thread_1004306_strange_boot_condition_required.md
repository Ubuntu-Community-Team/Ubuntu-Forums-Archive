---
title: "strange boot condition required ?"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by nnjond on 2008-12-07
Hi, Can anyone help me?

my pc won't even peep unless i unplug the ATA cable on my sdb (my data disc). (It loads normally if i do unplug it.) 

This problem seemed to occure when I left an os distro in the tray and re-started.. Since then my established setup fails to make it to the peep from cold: just the fan spins. When I unplug the data cable to my sdb, re-start from cold, it will go ahead and load the os from my primary drive but of course my data disc is not connected.

If once passed the peep from cold with sdb cable disconnected, I pause at the 1st "splash" screen and connect the sdb data cable. then press the warm-boot button on my pc it loads normally as it used to. 

This problem occured without me altering the bios.

What should I do?

---

### Post by Dedoimedo on 2008-12-07
Can you check that the boot order is correct in BIOS?
Dedoimedo

---

### Post by nnjond on 2008-12-07
Thanks for your interest. I've juggled the priorities around with no succsess 

At pressent

CDROM
sda
sdb
usb

---

