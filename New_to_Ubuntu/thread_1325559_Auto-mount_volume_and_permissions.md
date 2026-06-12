---
title: "Auto-mount volume and permissions"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by rcbinwi on 2009-11-13
I dual boot with XP and Jaunty.  I tried to get the XP partition to mount at boot.  I used pysdm, but whenever I changed the checkmarks and clicked "apply," the checkmarks would always go back to how they were before.  So I can't get the volume to mount automatically.

Now things are worse.  When I go to mount and unmount this volume, I'm getting an error message:
```
Cannot unmount volume
You are not privileged to unmount this volume.
umount: only root can unmount /dev/sda2 from /media/sda2
```

I used to be able to mount and unmount this volume without having to do anything.  So my questions concern getting back my old permissions and getting the volume to mount at boot up.

One other point is that my Firefox profile is located in that partition.  Firefox can't access that partition, even when the volume is mounted.

Thanks!

---

### Post by LunaticHiatus on 2009-11-13
it sounds like you need to sudo. Your error is implying your not running it as administrator.

---

### Post by rcbinwi on 2009-11-13
This is true.  If I want to unmount I can do so in sudo nautilus.  However, I can't seem to be able to remount it from the same.  When I open /media/sda2, it's blank.

---

### Post by rcbinwi on 2009-11-13
Ok, I think I solved one problem, but still have another problem.

Firefox was not able to access my partition, whereas it was able before I ran pysdm.  The reason--I think--is because it changed the name from /media/disk to /media/sda2.  Once I changed the directory in my Firefox profile, it worked just fine.

However, I'm still having trouble mounting and unmounting the drive.  The easiest way now is via pysdm, but I would like to be able to unmount it by right-clicking, without being in the root.

Any ideas?

---

### Post by rcbinwi on 2009-11-13
I ran pysdm again, and this time I could change it.  Now I can unmount it without being the root.  Mounting it is different, but I can live with that for now.

---

### Post by durand on 2009-11-13
Are you running pysdm as root? ie, ```
sudo psydm
```

---

### Post by rcbinwi on 2009-11-14
I thought I was using sudo, but my only guess now is that I wasn't.  Thanks!

---

