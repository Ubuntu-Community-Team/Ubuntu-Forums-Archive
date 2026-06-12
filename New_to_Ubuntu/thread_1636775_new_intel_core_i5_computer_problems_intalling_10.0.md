---
title: "new intel core i5 computer problems intalling 10.04"
date: 2010-12-03
forum: New to Ubuntu
---

### Post by powerpc g4 on 2010-12-03
hello everyone,
i have been searching the forum but cant seam to find an answer problem...
i have a custom built shuttle sh55 j2 with the Intel core i5-650 processor, 4 gig's of g.skill ddr3 ram, 1 tb WD hard drive.

i want to do a dual boot with windows 7 and ubuntu 10.4, now i can get windows up with no problems but when i get to the prepare partition portion <step 4 of 8 i think> of the ubuntu installation my HD isnt recognized, all of the buttons, such as <New Partition Table> and <Edit Partition>,  are disable. When I click forward it gives me the "No root system is  defined..." message. 
when i open GParted and it shows it there.. i have  tried formating the drive partition in multiple formats to see i anything shows up... and nothing.
i have tried uninstalling windows and getting ubuntu up 1st and nothing
When i open terminal to cfdisk it displays a gray screen and says 'FATAL ERROR: Cannot open disk drive'.

so im not sure where to go from here....any ideas?

---

### Post by bananas4370 on 2010-12-03
I've run into this issue installing windows, and this could be affecting you. I had to change in the BIOS the section concerning SATA, from native SATA support to AHCI. You'll need to check how your BIOS words this. I don't know if this will affect your windows setup.

Cheers
Patrick

---

### Post by Daveth on 2010-12-03
Is the hard drive SATA 2 or 3? I found a post which suggests that SATA 3 is/was not recognised, though i imagine kernel fixes have sorted that by now.

---

### Post by powerpc g4 on 2010-12-04
-- i went into the bios and did the change over to AHCI. still nothing...

--the WD website is telling me the hard drive's interface is SATA 3 Gb/s,you mentioned a kernal to patch this, do you know how i could go about getting / installing it?

---

