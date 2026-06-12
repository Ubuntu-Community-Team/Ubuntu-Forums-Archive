---
title: "external harddrive problems"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by abraxas334 on 2011-02-15
I bought a backup 2T harddrive. On a different computer (running OSX) to my current one (Ubuntu) I added a lot files for back up. Now I want to change some of them but I don't have the right permission to change them. Nor using sudo am I allowed to change the permission/remove directories.
As all my original files are still ok I can just wipe the backup drive and put the files back on it. My question is: How do I format the harddrive. 
It is a sata drive with a USB docking station. Ubuntu atumatically mounts it to media.

Any help would be great thanks
Thanks

---

### Post by mikewhatever on 2011-02-15
System->Administration->Disk Utility

---

### Post by Sidewinder1 on 2011-02-15
I have multiple external hard drives; some esata and some usb. I have solved your problems many times, on my system, in the following manner: copy and paste this command into your terminal:
```
sudo chown -R abraxas334:abraxas334 /media/disk
```
The above is assuming that your ubuntu log-in username is abraxas334 and that the mount point of your external hard-drive is media/disk. You can check the mount point by, after it auto-mounts, right click on the drive on your desk-top, left click on properties, then left click on volume.

HTH,
Side

---

### Post by abraxas334 on 2011-02-15
> **Sidewinder1 said:**
> 
into your terminal:
```
sudo chown -R abraxas334:abraxas334 /media/disk
```

HTH,
Side

Thanks so much that worked brilliantly!

---

### Post by Sidewinder1 on 2011-02-15
My pleasure! Glad to've helped 'cause I've been helped so many times by the kind and knowledgeable folks on this board, it's really nice to return the favor :p.
Side

---

