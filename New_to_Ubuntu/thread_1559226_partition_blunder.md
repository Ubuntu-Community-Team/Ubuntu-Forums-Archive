---
title: "partition blunder"
date: 2010-08-23
forum: New to Ubuntu
---

### Post by Sleven7 on 2010-08-23
Ok, here is a brief run down of the last 8 hours or so...

Tried to install Gnome3 only to have the system crash, my fault, I used the bash terminal instead of the run application line.  Recovered old Gnome by rebooting.

On reboot, the keyboard on the laptop was messed up, was getting number instead of letters, reconfigured everything including the desktop.  Reference thread [http://ubuntuforums.org/showthread.php?t=1559107](http://ubuntuforums.org/showthread.php?t=1559107)

I decide I'm just going to reinstall Ubuntu 10.04 from the CD

It repartitions the HD again and now I have a 50G partition with nothing on it.  I stopped the reinstall before it put two copies of Ubuntu 10.04 on the HD.

I reboot with the original Ubuntu and the keyboard issue has corrected itself, keyboard is working fine (go figure) but Windows 7 will not boot.

Is there any way to correct the repartition?

---

### Post by redbook4574 on 2010-08-23
> **Sleven7 said:**
> Ok, here is a brief run down of the last 8 hours or so...

Tried to install Gnome3 only to have the system crash, my fault, I used the bash terminal instead of the run application line.  Recovered old Gnome by rebooting.

On reboot, the keyboard on the laptop was messed up, was getting number instead of letters, reconfigured everything including the desktop.  Reference thread [http://ubuntuforums.org/showthread.php?t=1559107](http://ubuntuforums.org/showthread.php?t=1559107)

I decide I'm just going to reinstall Ubuntu 10.04 from the CD

It repartitions the HD again and now I have a 50G partition with nothing on it.  I stopped the reinstall before it put two copies of Ubuntu 10.04 on the HD.

I reboot with the original Ubuntu and the keyboard issue has corrected itself, keyboard is working fine (go figure) but Windows 7 will not boot.

Is there any way to correct the repartition?

You could try using testdisk.

---

### Post by jtarin on 2010-08-23
In Ubuntu...in the terminal run the command ```
fdisk -l
``` and post.

---

### Post by Sleven7 on 2010-08-24
When I enter "fdisk -l" in the terminal, nothing happens, it immediately returns to the prompt without displaying anything.

---

### Post by jtarin on 2010-08-24
Then enter fdisk -v to see if it's installed, which by all that is practical it should be. Try sudo fdisk -l
Whenever you try a _**legal**_ command in the terminal and you get no results...try pre-pending sudo to the command.

---

### Post by Sleven7 on 2010-08-24
Had to use sudo for "fdisk -l" to work.  It returned:

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9a0c9a0c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1536000   27  Unknown
/dev/sda2             192        9409    74036331+   7  HPFS/NTFS
/dev/sda3           29346       30402     8479744   17  Hidden HPFS/NTFS
/dev/sda4           16055       29346   106762241    5  Extended
/dev/sda5           16055       28800   102376448   83  Linux
/dev/sda6           28800       29346     4384768   82  Linux swap / Solaris

---

### Post by LiquidMeson on 2010-08-24
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

download ms-sys from here, [http://ms-sys.sourceforge.net/](http://ms-sys.sourceforge.net/) instead of sudo ag install ms-sys (banned for legal issues)

extract it,
terminal > cd ms-sys*
make
sudo make install

continue from website.

wish the site had debs

---

### Post by jtarin on 2010-08-24
Is Windows on your /dev/sda1 * 1 192 1536000 27 Unknown?
Looks like you borked your boot record for Win. Do you have the Win 7 repair disc? It can correct that but then you will have to reinstall Grub.

---

