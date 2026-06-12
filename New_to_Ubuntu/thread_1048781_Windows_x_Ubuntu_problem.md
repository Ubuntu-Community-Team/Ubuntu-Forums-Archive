---
title: "Windows x Ubuntu problem"
date: 2009-01-23
forum: New to Ubuntu
---

### Post by Torak on 2009-01-23
I have a major problem. I have a 400G HD and installed Ubuntu 8.10x64 on a partitioned 80G. Now when I try to start both Windows options one takes me to a HP recovery and a Windows recovery(one that was one recovery drive). Is there ANY way at all to get Windows Vistax64 back without restoring to system factory and keeping all of my files? Please any help at all would be wonderful.

---

### Post by dnRoyston on 2009-01-23
HP recovery??? This might seem like a really stupid question, but I can't help but ask. Is the CD tray occupied? This happened to me multiples of times.

Sorry for the stupid question

---

### Post by Synt4xError on 2009-01-23
What do you mean when you try to start both windows options? Explain a bit more please.

---

### Post by Torak on 2009-01-23
Disc tray is empty just checked.

> **Synt4xError said:**
> What do you mean when you try to start both windows options? Explain a bit more please.

I see two "Windows Vista/Longhorn (loader)".

---

### Post by Synt4xError on 2009-01-23
and you can't log into either of them?

---

### Post by Torak on 2009-01-23
> **Synt4xError said:**
> and you can't log into either of them?

I can run both yes but one takes me too a HP recovery and the recovery drive that was on my laptop. I really dont think that Ubuntu messed with any of the files because when I look on my partition in Ubuntu nothing has changed. I think the HP recovery (i say this because on my older laptop Vista worked under the second option) is just over reacting.

---

### Post by halitech on 2009-01-23
whats the output of```
sudo fdisk -l
``` and ```
cat /boot/grub/menu.lst
```

---

### Post by caljohnsmith on 2009-01-23
**Torak**, in order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what it will take to boot Vista.

---

### Post by Torak on 2009-01-23
sudo fdisk -l
```
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x89900f6b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       36459   292856886    7  HPFS/NTFS
/dev/sda2           36460       46956    84317152+   5  Extended
/dev/sda3           46957       48641    13531136    7  HPFS/NTFS
/dev/sda5           36460       46523    80839048+  83  Linux
/dev/sda6           46524       46956     3478041   82  Linux swap / Solaris


```
cat /boot/grub/menu.lst
```
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
# kopt=root=UUID=40620881-c8bc-4cff-8d2d-e88ae0592c7f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=40620881-c8bc-4cff-8d2d-e88ae0592c7f

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

title Ubuntu 8.10x64
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=40620881-c8bc-4cff-8d2d-e88ae0592c7f ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=40620881-c8bc-4cff-8d2d-e88ae0592c7f ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=40620881-c8bc-4cff-8d2d-e88ae0592c7f ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=40620881-c8bc-4cff-8d2d-e88ae0592c7f ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1
savedefault
makeactive

```

Results.txt
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr

sda2: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sdb1': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sdb1 sdb1 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sdb1 sdb1 ntfs-3g force 0 0

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders, total 781422768 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x89900f6b

Partition  Boot        Start          End         Size  Id System

/dev/sda1    *            63  585,713,834  585,713,772   7 HPFS/NTFS
/dev/sda2        585,713,835  754,348,139  168,634,305   5 Extended
/dev/sda5        585,713,898  747,391,994  161,678,097  83 Linux
/dev/sda6        747,392,058  754,348,139    6,956,082  82 Linux swap / Solaris
/dev/sda3        754,354,176  781,416,447   27,062,272   7 HPFS/NTFS


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107861504 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773167 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1725f60e

Partition  Boot        Start          End         Size  Id System

/dev/sdb1                 63  976,768,064  976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="4E401EBF5E239B86" TYPE="ntfs" 
/dev/sda3: UUID="2484CB3084CB0372" LABEL="RECOVERY" TYPE="ntfs" 
/dev/sda5: UUID="40620881-c8bc-4cff-8d2d-e88ae0592c7f" TYPE="ext3" 
/dev/sda6: UUID="59be609c-c9f7-4cbd-9fd6-937568a3e599" TYPE="swap" 
/dev/sdb1: UUID="58F82DB0F82D8D76" LABEL="SimpleDrive" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/trevor/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=trevor)
/dev/sda1 on /media/disk type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

=========================== sda5/boot/grub/menu.lst: ===========================

default 0
timeout 10

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
# kopt=root=UUID=40620881-c8bc-4cff-8d2d-e88ae0592c7f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=40620881-c8bc-4cff-8d2d-e88ae0592c7f

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

title Ubuntu 8.10x64
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=40620881-c8bc-4cff-8d2d-e88ae0592c7f ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=40620881-c8bc-4cff-8d2d-e88ae0592c7f ro  single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=40620881-c8bc-4cff-8d2d-e88ae0592c7f ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=40620881-c8bc-4cff-8d2d-e88ae0592c7f ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu 8.10, memtest86+
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Other operating systems:
root

title Windows Vista/Longhorn (loader)
root (hd0,0)
chainloader +1
savedefault
makeactive

title Windows Vista/Longhorn (loader)
root (hd0,2)
chainloader +1
savedefault
makeactive


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=40620881-c8bc-4cff-8d2d-e88ae0592c7f /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=59be609c-c9f7-4cbd-9fd6-937568a3e599 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location  of files loaded by Grub: ===================


 314.0GB: boot/grub/menu.lst
 314.0GB: boot/grub/stage2
 314.0GB: boot/initrd.img-2.6.27-7-generic
 314.0GB: boot/initrd.img-2.6.27-9-generic
 314.0GB: boot/vmlinuz-2.6.27-7-generic
 314.0GB: boot/vmlinuz-2.6.27-9-generic
 314.0GB: initrd.img
 314.0GB: initrd.img.old
 314.0GB: vmlinuz
 314.0GB: vmlinuz.old

=============================== StdErr Messages: ===============================

No errors were reported.
```

---

### Post by caljohnsmith on 2009-01-24
So choosing either Windows Vista option in your menu.lst takes you to the HP/Vista recovery mode? How about posting the output of:
```
sudo mkdir /mnt/sda{1,3}
sudo mount /dev/sda1 /mnt/sda1 && ls -l /mnt/sda1
sudo mount /dev/sda3 /mnt/sda3 && ls -l /mnt/sda3
```
And we can work from there.

---

