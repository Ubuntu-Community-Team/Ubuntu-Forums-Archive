---
title: "Backup Files From Ubuntu To Windows Share?"
date: 2007-11-14
forum: Networking &amp; Wireless
---

### Post by martynp on 2007-11-14
Hi,

I am guessing this has been asked many times but I just don't seem to be able to find the answer so any help would be greatly appreciated.

I am running gutsy on my Laptop. I keep all my music and video etc on my Desktop and stream them via my wireless network.

I have a smb share linking the 2 together. I use Totem and Rythmnbox as the can browse my local shares unlike programs not associated with gnome.

I want to regularly backup a few important files to my Windows share (firefox backups, Thunderbird backups, that sort of thing). Currently, I have to use Nautilus and just drag and drop the files I want to backup manually.

Is there any program or script that I can do this automatically even if I have to do it by manually clicking 'backup' that's OK but just someway of choosing the files to backup and shipping them across the local wireless LAN.

I have tried sbackup but it only does SSH or FTP which I don't want to setup.

Any help would be great?

Many Thanks

---

### Post by ukripper on 2007-11-14
Try this guide very quick backup [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

More info on TAR backup [https://help.ubuntu.com/community/BackupYourSystem/TAR](https://help.ubuntu.com/community/BackupYourSystem/TAR)


i personally use TAR backup and also mondo [http://www.mondorescue.com/](http://www.mondorescue.com/)

---

### Post by martynp on 2007-11-14
Thanks for this, an interesting article, but not quite what I am looking for.

This seems to cover backing up your whole system. I basically want to 'cherry pick' a few important files and batch copy them to a windows share via SMB

Any further help would be appreciated.

Thanks

---

### Post by Peter09 on 2007-11-14
Try SimpleBackup it exactly what you want.

---

### Post by ukripper on 2007-11-14
I'd create  tar backup for specific file and then write a shell script which would dump my tar backup onto windows share using smb or ssh.

---

### Post by martynp on 2007-11-14
Peter09....

I installed SimpleBackup but it gave me no shortcuts anywhere. When I ran it from terminal i got the missing .conf error. I then created a blank .conf and ran it again and it started asking for parameters. I did some digging for what should be in the script but to no avail.

Any further help would be appreciated.

Thanks

---

### Post by Peter09 on 2007-11-14
I get a couple of links in System->Administration

One is named Simple Backup Config, the other is Simple Backup Restore

---

### Post by martynp on 2007-11-15
Ahh,

In that case you are installing 'sbackup' not 'simplebackup'. There is a difference. 'sbackup' is what started me with all this as it won't backup via SMB.

Thanks anyway.

---

### Post by Peter09 on 2007-11-15
sorry about the confusion.

I am using sbackup to backup across my windows shares from a Ubuntu machine.

Not sure what your problem is with it. (Note that both shares are mounted in fstab)

---

### Post by ukripper on 2007-11-15
> **martynp said:**
> Ahh,

In that case you are installing 'sbackup' not 'simplebackup'. There is a difference. 'sbackup' is what started me with all this as it won't backup via SMB.

Thanks anyway.

i think this may help - [http://www.linuxjournal.com/article/4360](http://www.linuxjournal.com/article/4360)

---

