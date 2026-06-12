---
title: "Can't find Places on 10.10 new install! Can't mount"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by rpete on 2011-01-12
Hi, I am getting used to 10.10 which I just installed on my netbook and unlike 10.04 there are no dropdown menus at the top with Applications, Places, and System.  Instead there are icons on the left side including Applications which has Systems in it but no Places.  This became important because I plugged an external hard drive into a USB port and wanted to go to places to see if it was recognized and couldn't find it. It also did not automount on the desktop.    

I did run the command sudo fdisk -l and the external hard drive was listed as dev/sdb correctly 

What command should I run to mount it?

---

### Post by bwhite82 on 2011-01-12
You'll have to make a directory where you want it mounted, usually media folder:

sudo mkdir /media/usb

then:

sudo mount /dev/sdb /media/usb

FWIW, this is the same reason I hated the netbook version, you can install ubuntu-desktop package if you want vanilla ubuntu. Another tip while in nbr is ALT+F2 to bring up dialog to type in whichever application you wish to run.

---

### Post by rpete on 2011-01-13
Hi, sudo fdisk -l lists the external drive, and mkdir /media/usb created a directory, and using the command cat etc/fstab shows it as well, but I still don't know where the drive is.  In 10.04 there is a Places menu which lists all places.  When I automount the drive in my other computer with 10,04 I see its icon on the desktop and it is listed under Places but how do I find it in 10.10 netbook remix?  For example, when I want to send an e-mail with an attached file from the external drive, the drive doesn't show up when I hit Browse,  even though all of the above indicates it is there.

---

### Post by SuaSwe on 2011-01-13
Try typing Alt+F2 then type Nautilus. Does that give you the browser?

---

### Post by rpete on 2011-01-13
Here is the output for two commands. I can't tell if there is anything wrong with etc and needs to be commented out.  Also it seems the device was mounted.  Where is it?  I want to access files in it. 

richard@richard-AO532h:~$ sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=a4a5f639-e587-4300-8afb-4ea4e9ffc30a none            swap    sw              0       0
richard@richard-AO532h:~$ sudo mount /dev/sdb1 /media/usb
richard@richard-AO532h:~$ sudo mount -t auto /dev/sdb1 ./usb
[sudo] password for richard: 
Mount is denied because the NTFS volume is already exclusively opened.
The volume may be already mounted, or another software may use it which
could be identified for example by the help of the 'fuser' command.

---

### Post by smurphy_it on 2011-01-13
Looks like sdb is already mounted at the root (/).

You could setup an entry in the fstab to always mount to a specific directory.  You can run sudo blkid to get the UUID of the drive (Digital signature basically).

Then sudo nano /etc/fstab and create an entry for it.  Ensure you use the option "user" so that anyone can access it.

What I would do is this... Create a directory/folder on your desktop.  Then mount in there (and create an entry in fstab).  Next time you plug in the usb drive, it should automatically mount and be mounted to the directory on your desktop.

PS.  Doing a "dmesg" in a terminal window will show the last devices detected.  Alternatively, you can do a 'tail /var/log/syslog' to see the last few lines of the syslog.

---

### Post by rpete on 2011-01-13
Hi, SuaSwe I pressed Alt f2 simultaneously and nothing happens.  

I stumbled on the location of the external hard drive when I opened office.  There it was listed under places on the left side and more importantly I was able to attach a file from folders in the drive to an e-mail.  That was the main purpose for asking for help.  I will try out suggestions for automounting by putting a directory on the desktop, although the drive is in media/usb.  It would be nice to have it open on the desktop whenever I start up.  

Thanks for your help.

---

### Post by rpete on 2011-01-14
smurphy_it  I need you to walk me through the steps to creating a directory and folder on my desktop.  Now when I click open in Office the NTFS drive is not listed under places so I am unable to access the drive. I also have a FAT usb stick that automounts.  Its icon can be seen with the other icons along the left side of the screen. I'm using 10.10 netbook remix.  

I ran sudo blkid and got the UUID but when I ran sudo nano etc/fstab I got a screen I didn't know what to do with.  There were phrases at the bottom like New File and Read File and Where Is  

How do I create a directory/folder on my desktop and then mount in there?  Sudo mkdir /media/desktop?  Sudo mount /dev/sdb1 media/destop?

How do I create an entry in fstab?

---

### Post by Paqman on 2011-01-14
> **rpete said:**
> Hi, I am getting used to 10.10 which I just installed on my netbook and unlike 10.04 there are no dropdown menus at the top with Applications, Places, and System.


That's because 10.10 introduced the new Unity interface for the Netbook Edition. However, the traditional Gnome interface (with Applications, Places, etc) is still available if you want. Just log out and select Gnome from the session menu at the bottom of the log in screen.

Also, Alt-F2 won't work in Unity, since you need Gnome panels for that to work. Your USB stick should still automount under Unity, it'll show up as an icon on the dock on the left hand side of the screen. Alternatively, click on the trash can to open Nautilus and browse to it from there.

---

### Post by rpete on 2011-01-14
Now I realize there is one workaround.  Other USB devices automount and their icons can be seen on the desktop at any time, but the NTFS external drive can only be accessed if it is plugged into the USB when the computer boots and then I have to go to OpenOffice, and click file and open and the drive is listed under places to get the file you want to open.

---

### Post by Paqman on 2011-01-14
> **rpete said:**
> I have to go to OpenOffice, and click file and open and the drive is listed under places to get the file you want to open.

To save hassle, once you've got a Nautilus window open like this, right click on the icon in the dock and pin it there permanently. That way you can open a Nautilus window with one click instead of going all round the houses like this. 

It should come with an icon for Nautilus by default IMO. I believe they've fixed this ridiculous problem for the next version of Unity.

---

### Post by smurphy_it on 2011-01-17
Create:

sudo mkdir /media/usb  ## Create this directory if it doesn't exist
sudo mount /dev/sdb1 /media/usb   ### Mount USB drive to that directory
sudo ln -s /media/usb ~/Desktop/usb-drive  ## Create symbolic link on desktop pointing to the mounted USB drive.

sudo nano /etc/fstab  ## Open up nano text editor to edit file /etc/fstab

Navigate with arrow keys, and make a new entry for the USB drive:


UUID=UUID#YOU_CAPTUREED /media/usb           vfat    defaults        0       0

---

