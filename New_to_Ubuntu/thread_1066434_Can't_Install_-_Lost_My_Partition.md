---
title: "Can't Install - Lost My Partition"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Joe Gandalf on 2009-02-10
I tried to install 8.10 (main OS is Win 7 beta). The install hung up towards the end. When I tried to reinstall, the program can no longer see the partition it had taken from the primary Win partition. How can I restore the 70 GB chunk back to Win, so I can reassign that chunk to Ubuntu? Or, what other options have I got? I want a dual boot system. I am confused...

Joe

---

### Post by yeats on 2009-02-10
First things first - are you still able to boot into Windows?  When you downloaded the Ubuntu .iso, did you check the image with winm5dsum and verify the disc integrity from the CD start menu?  Are you able to boot in with the live CD?

---

### Post by caljohnsmith on 2009-02-11
How about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And please post the output. That will tell us what your current partition scheme is.

---

### Post by Joe Gandalf on 2009-02-11
Thanks for your help. Here are the results, (with a caveat):

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0666d26b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   314697284   157348611    7  HPFS/NTFS
/dev/sda2       314697409   625137663   155220127+   f  W95 Ext'd (LBA)
/dev/sda5       314697728   463712255    74507264    7  HPFS/NTFS
/dev/sda6       463714304   625137663    80711680    7  HPFS/NTFS

The above are the results as of now. I need to point out that after trying some things last night, I went into Win, and ended up reformatting the partition that had contained the Ubuntu install. It is now NTFS, as I was hoping to merge it back into the primary, bootable Win partition (to get back to where I was before I tried the ubuntu install). However, I wan't able to accomplish that, so the ex-ubuntu partition is now just an empty NTFS partition, with no drive letter currently assigned.

Can I install ubuntu into that partition for a dual boot system, or do I need to restore the "lost" partition back into the primary? (FWIW, in Win, the 'merge'(?) menu command is always greyed out.)

Joe

---

### Post by Joe Gandalf on 2009-02-11
To Chris:

Yeah, I still can get into Windows. I never did check the CDROM, but it still boots OK - I'm answering these messages from within the live CD boot.

Joe

---

### Post by caljohnsmith on 2009-02-11
If you want to try reinstalling Ubuntu again, how about booting your Live CD, open gparted (System > Admin > Partition Editor), delete the sda6 NTFS partition, create a new ext3 logical partition to replace it, but leave some room at the end of your drive for a swap partition. Then create a swap logical partition with that space. Once you have those two partitions set up, try installing Ubuntu again, and set the mount point on the ext3 partition you created for Ubuntu as "/" or root, and also set the mount point on your swap partition as "swap". Then let us know how that goes.

---

### Post by Joe Gandalf on 2009-02-11
caljohnsmith wrote:
> If you want to try reinstalling Ubuntu again, how about booting your Live CD, open gparted (System > Admin > Partition Editor), delete the sda6 NTFS partition, create a new ext3 logical partition to replace it, but leave some room at the end of your drive for a swap partition. Then create a swap logical partition with that space. 

OK, so far, so good

> Once you have those two partitions set up, try installing Ubuntu again, and set the mount point on the ext3 partition you created for Ubuntu as "/" or root, and also set the mount point on your swap partition as "swap". Then let us know how that goes.

Here, I'm lost. When I try an install, I get no further than the 4th screen (where the "prepare partitions" selection normally shows), but there is no info displayed. I tried with the volume mounted and unmounted, but nothing shows up. If I try to go to the next step anyway, I get the message: 
"No root file system is defined. Please correct this from the partitioning menu."

Currently, this is the HD status:
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0666d26b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   314697284   157348611    7  HPFS/NTFS
/dev/sda2       314697409   625137663   155220127+   f  W95 Ext'd (LBA)
/dev/sda5       314697728   463712255    74507264    7  HPFS/NTFS
/dev/sda6       463748418   623097089    79674336   83  Linux
/dev/sda7       623097153   625137344     1020096   82  Linux swap / Solaris

I refuse to give up on this, but it does seem to be kicking my ***; I'm so used to DOS & Windows conventions that I fear I'm on the bottom of a steep learning curve.

Bedtime now - big audit at work tomorrow.

---

### Post by caljohnsmith on 2009-02-11
How about taking a look at this Ubuntu installation tutorial:

[http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html](http://mywebsite.bigpond.net.au/dfelderh/linuxmaniac/p23.html)

Be sure to choose the "manual" partition option in the installer; I think if you right-click on your sda6 ext3 partition when it shows your existing partitions, you can select "edit" or "use partition" or something of that sort, and you will then have the chance to set the "mount point." Let me know how that goes.

---

### Post by Joe Gandalf on 2009-02-12
Thanks for the new info. Something I did last night fouled up my Windows partition, & it wouldn't boot. Just now got that repaired, so I guess tomorrow will be my next chance to try out that technique. I appreciate your continued support (and patience).

Joe

(I also don't understand why this forum found it necessary to auto-censor my reference to posterior anatomy; I like to see discussions kept at a civil level, but this is ridiculous. Seems as though for everyone offended by that word, another would be offended by the suppression of same. Oh, well...)

---

### Post by Joe Gandalf on 2009-02-14
Well , hot d*** (uh, I mean good golly, Miss Molly) - it worked!

The technique you referenced (p 23) worked very well. I only had to install a driver for my nvidia card, so I could do better than 800 x 600. Even still, after the driver install reboot, I got a message (from my monitor) telling me that the input signal was out of range, and the monitor would go to sleep. It took a few power-down sessions of the monitor before I was able to get the display settings up and change them before it shut down again. Funny that this monitor can handle 1680 x 1050, but it thought the video signal was out of its range. 

All's well that ends well...

Again, thank you very much for your help. Now that Ubuntu is up & running, I can start to learn Linux, and wean myself off of my MS dependency.

Joe

---

### Post by caljohnsmith on 2009-02-14
That's great news, glad to hear you installed Ubuntu successfully. Cheers and enjoy your new install. :)

---

