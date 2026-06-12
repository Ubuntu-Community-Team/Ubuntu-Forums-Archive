---
title: "Partition Help"
date: 2010-05-20
forum: New to Ubuntu
---

### Post by tf4545 on 2010-05-20
I'm a new Ubuntu/Linux User and could use some direction in merging unallocated space on my HD into Ubuntu.  I attached a screen shot of GParted showing what I have right now.  What I would like to do is merge the ~124G of unallocated space into the /dva/sda5 partition to expand the space allotted to Ubuntu.  The /dev/sda2 is the Windows 7 partition and unfortunately need to keep it because of one application that I can't get to run in Wine...another thread for another time...

Is there an easy way to move the unallocated space into /dev/sda5?  I have looked through the forums and because of my lack of experience working with partitions (in any os) I have gotten more confused. My understanding to this point is that if I create a new partition out of the unallocated space then move it to the right of /dev/sda5 then I should be able to extend the Ubuntu partition to eat up the new space however I can't get that to work.

I'm using 10.04 on a Toshiba Satellite laptop. 

Thanks in advance for any and all help!!!

---

### Post by ajgreeny on 2010-05-20
You can do this with gparted on the live CD but not from your existing ubuntu installed OS, as gparted can not work on a mounted partition.

You would simply need to run gparted from the live CD, grab the left end of the extended sda4 and enlarge that to use all the unallocated space.  Once you have done that you should also be able to do the same to the ubuntu ext4 partition sda5.  This will take a long time (maybe hours rather than minutes) so make sure your laptop is using mains power, so there is no risk of it fully discharging and going into suspend or shutting down.  **Make sure you have backups** before doing anything like this as things always can go wrong, even if they seldom do.

The alternative, which will be much quicker would be to simply make a new partition in the unallocated space and format it to either ext4, or ntfs if you want to use it for windows as well.  This can be mounted at boot up and used for all your data files, docs, photos, music and videos, etc etc.

---

### Post by tf4545 on 2010-05-20
Thanks for the help ajgreeny!  I took the quick (and easy) route and created a new partition and formatted it as ext4.  Much simpler and serves the same ultimate purpose.  One last quick question...if I am able and decide to dump Windows off my machine altogether and boot directly into Ubuntu, is that going to require a re-install of 10.04?

Thanks again for the help!

---

### Post by ubunterooster on 2010-05-20
No need to reinstall, you can go back into the live CD, Start Gparted, and delete the Windows partition and resize the Ubuntu one. I'm sure you'll get a lot better by then and this step will be easy[IMG]http://www.easyfreesmileys.com/smileys/free-happy-smileys-410.gif[/IMG]

---

