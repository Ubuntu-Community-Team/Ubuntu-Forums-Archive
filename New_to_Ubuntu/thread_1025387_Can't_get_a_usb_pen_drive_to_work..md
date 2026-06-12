---
title: "Can't get a usb pen drive to work."
date: 2008-12-30
forum: New to Ubuntu
---

### Post by Mick8882003 on 2008-12-30
I have tried fdisk and gparted, both were able to successfully format the drive, but when I go to use it via nautilus it cannot mount the disk.

Help, I spent 60 bucks on this little thing and it came from France (I'm in Australia)

---

### Post by Ender41 on 2008-12-30
> **Mick8882003 said:**
> I have tried fdisk and gparted, both were able to successfully format the drive, but when I go to use it via nautilus it cannot mount the disk.

Help, I spent 60 bucks on this little thing and it came from France (I'm in Australia)


Sounds very expensive, how big is it ?

It's not something silly like a windows based system with a built in os like some electronic photoviewrs are is it ?

A little more detail about the pendrive might help us to help you

---

### Post by cdtech on 2008-12-30
When you plug it in check your log file for errors or abnormalities:
```
cat /var/log/messages
```
And also the output of this command is useful:
```
sudo fdisk -l
```

---

