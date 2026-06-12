---
title: "want to move ubuntu"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by tleeski on 2010-03-08
I recently received my March issue of Smart Computing, and found the article about downloading and installing Ubuntu 9.10.  All is well, after some issues initially with Gnome not loading (stuck in terminal mode and didn't know how to start X).  Now everything boots as it should and I found out how to set up my workspace as I like it.
My issue is, I like it and want to use both XP and Ubuntu, but I installed it on another partition on the same drive as XP, and now would like to uninstall, and put ubuntu on another drive entirely.  I can't seem to find anything about an uninstall process.  Any help?

---

### Post by Temposs on 2010-03-08
There isn't an uninstall process. Ubuntu is an OS, not an application. Is there an uninstall process for Windows? No, there isn't. 

All you do is format the Ubuntu partition(wipe it clean), fill the space with something else(like expanding your XP partition to fill the drive), and then go install Ubuntu wherever else you like, such as on your other hard drive.

---

### Post by Don1500 on 2010-03-08
Simple Solution.
Since you just loaded it I don't think you have too much stuff on your linux partition, correct?

Then you won't mind loosing that.

1. Login to Ubuntu using the Live CD. (The one you downloaded or received from Ubuntu)
2. System>Administration>Gparted
[INDENT][/INDENT][LIST]
[*]You should be seeing your Windows-Linux-Swap partitions on your boot drive.
[/LIST]
3. Delete the linux and swap drives
4. Extend the Windows partition to take the complete drive. Hit APPLY (The check mark)
[INDENT][LIST]
[*]This will eliminate your linux partition and the swap partition
[/LIST][/INDENT]
5. In the upper right select the other drive you have.
6. Format that drive with THREE partitions, one for / about 10-15 gig,   one for swap about 3 gig, and one for /home all the rest. Format to ext4.
[INDENT][LIST]
[*]Your Windows drives will be viewable from linux, but the linux will not be viewable from windows.
[/LIST][/INDENT]
7. Install Ubuntu on the newly formatted drive. Remember to put the / , swap, and /home in the right place during installation

---

### Post by tleeski on 2010-03-08
> **Temposs said:**
> There isn't an uninstall process. Ubuntu is an OS, not an application. Is there an uninstall process for Windows? No, there isn't. 

Good point.  Why didn't I think of that? (slap self on forehead):???:

All you do is format the Ubuntu partition(wipe it clean), fill the space with something else(like expanding your XP partition to fill the drive), and then go install Ubuntu wherever else you like, such as on your other hard drive.

I tired deleting the partition, but couldn't boot XP as I got a missing grub message.  I didn't format it, though.

Thanks for the response.

---

### Post by Don1500 on 2010-03-08
Startup using the live CD and follow my instructions, you will get Grub back.

---

### Post by tleeski on 2010-03-08
> **Don1500 said:**
> Simple Solution.
6. Format that drive with THREE partitions, one for / about 10-15 gig,   one for swap about 3 gig, and one for /home all the rest. Format to ext4.[INDENT]
[LIST]
[*]Your Windows drives will be viewable from linux, but the linux will not be viewable from windows.
[/LIST]
[/INDENT]7. Install Ubuntu on the newly formatted drive. Remember to put the / , swap, and /home in the right place during installation

This first install was pretty much automated with the cd... do those partitions go in that order?  And is /home on the rest of the drive for all my "stuff"?

---

### Post by Don1500 on 2010-03-08
> **tleeski said:**
> This first install was pretty much automated with the cd... do those partitions go in that order?  And is /home on the rest of the drive for all my "stuff"?

Yes but you should make sure you pick the right drive. and yes /home is all YOUR stuff and associated files (new programs you load, data, music, docs), / is the OS. and They should go in this order. / , /home , SWAP

---

### Post by tleeski on 2010-03-08
Thanks Don,
 
I actually had a little different scenario that I hadn't made clear. (not your fault)  The other drive was not permanently installed in the computer, but was going to be a swap drive, which was why I wanted to completely remove ubuntu from the xp drive.  I still ended up with the missing grub error and had to use recovery console w/ xp cd to fix the mbr and correct that problem.
 
Again, thank you for your assistance, and Karmic is alive and doing well on it's own drive.

---

