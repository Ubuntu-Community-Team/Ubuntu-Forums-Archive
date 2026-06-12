---
title: "help!! running in safe mode, need to save some folders to usb drive"
date: 2011-04-02
forum: New to Ubuntu
---

### Post by dwhite on 2011-04-02
how can i copy a folder to a usb drive on my laptop running in safemode (all i have is a terminal to work with)

i want to write a folder with cp -f "foldername" usb

but i don't know how to refer to the usb drive

---

### Post by wolfen69 on 2011-04-02
```
sudo fdisk -l
```
will give you the drives such as /dev/sda1

Having a live cd handy is good for retrieving files also.

---

### Post by Dutch70 on 2011-04-02
I'm not sure if this will help, but can't you create a bootable usb stick and save the folder to it.

---

### Post by mikewhatever on 2011-04-02
Mount the usb first with something like
```
sudo mount /mnt /dev/sdb1
```

Then copy whatever you like:
```
cp -r /path-to-folder/folder-name /mnt/
```

---

