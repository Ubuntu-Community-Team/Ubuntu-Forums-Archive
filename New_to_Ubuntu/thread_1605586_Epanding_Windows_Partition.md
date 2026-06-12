---
title: "Epanding Windows Partition"
date: 2010-10-25
forum: New to Ubuntu
---

### Post by JohnCUbu on 2010-10-25
When I installed Ubuntu, I gave windows less space than I need. My setup is windows/Ubuntu/swap/smallpart1/big part2/other partitions. I want to delete the two partitions behind Ubuntu and its swap, then expand windows. Moving the location of Ubuntu/swap back. I'm downloading gparted now, as doing this from windows with Easeus is not possible. But browsing the threads on partition resizing has alot of "do this wrong and grub will be confused" warnings. So, I just want to be sure, before I do this, that just using gparted and rebooting is all I need to do? Thanks. Man, I hate being a Ubu freshman.

---

### Post by Stephen Morgan on 2010-10-25
Yes, gparted can just delete the later partitions, move buntu and swap to the right and expand the windows partitions. Be ready for a wait, though, moving partitions is a slow business, especially if they're full of data. If you're worried about grub becoming confused run **sudo update-grub** after you're finished and grub ought to be okay.

---

### Post by Hippytaff on 2010-10-25
back up stuff :-D

---

### Post by JohnCUbu on 2010-10-25
Thanks for the fast replies! I think I'll use Paragon from windows to backup since I'm already here in windows. The funny thing is, I'm trying to expand windows so I can make HP recovery DVDs I never got around to  (It says I don't have enough space). As far as sudo update-grub how do I issue that command if I reboot and get errors and no grub? That's the doomsday scenario I had once before when something messed up one my Ubu partition. Couldn't even get into windows. Forget how I fixed it.I was one of those terrible experiences that scarred me :P

---

### Post by Hippytaff on 2010-10-25
You can boot from live cd and try to fix grub :-)

---

### Post by JohnCUbu on 2010-10-25
Thanks again. Fast help.

---

