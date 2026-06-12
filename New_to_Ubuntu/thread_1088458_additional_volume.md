---
title: "additional volume"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by dimitriv on 2009-03-06
hi

Under intrepid is it possible to create an additional volume which potentially could be accessed from another OS?. I've got capacity on the drive and would like to have a data volume that's accessible from Ubuntu, but in the event that I start dual booting and using another OS such as windows, both OS can read/write files on that volume? What's the best Ubuntu app for managing the disk config (I'm very familiar with Windows Disk Management interface)?

thank you

---

### Post by dzark on 2009-03-06
Gparted should already be installed. System -> Administrator -> Partition Editor

Remember to back your important data up before playing with partitions. Always. You will be unable to resize your boot partition, so maybe boot off liveCD?

---

### Post by dimitriv on 2009-03-06
I added Gparted, that'll do the trick, thanks.
Can an EXT3 partition be read by Windows/ best to use FAT32 (NTFS greyed out)?

---

### Post by dzark on 2009-03-06
Windows can only read FAT/FAT32/NTFS file systems, so..

I have [Ext2 IFS]("http://www.fs-driver.org/") installed on my windows boxes, allows read/write on ext3 formated partitions. You have to remember though, as windows doesn't handle file permissions/ownerships all data on the partition is visible. Quite nice havin my friend discover my pr0n collection....

---

### Post by dimitriv on 2009-03-07
gotta have those permissions, eh!

Thanks

---

### Post by dimitriv on 2009-03-07
Using Gparted I created an Ext3 Partition. After authentication the new media mounts (as /media/disk) but it doesn't allow me to create files/folders or copy data on to the drive. what do i need to do to have R/W access to this drive from Ubuntu?  Thank you

---

### Post by dzark on 2009-03-07
whats the exact error message?

what if you try copying a file in terminal?

```
cp /home/yourusernamehere/filename /media/disk
```

---

### Post by dimitriv on 2009-03-07
hi dzark

In the UI all the options are/were greyed out.

Through the terminal i get
cp: cannot create regular file '/media/disk/filename': Permission Denied

Permissions, trouble without them, trouble with them!

---

### Post by dzark on 2009-03-07
UI of gParted?

whatabout a ```
sudo cp /home/username/filename /media/disk
```

how did you mount it? by clicking on the partition in the left filebrowser window

---

### Post by theozzlives on 2009-03-07
```
sudo chown <username> /media/disk
```

---

### Post by dimitriv on 2009-03-07
dzark - using Sudo it worked

theozzlives - magic. ran that and now i've got r/w access. incidentally should I have had to run that command (was something not right or will it always be a necessary step after partition is created and mounted?)

Thank you

---

