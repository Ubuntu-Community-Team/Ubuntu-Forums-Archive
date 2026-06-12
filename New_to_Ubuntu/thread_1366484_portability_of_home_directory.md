---
title: "portability of home directory?"
date: 2009-12-28
forum: New to Ubuntu
---

### Post by MichaelBurns on 2009-12-28
How much of/what kind of a hassle should I expect to encounter if I simply copy a xubuntu /home/user/ directory, say onto a flash drive, and then copy it into the /home/ directory of some other Linux distribution's file system?  Will the user account be usable immediately?  If not, what will I need to do in order to have the user account up and running in the other distribution?

I'm asking for two reasons:  1)  I think that I might change my mom from xubuntu back to ubuntu.  2)  It will help me better understand what Linux actually is, in general.

---

### Post by gsmanners on 2009-12-28
If it's the same version of Ubuntu/Xubuntu I doubt there will be any problems. If it's one version up or down, you might run into a problem with one or two apps, but I highly doubt it.

The real problem you'd run into is the exact method you use for archiving the files. If you just copy the files to a FAT32 or NTFS formatted device, you'll lose the permission flags. What you need to do is create a tar.gz archive of the /home folder and then copy that to your storage device.

---

### Post by phillw on 2009-12-28
> **gsmanners said:**
> If it's the same version of Ubuntu/Xubuntu I doubt there will be any problems. If it's one version up or down, you might run into a problem with one or two apps, but I highly doubt it.

The real problem you'd run into is the exact method you use for archiving the files. If you just copy the files to a FAT32 or NTFS formatted device, you'll lose the permission flags. What you need to do is create a tar.gz archive of the /home folder and then copy that to your storage device.

+1, tar allows the retention of ownership. Be aware tho' if your UID on the two machines is different, then you're going to have permissions problems.

```

cat /etc/passwd 
```
look for your user-name
> phillw:x:1001:1001:Phill. Whiteside,,,:/home/phillw:/bin/bash

the 1001, above is both by UID (user number), and on the second occurance, my GID (Group number)

The UID specifically has to be the same on both installs - else you will have to re-assign either ownership or UID each time you do a transfer.

I use rsync for my /home area - as it's not too big. - but as noted, you do need the device being backed up TO to be permission aware on it's file system.

Regards,

Phill.

---

### Post by Raistlin355 on 2009-12-28
This is how I have been "upgrading" my installs.  I use rsync to copy my home directory then install new version and rsync my home directory back to its new "home".  I have never had a problem doing this.

---

### Post by MichaelBurns on 2009-12-28
OK, I'm seeing a theme in common with a similar question that I asked about backing up the /home/ directory:  tar or rsync.  I will definitely look into those two commands.  (Well, I'm already familiar with tar, but I'll read up on it anyway.)

One point that I'm unclear on:  are y'all assuming that the user account will already exist in the new distribution?  Basically, I'm looking for a way to move the entire user account, files and settings and even passwords, to a fresh new installation, without any input from the user.

---

### Post by Raistlin355 on 2009-12-28
I do create a new user using the same name and rsync the old data to the new location.  I don't think I havew ever tried to do it without creating a user account, I shall try it and let ya know.

---

### Post by audiomick on 2009-12-28
> **MichaelBurns said:**
> 
One point that I'm unclear on:  are y'all assuming that the user account will already exist in the new distribution?  Basically, I'm looking for a way to move the entire user account, files and settings and even passwords, to a fresh new installation, without any input from the user.

I think it has to be. I know if you want to re-use, i.e. re-mount unchanged a home partition in a fresh install, you have to set up an identical user name and password in the new install to that which was in the old install.

---

### Post by jim Kane on 2009-12-28
> **MichaelBurns said:**
> How much of/what kind of a hassle should I expect to encounter if I simply copy a xubuntu /home/user/ directory, say onto a flash drive, .

                                       you can use sbackup from the repository 
    [LEFT]i have tested this, saving the backup home/usr to a usb drive from 8.04 - 9.10 xubuntu works perfectly. [/LEFT]

---

### Post by MichaelBurns on 2009-12-28
Perhaps a naive question:
Shouldn't there be some system files that I can copy to take care of this?  E.g. /etc/passwd

---

### Post by phillw on 2009-12-28
> **MichaelBurns said:**
> Perhaps a naive question:
Shouldn't there be some system files that I can copy to take care of this?  E.g. /etc/passwd

Copying over /etc/passwd & /etc/shadow across two different ubuntu's is IMHO - asking for trouble. Just have a user set up with the same name on both (I had to alter my UID in /etc/pawsswd for rsync to work, as I was 1000 on 10.04 and had a UID of 1001 on 9.10, so, just altered /etc/passwd on 10.04 to make it 1001)

That's why I added the bit about UID's.

Phill.

---

