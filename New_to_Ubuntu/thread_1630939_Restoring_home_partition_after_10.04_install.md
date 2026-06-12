---
title: "Restoring home partition after 10.04 install"
date: 2010-11-25
forum: New to Ubuntu
---

### Post by gloxer54 on 2010-11-25
**[SIZE="3"][/SIZE]**Okay, I just did a clean install of 10.04 LTS from 9.10.  I did not partition my /home.  I had saved it to a usb drive via "sudo rsync -azvv /home media/media1".  I entered the same username and password in 10.04 as I had in 9.10.  No luck.  I do not seem to have the old /home.  
  So, even though I am not a newbie, I need some simple help ( if it exists) to restore my /home from the other save one on my external HD.
  Any Ideas?  Also let me know if you need more info.

---

### Post by BugBuster on 2010-11-25
If your usb drive is formatted vfat or ntfs(most likely it is) you may have lost the linux file-system attributes likes file permissions and owner information when you backed up your home.

---

### Post by oldfred on 2010-11-26
Did you follow instructions like this:
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you did use a FAT you have to reset permissions and ownership as BugBuster mentioned.

This has to commands and some discussion on how to reset. Command summary at the end.
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by C.S.Cameron on 2010-11-26
I recently did a fresh install retaining the /home partition as you did.
I recall that all I needed to do to get the new install to find home was edit fstab as shown in the page oldfred noted:

Add these lines into fstab

```

UUID=????????   /media/home    ext3          nodev,nosuid       0       2 

```

Replace???????? with the UUID number of the intended /home partition.

---

### Post by gloxer54 on 2010-11-26
Okay, the external HD partition I have used to attempt to save my /home is formatted in ext3.  So that is no problem.  I may have mis-used the rsync command from the link : [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync) .
  Now C.S. Cameron, does that command you suggest actually replace /home, as in move the /home from the external to replace the internal? Or does it just point to the external?  I need to know, if you do not mind as I do not use my external all the time.
  Let me know if more info is needed.
      thanks for the replies so far.

p.s. I did run a simulation with Grsysc and it said it failed to copy a lot.  I am glad it was only a simulation.  It would be nice if the answer was in the form GUI, but that is not necessary as long as the command line is explained.  thanks again!

---

### Post by oldfred on 2010-11-26
The fstab entry can be either your internal /home or the external, it just depends on which partition you point it to.

This was my entry when I had a separate /home on sdc9 which was an internal drive.

```
# /home was on /dev/sdc9 during installation
UUID=b8a7e331-a716-4ac1-bf58-6ac515606c6d /home           ext4    defaults        0       2
```

---

### Post by C.S.Cameron on 2010-11-26
> Now C.S. Cameron, does that command you suggest actually replace /home, as in move the /home from the external to replace the internal? Or does it just point to the external? I need to know, if you do not mind as I do not use my external all the time.

As Oldfred noted the line I quoted, when added to fstab, just points the way to the home partition when booting, whether it is on a separate partition, hard drive, thumb drive, etc.

If you have reinstalled Ubuntu without reformatting your old home partition, it should point there.

---

### Post by gloxer54 on 2010-11-27
> **oldfred said:**
> The fstab entry can be either your internal /home or the external, it just depends on which partition you point it to.

This was my entry when I had a separate /home on sdc9 which was an internal drive.

```
# /home was on /dev/sdc9 during installation
UUID=b8a7e331-a716-4ac1-bf58-6ac515606c6d /home           ext4    defaults        0       2
```
Thank you so far.  Now if someone would tell me how to replace the new /home with my old one from my external HD, I would be very happy.  This is what I wanted from the beginning. 

  Thanks,

       Mike (gloxer54)

---

### Post by C.S.Cameron on 2010-11-27
I think you can boot the Live CD and copy the home partition from external HDD to internal.

---

### Post by gloxer54 on 2010-11-27
Okay, C. S. Cameron, I had a similar thought and have found my  answer.  Using PCMan File Manager I went to my external HD and went into the /home folder (as super user mode) and copied each user folder and then went to my internal HD /home and pasted them inside there.  Then, in the System>Administration>User and Groups, I added each user (in the order of their numbers, 1001,1002, and1003 ) then logged out and back in as each.  This WORKED!!! I know this was a crazy workaround to get where I needed to go, but when in need...  Now all I need do is find out how to mark this as solved.

---

### Post by C.S.Cameron on 2010-11-27
Click on Thread Tools at the top of the page.

---

### Post by gloxer54 on 2010-11-27
Well. my idea kind of works.  All the files are there, but I do not have permission to alter them.  So....I need a better answer or a way to correct this one.  Any ideas folks?  Ask me for any information you may still need.

---

### Post by oldfred on 2010-11-27
If you moved them as root did you reset everything to owned by root?

Back to post #3 on resetting permissions & ownership.

---

### Post by C.S.Cameron on 2010-11-27
See Oldfred's first post about the use of "Rsync".
It is meant to copy home and retain permissions.

---

