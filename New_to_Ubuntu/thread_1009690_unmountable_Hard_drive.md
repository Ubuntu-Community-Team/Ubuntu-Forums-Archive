---
title: "unmountable Hard drive"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by idproc on 2008-12-12
I have just installed and made ubuntu my new os. Now, I have two harddrives in my computer. My C drive works fine, but when I click on my other drive it comes up with a box that says this can not be mounted. Can anyone offer any help. I know nothing about this os. It is an internal hard drive.

---

### Post by -kg- on 2008-12-12
OK, when you say you have two hard drives, do you mean physical hard drives or partitions?  Are you dual-booting with Windows, or is Ubuntu standalone on your hard drive(s)?

If it is standalone (i.e., no Windows), then you may be trying to mount the "Swap" drive, which you can't mount (It shouldn't even be visible for you *to* attempt to mount, though).

What type of "drive" (i.e., partition) is it?  ext2? ext3? (Linux) FAT? NTFS? (Windows, naturally) Where are you clicking on it to try to mount it? (mounting is how a drive is accessed by and from Linux.  This is done automatically under Windows for partitions with compatible file systems.It has to be done manually by clicking on it in Nautilus (same as Windows Explorer), issuing the mount command in the terminal window, or by an automated script.)

Need just a bit more information before we can successfully help you. Answer as much of the above as you can.

---

### Post by idproc on 2008-12-13
O.K.  Thanks for your help.  I have installed ubuntu as a stand alone O.s. I have two physically different hard drives. One is the C: drive that linux is installed on. The other was unplugged during installation to make sure nother was going to happen to it like accentdentally being formatted. Once I booted linux up, I hooked up the other drive. I can see it under "places" but when I click on it, it tells me that I can not mount it. That's funny because when I was trying the program out by using the CD to boot linux I would use the drive. Now that I have totally gotten rid of windows XP I can't access it anymore.

---

### Post by adult swim on 2008-12-13
go to a terminal and enter in ```
sudo fdisk -lu
```
then copy and paste what it returns here

---

### Post by idproc on 2008-12-13
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders, total 78177792 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000675f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    75923189    37961563+  83  Linux
/dev/sda2        75923190    78172289     1124550    5  Extended
/dev/sda5        75923253    78172289     1124518+  82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x21e1ad20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   160071659    80035798+   7  HPFS/NTFS
idproc@idproc-desktop:~$

---

### Post by adult swim on 2008-12-13
i really never mess with ntfs drives but a quick search suggested to run from a terminal ```
sudo modprobe ntfs
``` then try and mount the drive.  let me know if it works.

---

### Post by idproc on 2008-12-13
did not do anything. thanks for responding.

---

### Post by adult swim on 2008-12-13
i am out of ideas.  unfortunately i dont have an ntfs drive around to figure out how to do it.  i know it can be done so dont give up just yet.  im sure someone with the know how will see this thread and let you in on the secret!
EDIT: i just saw this post, you may want to give a try.  it is a GUI to get drives to mount.
[http://ubuntuforums.org/showthread.php?t=985765](http://ubuntuforums.org/showthread.php?t=985765)

---

### Post by pdtpatrick on 2008-12-13
Question .. are you trying to mount ntfs? If so then you need to have ntfs-3g installed.. look that up. You should be on your way after that.

---

### Post by idproc on 2008-12-13
Thanks I have solved the problem. I used the software of storage manager and the problem is fixed. Thank you so much for all your help.

Thanks):P)

---

### Post by vanadium on 2008-12-13
The reason your ntfs volume did not mount was that it had not been properly shut down a previous time (= the file system was not properly closed). This can happen when the drive was connected to Windows, and Windows was hibernated instead of closed down. In can also happen when the system in unproperly shut down (e.g. power outage).

The normal fix is to check the disk under MS Windows. Even just connecting and properly disconnecting might do.

ntfs is a proprietary format of MS Windows. If linux senses the partition is not 'clean', it will not mount it by default not to risk damage. You can still "force mount" such a drive however.

You do not have MS Windows anymore. In that case, I strongly recommend you to reformat that partition to ext3 format, a format that linux fully supports.

---

### Post by -kg- on 2008-12-14
> You do not have MS Windows anymore. In that case, I strongly recommend you to reformat that partition to ext3 format, a format that linux fully supports.

And I would sincerely concur.  If you are no longer using Windows in any capacity, there is no need to maintain a Windows-specific file system. It would be much better to convert that space to ext3 and use that space to it's fullest extent.

The only reason I'm maintaining a Windows installation is a couple of programs that I "can't do without."  Delorme mapping and GPS (though I fully intend checking out Virtualbox to be able to run it) and I really like MS Flight Simulator X (which is slow enough running natively under Windows...I doubt it would run well under multiple layers of OSes).

---

### Post by barbedsaber on 2008-12-14
sounds like one of those cheesy movies

"this summer, no-one is safe. From the curse, of the unmountable hardrive.(only in cinemas)"

:)

---

