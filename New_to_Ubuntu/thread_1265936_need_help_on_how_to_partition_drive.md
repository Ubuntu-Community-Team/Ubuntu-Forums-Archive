---
title: "need help on how to partition drive"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by demeter on 2009-09-14
[SIZE=3]hi there, im planning to use my spare 40 Gig Hard drive to install jaunty, but Im not sure on how to properly and safely partition this. My plan is to have 15 Gig for the system and the rest for saving my data. when I ran the installer and it came to manually partitioning the drive section, i got confused...What is the correct: type, mount point, file type for each partition? I do know(from the threads) that the swap partition should be at least double the RAM...so i quit and ran to the other pc to write this...:) Any help will be greatly appreciated....Thanks in advance...[/SIZE]

---

### Post by nothingspecial on 2009-09-14
If you are using the whole drive.

I use 8gig for ubuntu - format ext3 and mount as /

2gig for swap (i have 1 gig ram) - use as swap area

And the rest for home -  format ext3 and mount /home

---

### Post by demeter on 2009-09-14
[SIZE=2]yes, I will be using the whole drive for this. Thank you very much for the info...:)[/SIZE]

---

### Post by nhasian on 2009-09-14
since you have such a small drive, i recommend that you make the root partition only 10 gigs and the swap file the same size as ram.  EXT3 was the default in jaunty, but EXT4 is the default filesystem in Karmic Koala 9.10

---

### Post by mapes12 on 2009-09-14
From the left in Gparted in this order:

/ - about 8GB
/home - balance of space after deducting root and SWAP
/SWAP - about 2xRAM

Once you have the partitions set up (I use ext3) then in the partitioning section of the installer select "Manual" then for each partition carefully select what you want it to be i.e.

/
/home
/SWAP

Post back if you need any further help.

---

### Post by demeter on 2009-09-14
[SIZE=2]Thank you very much guys, I'm installing right now...I'll post back if its successful...:)[/SIZE]

---

