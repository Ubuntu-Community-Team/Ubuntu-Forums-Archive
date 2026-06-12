---
title: "GRUB Menu Not Responding"
date: 2009-12-03
forum: New to Ubuntu
---

### Post by Sallée on 2009-12-03
Ubuntu Karmic 9.10 on older laptop, HP ze4420us.  Cannot recall any changes/updates made before last power down. 

When I power up, everything stops at the GRUB menu.  The arrow, "E", "C", and "Enter" keys are unresponsive.  

I have tried:
-boot with external wired keyboard (with PS/2 plug),
-boot with external wireless keyboard (with USB plug, but non-standards compliant), and
-boot with Super Grub Disk.
All had the same result: no  response.

Additionally, using LiveCD, I have also tried:
-reinstalling GRUB2 according to [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) and 
-editing TIMEOUT to "1" in /etc/default/grub.
Again the result was no response.

---

### Post by kansasnoob on 2009-12-03
I have encountered some corner issues where grub2 just wouldn't work, which is why I wrote this:

[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

I am curious if you've run any previous Ubuntu on this lappy????????

---

### Post by Sallée on 2009-12-03
kansasnoob,
Looks like a very useful tutorial.  Unless there is a way around it that I do not know about yet, I cannot use anything automated (like apt-get) because I cannot boot my hard drive.  Is there a way I can do this from LiveCD?

This was my second Ubuntu distro on this laptop.  I had Jaunty running for about 5 months prior.

---

### Post by Sallée on 2009-12-03
Went ahead and tried it.  Worked up until Step 3.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009827a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4702    37768783+  83  Linux
/dev/sda2            4703        4864     1301265    5  Extended
/dev/sda5            4703        4864     1301233+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ sudo grub-install /dev/sda
Could not find device for /boot: Not found or not a block device.
```

---

### Post by kansasnoob on 2009-12-04
Note: If any of the following steps fail just abort and run the Boot Info Script as mentioned at the end.

If you're attempting that from the Live CD you must boot to the Live Desktop and then mount and chroot your installed Ubuntu which is on sda1 so you'd:

```
sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
```

```
dpkg-divert --local --rename --add /sbin/initctl && ln -s /bin/true /sbin/initctl
```

Now, since I'm not sure if you already managed to create /boot/grub_backup or not run:

```
ls /boot
```

Output should look similar to this:

```
abi-2.6.31-14-generic         System.map-2.6.31-14-generic
abi-2.6.31-15-generic         System.map-2.6.31-15-generic
config-2.6.31-14-generic      vmcoreinfo-2.6.31-14-generic
config-2.6.31-15-generic      vmcoreinfo-2.6.31-15-generic
grub                          vmlinuz-2.6.31-14-generic
initrd.img-2.6.31-15-generic  vmlinuz-2.6.31-15-generic
memtest86+.bin
```


If you already have a grub_backup in there change the next command to something like "mv /boot/grub /boot/grub_backup**2**", otherwise:

```
mv /boot/grub /boot/grub_backup
```

```
mkdir /boot/grub
```

```
apt-get --purge remove grub-pc grub-common os-prober
```

```
apt-get install grub
```

```
update-grub
```

```
grub-install /dev/sda
```

```
grub
```

```
root (hd0,0)
```

```
setup (hd0)
```

```
quit
```

```
rm /sbin/initctl  && dpkg-divert --local --remove /sbin/initctl
```

```
exit
```

```
sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

Then reboot, remove CD and if all succeeded you should be able to boot Ubuntu, if not I'll need to see the results of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

---

### Post by Sallée on 2009-12-04
After running the following processes
```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt
root@ubuntu:/# dpkg-divert --local --rename --add /sbin/initctl && ln -s /bin/true /sbin/initctl
Adding `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# mv /boot/grub /boot/grub_backup
root@ubuntu:/# mkdir /boot/grub
root@ubuntu:/# apt-get --purge remove grub-pc grub-common os-prober
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  grub-common* grub-pc* os-prober*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 4,354kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 146178 files and directories currently installed.)
Removing grub-pc ...
Purging configuration files for grub-pc ...
Removing grub-common ...
Purging configuration files for grub-common ...
Removing os-prober ...
dpkg: warning: while removing os-prober, directory '/var/lib/os-prober' not empty so not removed.
Processing triggers for man-db ...
Processing triggers for sreadahead ...
sreadahead will be reprofiled on next reboot
Processing triggers for install-info ...
root@ubuntu:/# apt-get install grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  grub-common os-prober
Suggested packages:
  grub-doc mdadm multiboot-doc grub-emu
