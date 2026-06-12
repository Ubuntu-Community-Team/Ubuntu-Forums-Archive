---
title: "Broken links to Windows partition on reboot"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by pacojoseph on 2011-01-13
Ok, I'm triple booting to Ubuntu, Windows 7 and XP on my laptop. All of my media files are in the Windows 7 partition. I have tried placing a link on my Ubuntu desktop to these media file so I don't have to navigate to them every time I want to open an MP3 or a video. The link will work until I reboot, after which clicking on a link results in a broken link message. If I click on my Windows 7 partition in the"places" menu, the link then un-breaks and becomes usable. Is there any way to link to folders on another partition without the link breaking every time I reboot?

---

### Post by marin123 on 2011-01-13
you cannot access those places through shortcuts because partitions are not mounted. you have to mount them after each reboot to access files through shortcuts.

install ntfs-config:

```
sudo apt-get install ntfs-config
```

that will help you automount ntfs partitions on startup...

---

### Post by Mark Phelps on 2011-01-13
Need to be cautious here ... if the files are in a Win7 OS partition, you need to ensure that one of the following is true:
1) You only mount the partition read-only
2) If you do mount the partition read-write, you do NOT make any updates to the files in that partition.

Mounting a Win7 OS partition read/write in Linux is asking for trouble.  IF anything happens along the lines of unclean dismounts or shutdowns, that partition may be rendered unbootable -- which will cause you to lose access to Win7.

---

### Post by jonpon on 2011-01-13
I had a similar problem once, I edited the fstab. here's a[ link]("http://ubuntuforums.org/showthread.php?t=1243587")

---

### Post by presence1960 on 2011-01-13
Heed what Mark has told you. Your best bet is to create an NTFS partition (primary or logical) to keep your data for shared access between different OSs.

---

