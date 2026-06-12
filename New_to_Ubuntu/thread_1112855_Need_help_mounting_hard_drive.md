---
title: "Need help mounting hard drive"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by BarePaw on 2009-04-01
I'm trying to mount a brand new hard drive in a system that is entirely Ubuntu 8.10 (no Windows involved). I have already successfully formatted the drive using ext3 filesystem in Gnu Partition Editor. 
When I try to change the permissions by typing 
"chmod 777 /media/drivename" it tells me "Operation Not Permitted". 
When I try to mount the drive by typing "mount /dev/sdb /media/drivename" it tells me "mount: only root can do that". 
When I type "/dev/sdb /media/drivename ext3 defaults 0 0" it tells me "Permission Denied". 
Could you please tell me what I'm doing wrong? Thanks.

---

### Post by primaxx on 2009-04-01
Add sudo before your commands. (Then you operate as root)
example:```
sudo mount /dev/sdb /media/drivename
```
:-)

---

### Post by indytim on 2009-04-01
> sudo mount /dev/sdb /media/drivename

If you have formatted only 1 partition on this drive, the mount should say:
> sudo mount /dev/**sdb1** /media/drivename.

Also, just a reminder... when you have mounted the drive successfully, you will also need to modify your /etc/fstab file to reflect a mounting at bootup.

IndyTim

---

### Post by AnimalMagic on 2009-04-01
I have a similar problem with a USB disk. I ceated a new partition using gparted, but when it automounts, it's read only.

I tried 
> sudo chown myuser /media/mountpoint but it made no difference.

I also tried 
> sudo chown myuser /dev/sdb1
with no result.

---

### Post by AnimalMagic on 2009-04-01
Correction... After unmounting and remounting, I was able to write to the disk! Doh!

---

### Post by BarePaw on 2009-04-01
Thanks guys. That all worked, except I'm still getting the "Gtk-WARNING **: cannot open display:" after typing "sudo gedit /etc/fstab"

---

### Post by mikechant on 2009-04-02
> Thanks guys. That all worked, except I'm still getting the "Gtk-WARNING **: cannot open display:" after typing "sudo gedit /etc/fstab"

Try using 'graphical sudo' instead:
```
gksudo gedit /etc/fstab
```

---

