---
title: "mount and unmount commands"
date: 2011-04-12
forum: New to Ubuntu
---

### Post by slixz85 on 2011-04-12
hi im using a live installer iso and have downloaded another iso for installation but the device is saying volume locked when trying to mount it and it doesnt not automount. just needing to know the simple mount and unmount procedure or force mount or something. i am needing to mount it to mountpoint unetbootin says. any info helpful

thanks

---

### Post by slixz85 on 2011-04-12
> **slixz85 said:**
> hi im using a live installer iso and have downloaded another iso for installation but the device is saying volume locked when trying to mount it and it doesnt not automount. just needing to know the simple mount and unmount procedure or force mount or something. i am needing to mount it to mountpoint unetbootin says. any info helpful

thanks


also since obvious live install i cant restart the machine cuz i would ahve to download iso again for 2hours

thanks

---

### Post by wolfen69 on 2011-04-12
```
sudo mkdir /media/name_of_file
```
then
```
sudo mount /media/name_of_file.iso /media/name_of_file -o loop
```

---

### Post by seawolf167 on 2011-04-12
The general mounting procedure was posted above, unmounting is very similar

```
sudo umount /path/to/mount/point
```You can read more on both commands in the man pages

```
man mount
man umount
```

---

### Post by slixz85 on 2011-04-12
> **wolfen69 said:**
> ```
sudo mkdir /media/name_of_file
```
then
```
sudo mount /media/name_of_file.iso /media/name_of_file -o loop
```


a bit lost. to make sure on right page... there is no hard drive in my laptop it has been taken out and using a flash drive live installer right now just to get on the net. this laptop has only 1 other usb drive (2 total) because of the live system i cant unplug. sometimes from unpluggin and repluggin in the flash drives the device path switches from /dev/sdc1 to /dev/sdd1 dont know why. and the volume is locked so it wont let me do anything with it. i dont really want to restart the machine because i would lose it and also this has happened to me before(volume lock deal only)

mounting does this
mount: can't find /dev/sdd1 in /etc/fstab or /etc/mtab


using sudo mount /dev/sdd1 also tried sdc1

---

