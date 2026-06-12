---
title: "SD fails to mount"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by ironside on 2010-03-30
Hi everyone,

I have been searching for a solution access the internal SD reader with my Eee PC S101H (9,10) for some time. After endless searches i gave up trying to fix the problem. However the other day I thought I try inserting the SD card to see if an update had fix the problem and amazing it worked!. Anyway today I reinserted the SD card to access it and of course it didn't work.

Now I have no idea how to solve this problem and from what I am seeing in the forums I am not seeing a solution either, hence I am posting a new msg to see if anyone has a solution. 

Your guidance would be appreciated.

---

### Post by readycarpenter on 2010-03-31
what kind of error are you getting? most sd cards are formatted to fat32 or ntfs these are windows partition types, also ubuntu will not mount if the drive was not properly unmounted last time, to fix this try

```
sudo mkdir /media/sdcard
sudo mount /dev/(yourdevice) /media/sdcard -o force
```

and make sure to unmount it, don't just pull it out when finished
next time you put it in should auto mount

cheers

---

### Post by ironside on 2010-03-31
unfortunately it doesn't mount at all, no error msg etc. As for your command I receive the error:
 cannot create directory `/media/sdcard': File exists

sorry still a newbie

---

### Post by readycarpenter on 2010-03-31
> unfortunately it doesn't mount at all, no error msg etc. As for your command I receive the error:
cannot create directory `/media/sdcard': File exists

as for mkdir /media/sdcard this can be any folder, you are just creating a folder then mounting the card to it, 
I suspect you did successfully run mkdir /media/sdcard at least once or it would not exist.

so now just run
```
sudo mount /dev/(yourdevice) /media/sdcard -o force
```

and tell me what you get

---

### Post by llamabr on 2010-03-31
Or, if you don't know what the device is, pull it out, count to 10, put it back in, count 10 again, and then post the output of:

```
dmesg | tail
```

---

