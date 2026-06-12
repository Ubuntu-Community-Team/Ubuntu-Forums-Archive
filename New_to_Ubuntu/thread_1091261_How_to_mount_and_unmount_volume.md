---
title: "How to mount and unmount volume?"
date: 2009-03-09
forum: New to Ubuntu
---

### Post by amrutayan on 2009-03-09
i am using xp with ubuntu.

while i am using xp i want to use the volume used by ubuntu.

and how can i mount or unmount the drives of xp in ubuntu??

plz help me out.............

---

### Post by carml on 2009-03-09
There a software to let Windows see your Ubuntu drive, but I don't remember the name.By default only Ubuntu can see Windows,to solve your problem you can also save file under Windows,when using Ubuntu or you can create a shared partition where to save file so that you can access with both OS.
I hope this can help you :) .

---

### Post by logos34 on 2009-03-09
[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.10%20(Intrepid%20Ibex)%20and%20Ubuntu%208.04%20LTS%20(Hardy%20Heron](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G#Ubuntu%208.10%20(Intrepid%20Ibex)%20and%20Ubuntu%208.04%20LTS%20(Hardy%20Heron))

[http://www.fs-driver.org/](http://www.fs-driver.org/)

good luck

---

### Post by juanvdb on 2009-03-09
The software is called EXT2FS, but this will only work with EXT2 and EXT3 filesystems. 
The home page is at [http://e2fsprogs.sourceforge.net/ext2.html](http://e2fsprogs.sourceforge.net/ext2.html)

---

### Post by Berserker v7 on 2009-03-09
Linux drives can be read from windows using explorer2fs or similar softwares... disk writes from xp is not possible as far as i know...

If you are on Ubuntu, you will get list of all drives(including xp drives) in the side pane of the file browser... just click on them to mount... on older systems, you may have to use mount/ntfs-3g command from the terminal... not sure really ;)

---

