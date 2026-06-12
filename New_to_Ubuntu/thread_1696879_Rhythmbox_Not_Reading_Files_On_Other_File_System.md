---
title: "Rhythmbox Not Reading Files On Other File System"
date: 2011-02-28
forum: New to Ubuntu
---

### Post by inukai on 2011-02-28
I have my music files on a Windows (NTFS) partition on my HDD. I have Rhythmbox set up to look in that folder for music files and automatically add them to my library. The problem is that after a reboot Rhythmbox remains empty unless I goto File -> Import Folder... and manually select the folder. It seems to work when I've gone into that system through Linux's File Manager before loading Rhytmbox. Is there a way to fix this? Thanks.

---

### Post by pressko on 2011-02-28
Hi man,


Is your NTFS partition mounted automatically during the OS start up ? If it's not, you are not able to access your files until u mount the NTFS part. by clicking on partition icon . There are several ways to  mount NTFS during the start up , the easiest way is with NTFS configuration tool.

---

### Post by inukai on 2011-02-28
I'm pretty sure it's auto-mounted on startup. When I start up I can see the 376GB Filesystem with the eject icon, and I can acsess the files without having to run a mount command, but Rhythmbox can't unless I've accessed the folder first.

---

### Post by inukai on 2011-03-15
Any help here?

---

### Post by mcduck on 2011-03-15
Well, that actually sounds like the drive *isn't* auto-mounted on startup, but rather auto-mounted when you *access* it.

You might want to add the drive into /etc/fstab to get it to automount on startup.

Here's a guide for fstab: [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

..and if you want more help for configuring the drive in fstab, please run following commands and post the output and the contents of /etc/fstab here:
```

sudo fdisk -l
blkid
```

---

