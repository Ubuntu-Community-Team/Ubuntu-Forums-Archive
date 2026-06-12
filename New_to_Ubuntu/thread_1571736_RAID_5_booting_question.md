---
title: "RAID 5 booting question"
date: 2010-09-10
forum: New to Ubuntu
---

### Post by synicalx on 2010-09-10
Hey all

Not sure if a question about multiple RAID's is classified as 'Beginner' but I'm an Ubuntu beginner ):P

Anyways onto my question; I've got 3x500gb SATA drives that I'm looking at building into a RAID 5 array, only problem is it looks as if Ubuntu doesn't boot from RAID 5. The solution (as far as I can see) is to make a partition on each drive for /boot and configure that into a RAID 1 array, levaing the remaining space for the RAID 5 partition and swapfile (non RAID'ed?)

Basically what I'm asking is have I got the right idea with the 3 partitions and 2 RAID arrays and also if I am on the right track; how big should /boot be?

Thanks in advance and sorry to the mods if this is in the wrong section!

---

### Post by Xianath on 2010-09-10
For a beginner, you hit the nail on the head pretty well :) My setup is exactly that, only, I don't have swap. My /boot is 512MB so I can keep a few kernels around. Don't go below 100MB or you may have troubles upgrading kernels. With 3x500GB I think you can sacrifice 0.1% to be on the safe side :)

---

### Post by synicalx on 2010-09-10
> **Xianath said:**
> For a beginner, you hit the nail on the head pretty well :) My setup is exactly that, only, I don't have swap. My /boot is 512MB so I can keep a few kernels around. Don't go below 100MB or you may have troubles upgrading kernels. With 3x500GB I think you can sacrifice 0.1% to be on the safe side :)

Awesome thanks for the reply! Good to know I'm still a little bit clever :p

Will post back once I get it all sorted and let you know how it went

---

### Post by v1ad on 2010-09-10
i have successfully set up a raid 0 in Ubuntu. to set up raid is a real pain in the a**. also technically its only a fake raid, unless u have a dedicated raid chip. and the fake raid is the issue. if i was not dual booting i would do exactly what you are doing. /home /usr /boot and a few others on separate partitions.

---

### Post by synicalx on 2010-09-10
> **v1ad said:**
> i have successfully set up a raid 0 in Ubuntu. to set up raid is a real pain in the a**. also technically its only a fake raid, unless u have a dedicated raid chip. and the fake raid is the issue. if i was not dual booting i would do exactly what you are doing. /home /usr /boot and a few others on separate partitions.

Yeah I've heard it can be a bit of fun, however I think I might install the server edition this time around (w/ GUI as I'm using it for VM's mainly) which seems to have a fairly straight forward RAID config thingo. Also I'll just stick with a software RAID for now, only using the one OS and I'm student so a RAID card would mean I go without food for a week :D

Thanks again for your advice guys!

---

