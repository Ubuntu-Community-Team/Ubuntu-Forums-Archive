---
title: "External hard driver mount from terminal"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by bennis on 2009-01-05
I don't know how to find my hard drive. I know the mount command but i really can't find the hard drive to mount. I checked /mnt and /media. Help? :( Its a USB External if that helps.

---

### Post by rjmoerland on 2009-01-05
After attaching the drive, look in the /var/log/syslog file with a text editor and go to the end. Look for messages describing a new /dev/hdX or /dev/sdX. That's the drive you need to mount (if it's not automounted)

---

### Post by jerome1232 on 2009-01-05
Devices are actually found under /dev, to get a listing of attached hard disks try this command.

```
sudo fdisk -l
```

Also you will need to actually create a directory before you mount, so lets say your drive is /dev/sdb1 and you want to mount it to /media/sdb1 this is what you would do.

```
sudo mdkir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
# if it's a linux file system and you want your user to have r/w privliges to it, this is a one time thing.
sudo chown -R $USER: /media/sdb1
```

---

### Post by CAPLinux on 2009-01-05
Any time I plug in an external device, Thumb Drive, Smart Card, portable hard drive, etc it appears on my desktop.  Does that not happen for you?

---

### Post by rjmoerland on 2009-01-05
> **jerome1232 said:**
> Devices are actually found under /dev, to get a listing of attached hard disks try this command.

```
sudo fdisk -l
```


Cool 8)

---

### Post by bennis on 2009-01-05
Thank you all so very very much. I'm doing this via SSH and don't have a GUI installed, so i don't have a desktop.

---

