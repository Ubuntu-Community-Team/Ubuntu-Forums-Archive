---
title: "Newbie help for smartlink pci modem"
date: 2005-11-19
forum: Networking &amp; Wireless
---

### Post by anilubuntu on 2005-11-19
Hi all

I have just downloaded Ubuntu 5.10 breezy.  I love the looks, the theme and the new gnome.  Awesome!  However, I desperately need help configuring my smartlink pci modem.  i found a driver.deb but it didn't install.  without internet access, my ubuntu is totally crippled...HELP HELP!!!

I am currently triple booting ubuntu, Suse linux 9.1 personal (which automatically found out and installed the modem driver), and windows xp (which i am trying to get away from, and have succeeded to some extent)!

Please, please (literally begging....), some simple intructions/download for a newbie like me!


Thanx in advance!

---

### Post by the_pc_dude on 2005-11-28
Download your Drivers and you can do two things Use windoze to dwnl the drivers or use suse to dwnl them.
 If you use windows use Ltools in windows to write the drivers to the ubuntu partition . You can also dwnl load an version of ltools for linux

Or you can do these commands with terminal in ubuntu/Suse to mount the partition/HDD and write to it.

For Fat32 

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t vfat -o iocharset=utf8,umask=000

For NTFS

sudo mkdir /media/windows
sudo mount /dev/hda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222

---

