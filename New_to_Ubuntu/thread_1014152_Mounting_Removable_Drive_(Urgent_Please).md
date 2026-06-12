---
title: "Mounting Removable Drive (Urgent Please)"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Ant01 on 2008-12-17
Please can someone assist me in mounting a removable drive on my system. I spent some time learning the basics and had my system up and running. I use Ubuntu to store my files on a server but somehow removed the mounting from my removable drive (usb) when I renamed the disk. I have all my files stored on the removable drive and can't access them on Ubuntu. I am very frustrated as I have read up on mounting drives but can't get it right.....

PLEASE HELP

---

### Post by Titan8990 on 2008-12-17
First you need to find out the logical name of the drive.

Do so with the following command:

sudo fdisk -l


This will show all the drives in your system. I will assume that your drive is /dev/sdb1. To mount it:


sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1

Then you can view the contents of your drive at /media/sdb1 (it should also appear on your desktop).

---

### Post by ugm6hr on 2008-12-17
Are you on an Ubuntu-Gnome desktop, or server?

Show us /etc/fstab:
```
gedit /etc/fstab
```

---

### Post by Ant01 on 2008-12-17
Thanks for the quick response...
I am on a Ubuntu-Gnome desktop. When I the comands;
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1

I get the following message
root@antoine-ubuntu:/home/antoine# sudo mkdir /media/sdb1
root@antoine-ubuntu:/home/antoine# sudo mount /dev/sdb1 /media/sdb1
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 /media/sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0

---

### Post by Ant01 on 2008-12-17
gedit /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=012fd809-176a-4f4e-a1fd-ab0ab0b59735 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=3aee5586-4a96-428e-9213-3a829813e141 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

---

### Post by drs305 on 2008-12-17
The device you are trying to mount is formatted in ntfs. Your options are what the error message says. The best thing to do is go back to windows and do a normal shutdown.

If you can't do that, you can install a set of ntfs tools called "ntfsprogs" and then run "sudo ntfsfix /dev/[COLOR="Red"]sdb1[/COLOR]" if "sdb1" is the device name. This method is not quite as safe as clearing the error through windows, so don't try this first. To install ntfsprogs:
```
sudo apt-get update
sudo apt-get install ntfsprogs
*once installed:*
sudo ntfsfix /dev/sd[COLOR="Red"]b1[/COLOR]
```

Once you have cleaned up the error, I recommend you install and use the NTFS Configuration Tool if you want the device listed in fstab.

To install:
```
sudo apt-get update
sudo apt-get install ntfs-config
```

Next start the program (Main Menu,System Tools, NTFS Configuration Tool)

It will ask for a mountpoint. Select a name. The mountpoint will be /media/*thenameyoupicked*

Next tick the options for write capability and close the app.

NTFS Configuration Tool will automatically add the entry to fstab and the partition will automount on subsequent boots. If it doesn't mount initially, run:
```
sudo mount -a
```

---

### Post by xjcannonx on 2008-12-17
Do you have a windows machine available?

---

### Post by logos34 on 2008-12-17
reopen fstab as root so you can edit it per the error message:

gksudo gedit /etc/fstab


now paste te line at the botttom

/dev/sdb1 /media/sdb1 ntfs-3g defaults,force 0 0


Or else get and ntfs-config which will do it for you:

sudo apt-get install ntfs-config

gksudo ntfs-config

enable r+w support external hdd

edit: I see someone has already post much the same

---

### Post by Ant01 on 2008-12-17
My other machines run windows. The server machine is a dual bootup but it doesn't want to boot up in windows, I think it may be corrupt, I will try again

---

### Post by xjcannonx on 2008-12-17
Instead of editing fstab it way be easier to just hook up your drive to windows and "safely remove" it from there. I think windows writes a file to each drive that is connected to it and in order for it to be hooked up on your ubuntu machine windows needs to write to that file basically saying it is done. Sometimes when you try to safely remove you might get an error, to get around this I think you could just shut down windows while the removable drive is still connected and then try it with ubuntu.

---

### Post by Ant01 on 2008-12-17
I have been using the removable drive on my laptop with no problem. I tried booting up the server from Grub with windows but it seems that windows is corrupt as it bombs out of windows and reboots when I choose the windows option....

---

### Post by Ant01 on 2008-12-17
Thanks guys for the help, managed to fix the problem using the NTFS Configuration Tool.

---

