---
title: "Ubuntu Has No Disk Space"
date: 2009-05-01
forum: New to Ubuntu
---

### Post by Nuadha on 2009-05-01
Today, being rather unaware of exactly what linux was, i was persuaded by a friend to install it on my SAMSUNG NC10, he recommended that i use Ubuntu. After finding UNR i thought, "wow that is handy," so i hastily downloaded and installed it. It started up great, and everything (except the reported error of sound recorder not working) worked well. Then an update message popped up and i clicked update. It said i didn't have any room, after double checking that i had a clean 80GB partition i tried again, and still it didn't work. After rooting around the internet and the help files i found that the drive needed to have the ext3 file system for Ubuntu to be able to write to it. I looked in the help documents some more and found that i needed to use "Gnome partition editor" to do this, however it isn't in my version of Ubuntu (downloaded from this Ubuntu.com website) and so i can't make any partitions the right file system, and therefore cannot update or add new programs (or files) i don't know what to do to remedy the situation. Any help would be much appreciated.
EDIT: won't be here the next few days so sorry if i seem to be ignoring advice

---

### Post by Paqman on 2009-05-01
How big is your root partition and how full is it? Go to System > Admin > System Monitor and check the file systems tab.

A spare partition won't be much use for updates, as all those go into your root partition.

---

### Post by Nuadha on 2009-05-01
2.2GB is the size of my root partition.
And the update is about 80MB

---

### Post by Paqman on 2009-05-01
> **Nuadha said:**
> 2.2GB is the size of my root partition.
And the update is about 80MB

That's extraordinarily tiny, no wonder you've run out of space.

Best thing to do would be install Gparted (it's in the repos). Shrink one of the adjacent partitions and give the space to your root. Expanding it out to at least about 6GB would be good.

Taking a backup is always good practice before messing with partitions, btw.

---

### Post by blueridgedog on 2009-05-01
Or, alternatively, reinstall and use the partition creation step to allocate about 10 gig to your root.

---

### Post by Hobgoblin on 2009-05-01
Sounds like you have installed it alongside the original operating system and for whatever reason the installer used a very small partition for Ubuntu.

---

### Post by Paqman on 2009-05-01
> **blueridgedog said:**
> Or, alternatively, reinstall and use the partition creation step to allocate about 10 gig to your root.

Might be quicker. Resizing partitions once they have data in them can be sllooooooooowwwwww.

---

### Post by fugaki on 2009-05-01
> **Paqman said:**
> Might be quicker. Resizing partitions once they have data in them can be sllooooooooowwwwww.

Plus if you're new to it, I think you will have better luck using the partition manager that comes with the install.

---

### Post by llamabr on 2009-05-01
Are you dual booting?  Open terminal, and post the output of

```
df -h
```

It looks like you just gave your root partition too small, and should reinstall.

---

### Post by Nuadha on 2009-05-01
Ok, thank you all for your help. I'll try reinstalling it first, as it sounds easier.

Edit(to save double posting):
Reinstalling and then manually configuring the partition size seemed to the job, thanks for your help

---

