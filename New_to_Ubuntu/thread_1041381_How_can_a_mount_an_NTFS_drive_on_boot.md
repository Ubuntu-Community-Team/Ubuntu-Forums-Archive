---
title: "How can a mount an NTFS drive on boot?"
date: 2009-01-16
forum: New to Ubuntu
---

### Post by hamofgrey on 2009-01-16
I am having trouble getting my Windows partition to mount on boot.
What I want to do is to mount the drive on boot and to make it available to every user.

I was going to try and mount the drive within a script and run the script on boot, I am reading a book on how to do this but I am stuck or is there an easier method?

Atm I can't even get the drive to mount using the mount command. I am definitely doing it wrong.

Any help would be appreciated.

---

### Post by drjonze on 2009-01-16
I auto mount my ntfs drives by using the NTFS configuration tool. If you go to add/remove programs and search NTFS you'll find it.

---

### Post by hamofgrey on 2009-01-16
I was hoping somebody would be able to show how to use a script or edit the fstab file in etc.

---

### Post by taurus on 2009-01-16
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by hamofgrey on 2009-01-16
I know how to install ntfs tools. I was hoping for more help on the last post subject matter.

---

### Post by taurus on 2009-01-16
[http://www.psychocats.net/ubuntu/mountwindowsfstab#fstab](http://www.psychocats.net/ubuntu/mountwindowsfstab#fstab)

---

