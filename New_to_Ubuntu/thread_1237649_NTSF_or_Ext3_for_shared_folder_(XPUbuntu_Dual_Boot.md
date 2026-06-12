---
title: "NTSF or Ext3 for shared folder (XP/Ubuntu Dual Boot)"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by MAJcrew35 on 2009-08-11
I am planning on dual booting XP and UNR on my new netbook, and I was going to create a shared partition. I know that Ubuntu can now read/write NTSF, and there exists some software that allows XP to read/write Ext3. Which would be the better choice for the shared partition?

Thanks!

---

### Post by VCoolio on 2009-08-11
The ntfs mounting in ubuntu may take some % cpu (not too bad though). The ext3 patch in windows will suggest to reformat the new found partition (sigh), so be careful with that. The best option is not to dual boot and use ubuntu only. Way beyond, second choice, I'd say use ntfs.

---

### Post by mrgreggie on 2009-08-11
I'll second the call to use NTFS to facilitate Windows access.  I use it for my one external drive at the moment without any trouble.

---

### Post by hyperdude111 on 2009-08-11
I recommend either FAT32 or NTFS for your shared partition as both ubuntu and windows can read/write with no issues. 

There is software available to read EX2 and EX3 from any windows OS. [http://www.fs-driver.org/](http://www.fs-driver.org/) This however does not include EXT4 yet.

---

### Post by bdentremont on 2009-08-12
My experience with NTFS on Ubuntu has also been pretty good, but I will mention a couple issues:

1) NTFS and FAT do not do Unix file permissions and the linux "chmod" command won't work on this drive.  This may not mean much to you now, but if you use this as your home directory and start tinkering in Ubuntu, you may run across this issue.  Additional information:
[https://answers.launchpad.net/ubuntu/+source/ntfs-3g/+question/39026]("https://answers.launchpad.net/ubuntu/+source/ntfs-3g/+question/39026")

2) At least the last I checked, NTFS-3G driver used by Ubuntu for NTFS doesn't use the journal of the NTFS journaling file system.  This is important because if the drive is not cleanly released from Windows, Ubuntu will refuse to mount it until Windows is restarted and shutdown properly.  Thus, if Windows crashes and you think you will boot Ubuntu, you could be in for a nasty surprise at first. Additional information:
[http://ubuntuforums.org/showthread.php?t=217009&page=102]("http://ubuntuforums.org/showthread.php?t=217009&page=102")

Nether of these is a deal killer and I suspect similar annoyances the other way (EXT3 on Windows), but hopefully awareness will save you pain when they occur and you know that these are related to your disk format.

---

### Post by LunaticHiatus on 2009-08-12
why not fat32?

---

### Post by VCoolio on 2009-08-12
fat32 doesn't support file sizes above 4 GiB. If you don't have these (like dvd-images) it may be an option, but it's also not a journaling fs, thus unsafe in case of a crash or power loss.

---

### Post by MAJcrew35 on 2009-08-12
Thanks for the replies everyone! NTFS it is.

---

