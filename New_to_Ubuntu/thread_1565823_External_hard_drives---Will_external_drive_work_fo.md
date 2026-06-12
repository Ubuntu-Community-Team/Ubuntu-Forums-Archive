---
title: "External hard drives---Will external drive work for unbuntu and Win-XP?"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by oldpath on 2010-09-01
I need to back up photos from both sides of an old dual boot computer with one side Ubuntu and the other Win-XP.  I notice some external drives come with Windows centric software.  Will there be any problems getting photos downloaded from this computer?

  I have not yet bought an external hard drive and would appreciate any recommendations along that line.  

Once I have my photos off of the Windows side I will remove Win-XP from the machine.  The computer is getting old at 9 years of age. Time to retire the machine soon.

The computer has USB 2 ports

Oldpath

---

### Post by TNT1 on 2010-09-01
My latest external HDD came with windows software installed, I formatted with ext4. What you can do, is boot into your linux os, and access your windows files from there and copy direct to your external HDD. If you are going to bin windows anyway, then it doesn't matter what software is pre-installed on the drove. I'd format it with ext3 or ext4, and ntfs as a last bail out in case windows ever has to see it. Or partition the drive and put some as ntfs and some as ext4.

---

### Post by egalvan on 2010-09-01
Linux has fairly good write support for NTFS, so moving fiels TO the external drive should not be a problem.

Note that any "Windows-centric" software will of course NOT run under Linux.

if the Windows side of that machine is still running well, then of course you could use the back-up software...
BUT JUST BE SURE IT DOES NOT SAVE TO A PROPRIETARY SYSTEM. otherwise you will need that exact same software to read it again.
TEST IT... you MUST BE ABLE TO READ THE BACKED-UP FILES FROM ANY OTHER MACHINE...

Which is why Linux is recommended. 
Or do a "move files" operation under Windows.


Formatting as NTFS will give you the ability to access from any Windows machine )XP or above,of course).
Formatting as ext3 or ext4 will give you the advanced journaling capabilities inherent in Linux FS, but you will be a bit restricted in what machine can read it...
Or connect it via a networked machine, and let SAMBA handle it.


But I will repeat the most important advice....

**FULLY TEST** ANY METHOD YOU USE TO **BE SURE** THAT FILES ARE BEING CORRECTLY WRITTEN TO THE NEW DRIVE,
 AND **MAKE SURE** THAT YOU CAN READ THEM...
**BEFORE** YOU COMMIT TO THE CHANGES.

I've seen too many folks blithely "backing up" precious files...
replacing machines or drives...
only to find that the "back-up" did not work.

---

### Post by clive littlewood on 2010-09-01
Hi

I bought an WD passport usb drive and use it as "plug and play" across Ubuntu and windows 7

I did not install the windows software out of the box.

Another simple file sharing option (if not many files) is drop box which is cross platform.

Clive

---

### Post by oldpath on 2010-09-01
Thanks for all the advice.  I think I will be very careful before backing off files to an external hard drive.  You all have given me plenty to work with.

Oldpath

---

