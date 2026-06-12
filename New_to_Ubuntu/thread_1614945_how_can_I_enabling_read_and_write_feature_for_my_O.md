---
title: "how can I enabling read and write feature for my OSX HFS+ partition"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by X-Tarzan on 2010-11-06
dear sensei i want to save some files on my mac HFS+ partition, I was very sad, I can only see my file, but can not save it on my HFS+ partition , said i need permissions, what should i do

---

### Post by srs5694 on 2010-11-06
Linux's HFS+ driver only supports writing to a disk if it has no journal. It is possible to disable the journal on HFS+ from within OS X, but I don't recall the details of how to do this. There's also a patch or procedure to enable Linux to write to a journaled HFS+ volume, but again, I don't recall the details.

If you just want to copy one or two files, your best bet is to use some other medium, like a USB flash drive, as temporary storage; write the files to that volume in Linux, then boot OS X and copy them to the OS X disk. If you want to be able to exchange files on a regular basis, your best bet is to create a separate data sharing/exchange partition, using the unjournaled version of HFS+ on that partition. (It's generally unwise to allow any OS regular write access to another OS's main boot partition, so I don't recommend using your regular OS X partition for this purpose.)

Note that there may be user ID (UID) and group ID (GID) issues when exchanging files. OS X and Linux both use Unix-style ownership and permissions, but OS X seems to start numbering its accounts at UID 501, whereas Ubuntu begins at 1000. Data exchange is easier if you synchronize the UID values between OSes, by changing the OS X UID to 1000 or the Ubuntu UID to 501 (for the first user; values go up for subsequent users). In Ubuntu, you can use the usermod command to do this, followed by chmod to change the ownership on existing files to match the new UID value. I'm sure this is possible in OS X, too, but I don't know the details offhand.

---

### Post by coffeecat on 2010-11-06
> **srs5694 said:**
> It is possible to disable the journal on HFS+ from within OS X, but I don't recall the details of how to do this.

I could only find a way to disable the journal by using the MacOS terminal. The following seemed to work for me in Snow Leopard.

To disable journal in HFS+, open a terminal and:

```
diskutil disableJournal /Volumes/VolumeName
```@X-Tarzan, that of course is for a mounted external HFS+ drive/partition in MacOS. If you're not sure of VolumeName, 'ls /Volumes/' in the MacOS terminal will reveal it.

Having said all that, I don't think you want to be disabling the journal on the partition where your Mac operating system resides. A separate partition or a FAT-32 formatted USB drive as srs5694 suggests might be better.

---

### Post by linux-hack on 2010-11-06
You can simply mount the partition with the option force in the /etc/fstarb

---

### Post by X-Tarzan on 2010-11-06
well thanks for all your guidance , i use HFS+ journaled ,after i thought i better keep it in the flashdisk , is there some kind tools like macdrive or similar , so i be able to access HFS + Journaled partition without worrying about can damage it

---

