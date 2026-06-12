---
title: "Second hard drive issue"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by GreggyZed on 2009-05-11
I apologize... I had the permissions set incorrectly.

---

### Post by cariboo on 2009-05-11
Do you automount the drive using fstab? You could also install ntfsprogs to automatically mount the drive. Ntfsprogs is in the repositories and you can use synaptic packae manager to install it.

Add the drive to fstab using a command similar to this.

```
# Second internal hard drive /dev/sda1
UUID=7451e251-cb09-4cda-b433-a2768d81affe /home/internal	ntfs-g3	relatime0	2
```

to edit /etc/fstab, press Alt-F2 and type:

```
gksu gedit /etc/fstab
```

---