The following NEW packages will be installed:
  grub grub-common os-prober
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 429kB/1,423kB of archives.
After this operation, 3,547kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com karmic/main grub 0.97-29ubuntu59 [407kB]
Get:2 http://us.archive.ubuntu.com karmic/main os-prober 1.35 [22.1kB]
Fetched 429kB in 28s (15.0kB/s)  
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 145923 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu4_i386.deb) ...
Selecting previously deselected package grub.
Unpacking grub (from .../grub_0.97-29ubuntu59_i386.deb) ...
Selecting previously deselected package os-prober.
Unpacking os-prober (from .../os-prober_1.35_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for sreadahead ...
Setting up grub-common (1.97~beta4-1ubuntu4) ...

Setting up grub (0.97-29ubuntu59) ...

Setting up os-prober (1.35) ...
root@ubuntu:/# update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

root@ubuntu:/# grub-install /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
Searching for GRUB installation directory ... found: /boot/grub
Installing GRUB to /dev/sda as (hd0)...
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)    /dev/fd0
(hd0)    /dev/sda
root@ubuntu:/# grub
Probing devices to guess BIOS drives. This may take a long time.
root@ubuntu:/# rm /sbin/initctl  && dpkg-divert --local --remove /sbin/initctl
Removing `local diversion of /sbin/initctl to /sbin/initctl.distrib'
root@ubuntu:/# exit
exit
ubuntu@ubuntu:~$ sudo umount /mnt/dev/pts && sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
ubuntu@ubuntu:~$
```I rebooted and received this error.  I tried a couple of times.  Each time pressed ctrl-d after five or so minutes.  After several minutes more, nothing had changed.
```
General error mounting filesystems.8f1-4f48-bfa7-1447e4cf25ae
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@TVJohnMcIver:~# [   15.780041] AC' 97 1 access is not valid [0xfffffffffff], removing mixer.
[   15.78097] ali mixer 1 creating error
exit
exec: 10: start: not found
init: mountall-shell post-stop process (696) terminated with status 2
```The results of the batch shell are as follows.
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders, total 78140160 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0009827a

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    75,537,629    75,537,567  83 Linux
/dev/sda2          75,537,630    78,140,159     2,602,530   5 Extended
/dev/sda5          75,537,693    78,140,159     2,602,467  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 8086 MB, 8086618112 bytes
249 heads, 62 sectors/track, 1023 cylinders, total 15794176 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0007b7fd

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  62    15,793,073    15,793,012  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="50fe7508-c8f1-4f48-bfa7-1447e4cf25ae" TYPE="ext4" 
/dev/sda5: UUID="f823f340-4b48-43ac-8bb1-02ac53cadfa9" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
/dev/sdb1: LABEL="Temp" UUID="8565147c-5bd6-46e6-a471-26b20d32421f" TYPE="ext4" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/Temp type ext4 (rw,nosuid,nodev,uhelper=devkit)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=50fe7508-c8f1-4f48-bfa7-1447e4cf25ae ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=50fe7508-c8f1-4f48-bfa7-1447e4cf25ae

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        50fe7508-c8f1-4f48-bfa7-1447e4cf25ae
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=50fe7508-c8f1-4f48-bfa7-1447e4cf25ae ro quiet splash 
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        50fe7508-c8f1-4f48-bfa7-1447e4cf25ae
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=50fe7508-c8f1-4f48-bfa7-1447e4cf25ae ro  single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        50fe7508-c8f1-4f48-bfa7-1447e4cf25ae
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=50fe7508-c8f1-4f48-bfa7-1447e4cf25ae ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        50fe7508-c8f1-4f48-bfa7-1447e4cf25ae
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=50fe7508-c8f1-4f48-bfa7-1447e4cf25ae ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, memtest86+
uuid        50fe7508-c8f1-4f48-bfa7-1447e4cf25ae
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=50fe7508-c8f1-4f48-bfa7-1447e4cf25ae /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f823f340-4b48-43ac-8bb1-02ac53cadfa9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initrd.img-2.6.31-14-generic
    .0GB: boot/initrd.img-2.6.31-15-generic
    .0GB: boot/vmlinuz-2.6.31-14-generic
    .0GB: boot/vmlinuz-2.6.31-15-generic
    .0GB: initrd.img
    .0GB: initrd.img.old
    .0GB: vmlinuz
    .0GB: vmlinuz.old
```I did not receive the "ubuntu@ubuntu:~$" after the batch shell was running for a about ten minutes.  Multiple trials to same end.

I appreciate your patience.  I am losing mine.  I am seriously considering a full reinstall at this point.

---

