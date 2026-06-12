---
title: "Copying files"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by mistypotato on 2009-02-23
Hi,

I want to copy files using the command line only....

The source is a main partition on my hard drive and the destination is a USB thumbdrive

FROM = /dev/sda1  (hard drive)

TO = /dev/sdb1  (thumbdrive)



How would I do this?

Do I need to mount the thumbdrive ?

---

### Post by sirjoebob on 2009-02-23
For something like this, you could have ran a google search but I'm feeling generous today :)

cp /dev/sda1/FILENAME /dev/sdb1

You can google bash copy for more info.

---

### Post by SuperSonic4 on 2009-02-23
The thumbdrive will need to be mounted yes

```
sudo mkdir /media/disk
sudo mount -t vfat /dev/sdb1 /media/disk
```

then you'd do ```
cp -v path_to_file_on_hdd /media/disk
```

path_to_file_on_hdd is where the source file is, if you wanted to copy your desktop folder and it's contents:

```
cp -Rv ~/Desktop /media/disk
``` - this will create a folder called Desktop on the usb pen with the contents inside

If you wanted to copy File.txt which is in your home directory

```
cd && cp -v File.txt /media/disk
``` - cd will take you to your home directory first

where I have put -v you can have

-v = verbose (show what is going on)
-f = force (do not confirm)
-i = interactive (ask)
-R = recursive (copy and folder and it's contents)

there are others than can be found in ```
man cp
```

Bear in mind in *NIX directories and files are case sensitive

---

### Post by geirha on 2009-02-23
No, both drives must be mounted. 
```
# Create mount-points
sudo mkdir -v /mnt/sda1 /mnt/sdb1

# Mount
sudo mount -v /dev/sda1 /mnt/sda1
sudo mount -v /dev/sdb1 /mnt/sdb1

# Copy
cp -v /mnt/sda1/file1 /mnt/sda1/file2 /mnt/sdb1/   # Copies file1 and file2 from the root of sda1 to the root of sdb1

# Unmount when done copying. It is important to unmount the thumb drive, especially if it is FAT or NTFS
sudo umount -v /mnt/sda1 /mnt/sdb1

# Remove mount-points
sudo rmdir -v /mnt/sda1 /mnt/sdb1

```

If the thumb drive has FAT or NTFS filsystem, then you'll need to either give your user privileges during mount, or run the copy command (cp) with sudo (sudo cp ...)

---

