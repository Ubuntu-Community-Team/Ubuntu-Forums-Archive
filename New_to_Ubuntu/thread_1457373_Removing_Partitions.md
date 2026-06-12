---
title: "Removing Partitions"
date: 2010-04-18
forum: New to Ubuntu
---

### Post by myolbug on 2010-04-18
For the heck of it I thought I would try out Ubuntu Remix and Linux Mint on my Windows laptop.  I am thinking of dumping remix and Mint and either just going with Ubuntu 9.10 or mayyybe Mint.  Right now I have three partitions and I would like to remove the two Linux partitions and install just one of the above.

What do I need to do and do I need to do this through windows or?  When I installed Mint, I thought I could put it on top of Remix, but I had to make a separate partition.  I couldn't overwrite Remix.

---

### Post by mikewhatever on 2010-04-18
Boot from your live cd and use System->Admin->Gparted. You should be able to delete each and any partition.

---

### Post by myolbug on 2010-04-19
> **mikewhatever said:**
> Boot from your live cd and use System->Admin->Gparted. You should be able to delete each and any partition.

Thanks.  Is this something I would do after it loads completely or at a certain time in the boot process?

---

### Post by Paqman on 2010-04-19
Once it loads completely you'll be running totally off the CD. Open up Gparted, right click on your swap partition and "swapoff". Then you'll be able to make any changes to your partitions you want.

---

### Post by myolbug on 2010-04-19
mikewhatever and Paqman, you both have my sincere thanks.

---

### Post by Zintha on 2010-04-19
Gotta love that gparted.
This answered a similar question I had too! 
I know this won't seem relevant or helpful but I wanted to post saying thanks!

---

