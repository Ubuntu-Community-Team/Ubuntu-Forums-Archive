---
title: "Removing Certain mounted drives from Desktop"
date: 2011-04-27
forum: New to Ubuntu
---

### Post by SenorHelmut on 2011-04-27
I know Ubuntu Tweak can show/remove all mounted drives from the desktop, but what I was wondering is if it is possible to just remove CERTAIN drives from the desktop.

For instance...  I use an NTFS partition to store files because i dual-boot between Win7 and Ubuntu (if only i could replace Adobe Photoshop 5). I installed NTFS Config so it always mounts at booting and shows the drive on my desktop. I want to hide the NTFS partition because everything is linked through the Home folder. But when I plug in flash drives or my phone, I want those devices to still show up on my desktop. 

At the moment, I can see all the drives or none of them.

So, any ideas?

---

### Post by Morbius1 on 2011-04-27
Change the mount point. A mount point in your home directory or /media creates a mount icon on the desktop. A mount point in /mnt or even off "/" itself does not.

So for example instead of /media/sda1 create a mount point at /mnt/sda1:
```
sudo mkdir /mnt/sda1
```Unmount the current mountpoint:
```
sudo umount /media/sda1
```Then go into /etc/fstab as root:
```
gksu gedit /etc/fstab
```And modify the line to the new mount point.

Then run the following command to test for errors and mount the new partition:
```
sudo mount -a
```If you run into problems or if my post was incoherent post the output of the following commands:
```
cat /etc/fstab
mount
```

---

