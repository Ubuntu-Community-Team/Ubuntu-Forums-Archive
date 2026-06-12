---
title: "How do I edit the Grub.cfg file from outside"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by darenjoe on 2011-03-15
okay I made an ignorant mistake. I commented out the Ubuntu boot option from the Grub.cfg file. I can not boot into Ubuntu 10.10 now. How do I edit the Grub.cfg file from outside. I'm guessing the solution is boot from a Ubuntu thumb drive and get the permission some how. Am I right?

Your Help Please.

Daren

---

### Post by drs305 on 2011-03-15
Yes. Boot the LiveCD, then mount your Ubuntu partition. X is the drive (sda, sdb), Y is the partition (1,5, etc). Open the editor and make the change. If you edited /boot/grub/grub.cfg, that should be all that is necessary.

```
sudo mount /dev/sd**[COLOR="Red"]XY[/COLOR]** /mnt
gksu gedit /mnt/boot/grub/grub.cfg
```

If you don't know which drive/partition is "XY", run the following (lowercase L)
```
sudo fdisk -l
```

---

### Post by darenjoe on 2011-03-15
The file that opened upon the gedited command was blank.

---

### Post by drs305 on 2011-03-15
> **darenjoe said:**
> The file that opened upon the gedit command was blank.

That means that gedit did not find the file. The most likely problem is that your real system partition is not mounted, or the file does not exist. 

You can check to see if the correct one is mounted on /mnt with the following:
Mount what you think is the correct partition. Then use the "ls" command to see if the file exists:
```
sudo mount /dev/sdXY /mnt  # Example: sudo mount /dev/sda5 /mnt
ls /mnt/boot/grub/
```
Do the contents of your system's grub folder appear? There should be a lot of *.mod files. If you find those, check to see if grub.cfg is also in that folder:
```
ls /mnt/boot/grub/grub.cfg
```

If you aren't finding any system files, you will have to find the correct system partition. When you run "sudo fdisk -l" the Ubuntu partition should be identified as "Linux" in the last column. Normally it is either partition 5 or partition 1 (sda1, sda5, sdb1, sdb5, etc) if you have no other OS or just Windows.

---

### Post by darenjoe on 2011-03-15
The file is there. I can open it. BUT I am booting from a thumb drive, so the commands lead back to the booting drive.

---

### Post by darenjoe on 2011-03-15
> **drs305 said:**
> That means that gedit did not find the file. The most likely problem is that your real system partition is not mounted, or the file does not exist. 

You can check to see if the correct one is mounted on /mnt with the following:
Mount what you think is the correct partition. Then use the "ls" command to see if the file exists:
```
sudo mount /dev/sdXY /mnt  # Example: sudo mount /dev/sda5 /mnt
ls /mnt/boot/grub/
```Do the contents of your system's grub folder appear? There should be a lot of *.mod files. If you find those, check to see if grub.cfg is also in that folder:
```
ls /mnt/boot/grub/grub.cfg
```If you aren't finding any system files, you will have to find the correct system partition. When you run "sudo fdisk -l" the Ubuntu partition should be identified as "Linux" in the last column. Normally it is either partition 5 or partition 1 (sda1, sda5, sdb1, sdb5, etc) if you have no other OS or just Windows.

I am using your terminal commands correctly. sda7 is mounted, but I need the permissions, what would be the command for that look like??

---

### Post by drs305 on 2011-03-15
> **darenjoe said:**
> I am using your terminal commands correctly. sda7 is mounted, but I need the permissions, what would be the command for that look like??

If you use "gksu" with either "nautilus" or "gedit" you will open the applicable GUI as root and should be able to edit the files ("gksu gedit /mnt/boot/grub/grub.cfg"  or to explore with the file browser "gksu nautilus /mnt/boot/grub").

Added:
You mentioned leading you back to the flash drive. When you run the fdisk command, you should see your flash drive as well as your hard drive. The first line for each drive lists the drive size. Use that to help determine the correct drive/partition to mount. You want to mount the partition on your hard drive that contains the grub.cfg file you want to edit (not the flash drive partition).

---

### Post by darenjoe on 2011-03-15
"gksu" with "nautilus"  That did it! I got in.

Thanks for the help and your time.

Daren

---

