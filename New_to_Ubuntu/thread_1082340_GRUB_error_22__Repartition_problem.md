---
title: "GRUB error 22 / Repartition problem"
date: 2009-02-27
forum: New to Ubuntu
---

### Post by WiseMaturin on 2009-02-27
So my Grub doesn't load so I can boot up any of my installed OSes.
Citing some Error 22.
I am currently running an Ubuntu Live CD so I can do homework and figure out wtf is going on and how to get everything back in order.

So does anyone know what gives?

---

### Post by caljohnsmith on 2009-02-27
In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by stalkier on 2009-02-27
I have had Error 22 a couple times before. It is easily fixed using Super Grub Disc.

---

### Post by WiseMaturin on 2009-02-28
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about downloading the **Boot Info Script** to your Ubuntu Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

> **stalkier said:**
> I have had Error 22 a couple times before. It is easily fixed using Super Grub Disc.


The RESULTS.txt file...
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => No boot loader is installed in the MBR of /dev/sdb

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  -
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf8000000

Partition  Boot         Start           End          Size  Id System



Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2500 MB, 2500485120 bytes
255 heads, 63 sectors/track, 304 cylinders, total 4883760 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63     4,883,759     4,883,697   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="No Name" UUID="0000-FFFF" TYPE="vfat" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/No Name type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


=========================== sdb1/boot/grub/menu.lst: ===========================

# You can edit this file to add your own distribution
# You can choose default to 0 to select first entry
# which it is usually the entry for the default distro
#
#
# You can also set timeout to something as 10
#
# This is the shortcut to call Super Grub Disk (commented)
#title Super Grub Disk
## The two commands: setgrubdevice and usbshift are needed
## so that SGD works well.
#usbshift
#configfile $(grub_device)/boot/sgd/menu.lst
#
# Just after default and timeout statements you have to put
# setgrubdevice so that grub device is correctly set.




default 0
timeout 2
setgrubdevice # This is compulsory
#sgdgfxmenu /boot/grub/message
foreground ffffff
background 0c00ff
color white/brown yellow/cyan


#title Inicio normal / Normal Boot 
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs

#title Soporte de accesibilidad / Accesibility Support -->
#configfile $(grub_device)/boot/grub/menu2.lst

title Super Grub Disk
# The two commands: setgrubdevice and usbshift are needed
# so that SGD works well.
usbshift
configfile $(grub_device)/boot/sgd/sgd.lst

#title Normal boot. Kernel is aware of Boot device
#kernel $(grub_device)/vmlinuz lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash boot_device=$(grub_device)
#initrd $(grub_device)/initramfs

#title Normal boot. Selecting kernel and initrd files depending on grub_device
#kernel $(grub_device)/vmlinuz_$(grub_device_string) lang=es a11y=none root=/dev/ram0 ramdisk_size=100000 initrd=initramfs quiet BOOT=live splash
#initrd $(grub_device)/initramfs_$(grub_device_string)

#title Selecthd test
#configfile $(grub_device)/boot/grub/choose/selecthd.lst

#title findp test
#configfile $(grub_device)/boot/grub/choose/selectpart.lst
#title set SGD variables and boot SGD
#
#configfile $(grub_device)/boot/sgd/menu.lst

=================== sdb1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
```

I have the Super Grub Disc downloaded to my flash drive.

---

### Post by caljohnsmith on 2009-02-28
According to the script results, your sda drive does not have a valid partition table any more. Do you know what would have caused that to happen? Can you think of anything you did before getting the Grub error 22 that might have erased your sda partition table? If you want to try and recover your partitions on the sda drive, "testdisk" is probably one of the best programs for doing it, but if Ubuntu was freshly installed to the sda drive, I would recommend just reinstalling. Let me know if you want to use testdisk to recover your partitions, because I can give you specific instructions for how to use it most effectively and accurately, at least based on my experience with it.

---

### Post by WiseMaturin on 2009-02-28
> **caljohnsmith said:**
> According to the script results, your sda drive does not have a valid partition table any more. Do you know what would have caused that to happen? Can you think of anything you did before getting the Grub error 22 that might have erased your sda partition table? If you want to try and recover your partitions on the sda drive, "testdisk" is probably one of the best programs for doing it, but if Ubuntu was freshly installed to the sda drive, I would recommend just reinstalling. Let me know if you want to use testdisk to recover your partitions, because I can give you specific instructions for how to use it most effectively and accurately, at least based on my experience with it.

I was trying to use the Ubuntu Live CD to repartition my harddrive because I'd had a problem previously with dual-booting Vista and Kubuntu, so I was trying to reinstall Vista. I was also thinking of making a separate partition for /home, but I was just going to take it one step at a time.

When I started the partition editor though, it said my whole 160GB drive was unallocated, so I quit and tried to restart to see if something was wrong, and then it came up with the Error 22.

---

