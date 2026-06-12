---
title: "Deleting windows xp from dual boot with ubuntu"
date: 2010-10-27
forum: New to Ubuntu
---

### Post by yellow hobbit on 2010-10-27
Okay so basically my problem is i have partitioned my drive c, installed windows xp on one and installed ubuntu on the other, Now i would like to get rid of windows xp but keep ubuntu. Without loosing all my files etc...

I have had this problem before and deleted the windows xp partition before which then could not boot ubuntu either. i was wondering how do i get rid of windows xp, merge the unallocated space after with ubuntu.

Thanks i have also included picture of the boot screen if that helps at all, i am total noob as you can see, learning from mistakes xD 

[http://ubuntuforums.org/picture.php?albumid=2077&pictureid=6925](http://ubuntuforums.org/picture.php?albumid=2077&pictureid=6925)

---

### Post by ivarn on 2010-10-27
Well, you don't have to delete the partition.
The partition could be good to have as a place to put other files on such as videos, music and stuff.
If you wanna do this, just right click on the partition from ubuntu and click format.
Now just update grub (sudo apt-get update grub).
If you remove the partition you would also have to resize the ext4 (linux) partition.
But if you wanna delete and resize, install partitionmanager from synaptic.
GOod luck.

---

