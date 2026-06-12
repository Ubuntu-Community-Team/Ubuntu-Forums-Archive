---
title: "Two physical drives two operating systems?"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by TopgunB on 2011-02-27
I am using ubuntu under Wubi. I have two physical hard drives on my laptop both aroung 200Gb.I would now like tom partition my hard drives and install Ubuntu properly in it's own partition. Is it possible to dual boot with Windows on one of the physical hard drives and Ubuntu on the other??

---

### Post by Verbeck on 2011-02-27
yes, it's possible. just choose which harddisk to install ubuntu on during the installation process
or choose 'manually partition' if you dont want ubuntu to use the entire disk

---

### Post by Ben Page on 2011-02-27
Are you sure you have two physical drives. From the sound of your post it looks like you have two partitions on one physical drive. Any OS will show a partition as a physical drive, not as a partition.
You can use gparted or Disk Utility to determine this.

To install OSes into separate drives, I would use a method of unplugging the secondary drive. Unplug the drive you don't want to use and install the OS regularly to tour primary drive, then plug them back in. For a beginner it can get quite confusing when partitioning and installing bootloaders, you could (and probably will) end up with one OS not booting. Then you can choose which OS to boot from your boot order menu of your PC (usually F11).

---

### Post by bill516 on 2011-02-27
Not a bad way to do it, Ben Page, but it does not work easily on a laptop!  (Which will have only one HD unless a second one is running through a USB port.)

In any event I don't think it matters whether each OS is on its own physical drive or on its own set of partitions on one single drive.

If we install Ubuntu and then let GRUB2 configure itself it should find the second (or third, or fourth) OS.

The only catch is to specify the boot drive when GRUB is installed.  That way when the machine boots, GRUB will do its thing and bring up the menu of installed OS's.

And away we go!

---

### Post by Ben Page on 2011-02-27
bil516, that's why I'm saying that he should check if he has two physical drives. There are laptops that pack 2 HDDs, but those are high end, usually gaming laptops. "Physical drive" is an actual computer peripheral, if you have two, than thats two parts that you can actually hold in your hands. But the OS will recognize one partitioned drive as more "physical drives", which are actually more partitions.

Thats why I'm encouraging the poster to check that out. There could also be issues if you install Ubuntu first and Windows second, Windows bootloader won't recognize any other OS except Windows, thus rendering Ubuntu unbootable.

Just a few pointers, to prevent future issues...

---

### Post by oldfred on 2011-02-27
HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

One of the few installs for a second hard drive with lots of detail:
Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

