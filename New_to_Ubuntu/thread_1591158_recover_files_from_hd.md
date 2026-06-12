---
title: "recover files from h/d"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by whispers1944 on 2010-10-08
I had a dual boot sys XP + U9.04 with seperate admin section , moved the drive into a different computer [ same model ] and installed WIN7 on the XP partition . now the question is can i recover the files from the u9.04 admin section , have tried several ways but nothing works = the ubuntu section is alive and win7 can see it but non of my rescue disc's can recover files - acronis - gparted - grub - super grub - U7.04 - U 10.04 LIVE DISC  etc .

THANKS FOR ANY REPLYS

 				 				**Thank you all** 			
 			 			 		   		 		 		A big thanks to -  suaswe  -  louieb  -  jtarin

thanks is not enough but it is all i have, i am very grateful for ur time and effort. Respect to you all

---

### Post by SuaSwe on 2010-10-08
Is it the root partition you're trying to recover files from? What happens when you try to access it using a LiveCD?

---

### Post by whispers1944 on 2010-10-09
> **SuaSwe said:**
> Is it the root partition you're trying to recover files from? What happens when you try to access it using a LiveCD?

THANKS FOR UR REPLY

SDA1 = WINDOWS 7
SDA5 = UBUNTU 10.04
SDA6 = SWAP 

i am not sure how to log on from live cd ?? do i have to mnt or what ?? KEN

---

### Post by whispers1944 on 2010-10-09
me a bit dumb but getting a bit better.

used 9.04 live cd to boot the compt and went to comp and can see the folder and files i need to recover but HOW DO I CHANGE THE FOLDER PERMISSIONS = i know the password and u/n for the admin THAT I SAVED THE FILES UNDER but don't know how to change it.

THANKS AGAIN FOR ANY HELP

---

### Post by louieb on 2010-10-09
If you can see the file you should be able to copy it somewhere else without changing permissions. What happened when you tried? 

But if you have to change permissions or ownership. 
Bring up the run dialog (Alt + F2) and enter
```
gksudo nautilus
```

Right click on the file or folder and open Properties.  And change there.

---

### Post by jtarin on 2010-10-09
Boot to the LiveCD Desktop. 
Please note that the Live CD must be the same as the system you are fixing - either 32-bit or 64-bit (if not then the chroot will fail).
Open a terminal - Applications, Accessories, Terminal.
Determine your normal system partition - (the switch is a lowercase "L")
```
sudo fdisk -l
```
If you aren't sure, run
```
df -Th
```. Look for the correct disk size and ext3 or ext4 format.
Mount your normal system partition:
Substitute the correct partition: sda1, sdb5, etc.
```
sudo mount /dev/sdXX /mnt # Example: sudo mount /dev/sda1 /mnt
```
Only if you have a separate boot partition:
sdYY is the /boot partition designation (for example sdb3)
```
sudo mount /dev/sdYY /mnt/boot
```
Mount the critical virtual filesystems:
```
sudo mount --bind /dev  /mnt/dev
sudo mount --bind /dev/pts  /mnt/dev/pts
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys  /mnt/sys
```
Chroot into your normal system device:
```
sudo chroot /mnt
```

Now you are in your Ubuntu install.

---

### Post by whispers1944 on 2010-10-09
A big thanks to -  suaswe  -  louieb  -  jtarin

thanks is not enough but it is all i have, i am very grateful for ur time and effort. Respect to you all

---

### Post by jtarin on 2010-10-09
Anytime! Your more than welcome. Glad your running again.

---

