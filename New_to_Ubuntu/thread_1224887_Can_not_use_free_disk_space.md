---
title: "Can not use free disk space"
date: 2009-07-27
forum: New to Ubuntu
---

### Post by thrasher22 on 2009-07-27
For some reason, despite there being over 89gb free on my HD ubuntu believes there is only 11gb left.

I initially thought the partition needed to be adjusted as to get this I had deleted all my music and movies from windows (slowly switching off windows :D). However when I used gparted it lists 3 partitions:
DellUtility - 54Mb
DellRestore - 2.75Gb 
/boot, /host - 146Gb (89Gb free)

Is there any way I can still adjust how much is set for Ubuntu? I'd rather not delete windows yet, but I need more than the 11Gb just for my music...

Any help is greatly appreciated!

---

### Post by admiralspark on 2009-07-27
Well, everyone please correct me if I'm wrong, but--
I believe that even if you delete 99% of all your windows junk, the HDD will still read 146gb as belonging to the windows partition. You actually have to use a program to adjust it. Since you used Gparted, I would assume at this moment in time that you have adjusted the Linux partition to take up most of what was once windows space?
I would suggest this: split the HDD into three partitions--one for the Windows OS, one for Ubuntu, and the last (and largest by far) a FAT32 shared (or Home) partition. You can save all of your things on that partition for both OS's and if either OS is screwed up, you won't lose the valuable data. 
Check here for some more info: [http://ubuntuforums.org/showthread.php?t=1130263 ]("http://ubuntuforums.org/showthread.php?t=1130263&highlight=adjusting+partition+size")

Let us know what you gain from that (and the two links in the second post).

Also, maybe using Wubi would be a good alternative, being able to keep both OS's and not adjust the partitions? 

And finally, something I just noticed: the last and largest of your partitions is /host...........host is Windows and all of it's included files, unless my copy of Ubuntu is special.

Correct me if I'm wrong?

---

### Post by LookTJ on 2009-07-27
To get a better idea of how you setup your partitions

post both ```
sudo fdisk -l
```
and ```
df -h
```

:)

---

### Post by llamabr on 2009-07-27
Post the output of:

```
df -h
```

---

### Post by mapes12 on 2009-07-28
This "Disk Full" HowTo may help:

[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

