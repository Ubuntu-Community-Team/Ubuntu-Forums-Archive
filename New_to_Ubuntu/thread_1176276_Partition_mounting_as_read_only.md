---
title: "Partition mounting as read only"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by Tootler on 2009-06-02
I have a dual boot Ubuntu/WinXP system with my data held on a FAT32 partition so that it is accessible to both Ubuntu and Windows. This worked fine until today when I started up the computer and was unable to edit my documents as they were loading as read only. I have checked the permissions on a selection documents and they are set as "Owner root, access read and write" etc. Similarly folders are set as "Owner root, access create and delete files" etc. If you click backwards and forwards a bit on the file browser the padlock symbol starts to appear, eventually showing on everything so it looks as if the whole partition is mounting as read only.

I usually hibernate Windows to speed load up, so I wondered if something in Windows was causing problems so I went to Windows, checked the files there and they were loading up as read/write there. So I shut Windows down completely and went back to Ubuntu and the problem was still there.

I have changed nothing, especially not fstab and there have been no updates installed immediately prior to the problem appearing.

Just in case, here is the contents of fstab on my system:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc        defaults    0   0
# /dev/sda3
UUID=ed332988-aaf5-4149-86d8-4e7c8ac7cf4b     /               ext3        defaults,errors=remount-ro    0   1
# /dev/sda2
UUID=DAD0B335D0B316AB       /media/drv0       ntfs-3g         defaults      0   0

# /dev/sda4
UUID=adfbcc7a-bff3-4142-891a-1b58e0286a67      none            swap        sw          0   0

# /dev/sda1
UUID=1C80-61A1  /media/DATA      vfat    user,fmask=0111,dmask=0000   0   0        
 
```

sda1 is my data partition and sda2 is the Windows partition.

Any help appreciated but please don't simply suggest changing FAT to NTFS, I do not feel it is worth the effort and anyway, will probably not resolve the problem.

Cheers

Geoff

---

### Post by MichaelSammels on 2009-06-02
Hey, try using the Storage Device Manager:

```
sudo apt-get install pysdm
```
```
sudo pysdm
```

Unmount the partition, and edit the options so it won't mount as read only. Make sure you enable options such as "Allow other users to mount", etc.

---

### Post by regala on 2009-06-02
> **Tootler said:**
> 
I usually hibernate Windows to speed load up, so I wondered if something in Windows was causing problems so I went to Windows, checked the files there and they were loading up as read/write there. So I shut Windows down completely and went back to Ubuntu and the problem was still there.


when switching OS-s you should NEVER hibernate, because filesystems are not safely closed (not even unsafely, they're left as though the system is still running). This is the best way to destroy a filesystem beyond repair.

1) windows left the filesystem in an inconsistent state, doesn't care as it will get it back later, with the ENTIRE OS back where it was, file dscriptors opened, postponed IO requests.
2) Linux finds a filesystem in an inconsistent state, in such a state, it cannot safely enable writing on it (safety before everything), but it closes a certain mess, "finishes" some open files...
3) windows boots back, at the point it left in 1). It resumes every posstponed IO on the filesystems, maybe writing on blocks that would have been safe to write to 2 boots ago, but which are use by other structures put there by any repair operation occured in 2)

...
never EVER do that. hibernation puts everything in an intermediate state only safely usable or recoverable by the OS that hibernates.

In your case, I guess windows detected something wrong on your fat32 the second boot and never really resumed, but whatever happened you should force fsck this partition before harm is permanent on this storage.

i guess chdsk on Windows should do.
Oh and no need to keep old Fat32 partitions to share between the two OS, windows and Linux can now write on NTFS.

br, mathieu

---

### Post by Tootler on 2009-06-02
Sorted (hopefully)

I found a corrupt "text" file. It was a saved email which was an great deal larger than it should have been so I suspect it carried a "payload". I had to go to windows to delete it, which I did - completely (ie not just sent to the recycle bin). After closing Windows and rebooting into Ubuntu, all worked OK.

> Oh and no need to keep old Fat32 partitions to share between the two OS, windows and Linux can now write on NTFS.

I know this now, but didn't at the time I set it up. In fact, everything I read at the time I first tried Ubuntu said that Linux can read but not write to NTFS, hence the reason for the FAT partition. I don't feel inclined to reformat now as it works so I see no point in reformatting to a different file system.

Thanks for the advice about hibernating Windows. The trouble is that my Windows install is getting long in the tooth now and can take up to 10 mins. to fully load even though I have removed a lot of programs I am no longer using and have cut down on the apps. that load on startup.

---

### Post by Mornedhel on 2009-06-02
> **Tootler said:**
> I know this now, but didn't at the time I set it up. In fact, everything I read at the time I first tried Ubuntu said that Linux can read but not write to NTFS, hence the reason for the FAT partition. I don't feel inclined to reformat now as it works so I see no point in reformatting to a different file system.

Unlike NTFS, FAT32 doesn't support files larger than 4GB, which are getting more and more common in this day of DVD ISOs and Bluray rips. NTFS also handles sparse files, while FAT32 doesn't. This makes NTFS a generally much better filesystem than FAT32 when dealing with torrenting, for instance.

---

### Post by mal1958 on 2009-06-02
Glad you resolved the prob.  I would highly and strongly recommend that you avoid Hibernate like it was the plague.  At least where windows is concerned.  Using that is an invatation to disaster.

     I know that Microsoft says that it's safe, but they are the ones who said windows was the fastest, best OS out there.  Of course, if that was the case then why are there so many Ubuntu users? :p

Mike

---

