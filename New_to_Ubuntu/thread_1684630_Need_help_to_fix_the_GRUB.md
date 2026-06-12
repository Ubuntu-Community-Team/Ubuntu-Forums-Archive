---
title: "Need help to fix the GRUB"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by whitehooder on 2011-02-09
Hi, i have searched the forum without any success so i thought it would be smart to post a new thread.

Ok, the problem is that i've burnt Ubuntu 10.10 to a CD and tried to install Ubuntu from the CD to my 4 gb flash drive with success, but when i boot now i need to have the USB plugged in for any GRUB to load.

I think the problem is'nt that i have no GRUB at my HardDrive but that the system has set itself tu use the USB as GRUB-loader.

When i try to run the system without having the USB plugged in i get a command line that looks like this:

GRUB RESCUE>

It would be nice to get response as quickly as possible.

Whitehooder:-k

---

### Post by cariboo on 2011-02-09
Boot from a Live CD, with the usb drive plugged in, and once at the desktop use these instructions:

[LIST=1]
[*]sudo  mount /dev/sdbX /mnt
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

Where /dev/sdbX = your usb drive. Once at the prompt type:

```
grub-install /dev/sda
```

the above command installs grub to the mbr of your first hard drive. Next type:

```
update-grub
```

to update the menu, then type Ctrl-d twice, and reboot, you should see a proper grub menu now.

---

### Post by Clever_Username on 2011-02-09
> **cariboo907 said:**
> Boot from a Live CD, with the usb drive plugged in, and once at the desktop use these instructions:

[LIST=1]
[*]sudo  mount /dev/sdbX /mnt
[*]sudo mount -o bind /sys /mnt/sys
[*]sudo mount -o bind /dev /mnt/dev
[*]sudo mount -o bind /proc /mnt/proc
[*]sudo chroot /mnt
[/LIST]

Where /dev/sdbX = your usb drive. Once at the prompt type:

```
grub-install /dev/sda
```

the above command installs grub to the mbr of your first hard drive. Next type:

```
update-grub
```

to update the menu, then type Ctrl-d twice, and reboot, you should see a proper grub menu now.



Wow! Just Wow.....

---

### Post by whitehooder on 2011-02-09
Thanks for the commands above, but there is only one thing i need to know:
How do i do this if my Ubuntu system is installed on a RAID (Striped)?
The disks names is /sda and /sdb i've checked using the Disk Utility program.

Whitehooder

---

### Post by whitehooder on 2011-02-09
The problem is not that i cant boot into my ubuntu but that i need a usb to do it ;D

---

### Post by whitehooder on 2011-02-10
Here is a screenshot of my disk utility screen hope it helps

---

### Post by oldfred on 2011-02-10
RAID complicates it. I do not use RAID for a desktop, so I do not know all the details.

But if you can boot into your install, then you can just install to the boot drive with:

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sdb"  then just run, not sure if for raid it is both sda & sdb or md0 etc:
sudo grub-install /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck /dev/sdb
sudo update-grub
#to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
#To see what drive grub2 uses see this line - grub-pc/install_devices:
sudo debconf-show grub-pc

If your system is more complex it is often best to run this and save a copy. If above does not work, then post this:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

---

### Post by whitehooder on 2011-02-10
Thanks for all help.

I actually posted a "Need help to fix GRUB on RAID (striped)" 
[http://ubuntuforums.org/showthread.php?t=1685201](http://ubuntuforums.org/showthread.php?t=1685201)

If any other got the same problem the link on how to install and configure the GRUB 2 from ronparent following the link i posted ;D

Thanks for all the help i've got but i think that this site is the best for beginners :D

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

Regards Whitehooder:popcorn:

---

