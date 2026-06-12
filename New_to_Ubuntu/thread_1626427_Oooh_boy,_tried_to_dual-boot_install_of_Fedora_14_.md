---
title: "Oooh boy, tried to dual-boot install of Fedora 14 and did not succeed, or worse!"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by Robert.Thompson on 2010-11-20
Hello:

I used the 'shrink' option during the Fedora 14 install thinking that that also meant it would dual-boot, it doesn't!

Now my PC boots only into Fedora.

Can I get my Ubuntu 10.10 back or make my PC dual-boot so that I can access Ubuntu?

Any help would be appreciated.

Thanks,

---

### Post by coffeecat on 2010-11-20
Fedora is notorious for not setting up it's own grub so that you can boot into other Linux distros that are also on the hard drive. Hopefully, it has not wiped out your Ubuntu, merely set up an inadequate grub menu. And, knowing Fedora, it will probably have set the grub menu to be hidden. Recognise the voice of bitter experience? Correct! :)

In Fedora, open a terminal and su to root. Post the output of:

```
fdisk -lu
```and...

```
blkid
```Also, post the contents of the file /boot/grub/menu.lst.

If Ubuntu is still there, we'll soon get you sorted.

---

### Post by Robert.Thompson on 2010-11-20
Sorry for delay - having lots of trouble today!

fdisk -lu:

[root@localhost rob]# fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003ae7d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   149803007    74900480   83  Linux
/dev/sda2       299810814   312580095     6384641    5  Extended
/dev/sda3       149803008   150827007      512000   83  Linux
/dev/sda4       150827008   299808767    74490880   8e  Linux LVM
/dev/sda5       299810816   312580095     6384640   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/dm-0: 36.9 GB, 36909875200 bytes
255 heads, 63 sectors/track, 4487 cylinders, total 72089600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-0 doesn't contain a valid partition table

Disk /dev/dm-1: 5301 MB, 5301600256 bytes
255 heads, 63 sectors/track, 644 cylinders, total 10354688 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-1 doesn't contain a valid partition table

Disk /dev/dm-2: 34.1 GB, 34057748480 bytes
255 heads, 63 sectors/track, 4140 cylinders, total 66519040 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/dm-2 doesn't contain a valid partition table
[root@localhost rob]# ^C


blkid:

[root@localhost rob]# blkid
/dev/sda1: UUID="04d81503-e0e6-4a58-952c-d20bf158a08a" TYPE="ext4" 
/dev/sda3: UUID="78589435-35ad-4fb7-aab7-37c6a09a14b3" TYPE="ext4" 
/dev/sda4: UUID="rE0Pyq-7hY8-mkya-EUCF-Lv4X-gsAg-QluV7E" TYPE="LVM2_member" 
/dev/sda5: UUID="497e765a-748a-44d1-af26-5ebeb6f0bf28" TYPE="swap" 
/dev/mapper/VolGroup-lv_root: LABEL="_Fedora-14-i686-" UUID="ea5906d9-f240-4256-885c-e2c0b1e9576a" TYPE="ext4" 
/dev/mapper/VolGroup-lv_swap: UUID="44f6af3c-a0d1-4d62-8edc-a9a0818c9489" TYPE="swap" 
/dev/mapper/VolGroup-lv_home: UUID="a34451f6-03b5-4768-a1b0-03bf4b81ee84" TYPE="ext4" 
[root@localhost rob]# 

/boot/grub/menu.lst:

Having trouble opening this file - tried AbiWord and got a blank document - any suggestions?

Thanks again for your help,

---

### Post by oldfred on 2010-11-20
Has Fedora finally converted to grub2?

To see all the details:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

---

### Post by Robert.Thompson on 2010-11-20
> **oldfred said:**
> Has Fedora finally converted to grub2?

To see all the details:
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code][ /code] tags.

```

 Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 
    150344284 on boot drive #1 for the stage2 file. A stage2 file is at this 
    location on /dev/sda. Stage2 looks on partition #3 for /grub/grub.conf.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda4: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

VolGroup-lv_root: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Fedora release 14 (Laughlin) 
                       Kernel on an ()
    Boot files/dirs:   /etc/fstab

VolGroup-lv_home: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

VolGroup-lv_swap: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048   149,803,007   149,800,960  83 Linux
/dev/sda2         299,810,814   312,580,095    12,769,282   5 Extended
/dev/sda5         299,810,816   312,580,095    12,769,280  82 Linux swap / Solaris
/dev/sda3         149,803,008   150,827,007     1,024,000  83 Linux
/dev/sda4         150,827,008   299,808,767   148,981,760  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/VolGroup-lv_home a34451f6-03b5-4768-a1b0-03bf4b81ee84   ext4                                     
/dev/mapper/VolGroup-lv_root ea5906d9-f240-4256-885c-e2c0b1e9576a   ext4       _Fedora-14-i686-              
/dev/mapper/VolGroup-lv_swap 44f6af3c-a0d1-4d62-8edc-a9a0818c9489   swap                                     
/dev/sda1        04d81503-e0e6-4a58-952c-d20bf158a08a   ext4                                     
/dev/sda2: PTTYPE="dos" PART_ENTRY_SCHEME="dos" PART_ENTRY_TYPE="0x5" PART_ENTRY_NUMBER="2" 
/dev/sda3        78589435-35ad-4fb7-aab7-37c6a09a14b3   ext4                                     
/dev/sda4        rE0Pyq-7hY8-mkya-EUCF-Lv4X-gsAg-QluV7E LVM2_member                               
/dev/sda5        497e765a-748a-44d1-af26-5ebeb6f0bf28   swap                                     
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
VolGroup-lv_home
VolGroup-lv_root
VolGroup-lv_swap

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/mapper/VolGroup-lv_root /                        ext4       (rw)
/dev/sda3        /boot                    ext4       (rw)
/dev/mapper/VolGroup-lv_home /home                    ext4       (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 04d81503-e0e6-4a58-952c-d20bf158a08a
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos1)'
search --no-floppy --fs-uuid --set 04d81503-e0e6-4a58-952c-d20bf158a08a
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 04d81503-e0e6-4a58-952c-d20bf158a08a
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=04d81503-e0e6-4a58-952c-d20bf158a08a ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 04d81503-e0e6-4a58-952c-d20bf158a08a
    echo    'Loading Linux 2.6.35-23-generic ...'
    linux    /boot/vmlinuz-2.6.35-23-generic root=UUID=04d81503-e0e6-4a58-952c-d20bf158a08a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 04d81503-e0e6-4a58-952c-d20bf158a08a
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=04d81503-e0e6-4a58-952c-d20bf158a08a ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 04d81503-e0e6-4a58-952c-d20bf158a08a
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=04d81503-e0e6-4a58-952c-d20bf158a08a ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 04d81503-e0e6-4a58-952c-d20bf158a08a
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 04d81503-e0e6-4a58-952c-d20bf158a08a
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=04d81503-e0e6-4a58-952c-d20bf158a08a /               ext4    errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0

=================== sda1: Location of files loaded by Grub: ===================


  14.1GB: boot/grub/core.img
  11.6GB: boot/grub/grub.cfg
  29.3GB: boot/initrd.img-2.6.32-25-generic
  11.5GB: boot/initrd.img-2.6.35-23-generic
  14.2GB: boot/vmlinuz-2.6.32-25-generic
  14.2GB: boot/vmlinuz-2.6.35-23-generic
  11.5GB: initrd.img
  29.3GB: initrd.img.old
  14.2GB: vmlinuz
  14.2GB: vmlinuz.old

============================= sda3/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,2)
#          kernel /vmlinuz-version ro root=/dev/mapper/VolGroup-lv_root
#          initrd /initrd-[generic-]version.img
#boot=/dev/sda
default=0
timeout=0
splashimage=(hd0,2)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.35.6-45.fc14.i686)
    root (hd0,2)
    kernel /vmlinuz-2.6.35.6-45.fc14.i686 ro root=/dev/mapper/VolGroup-lv_root rd_LVM_LV=VolGroup/lv_root rd_LVM_LV=VolGroup/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.35.6-45.fc14.i686.img

=================== sda3: Location of files loaded by Grub: ===================


  76.9GB: grub/grub.conf
  76.9GB: grub/menu.lst
  76.9GB: grub/stage2
  76.7GB: initramfs-2.6.35.6-45.fc14.i686.img
  76.7GB: initrd-plymouth.img
  76.7GB: vmlinuz-2.6.35.6-45.fc14.i686

========================= VolGroup-lv_root/etc/fstab: =========================


#
# /etc/fstab
# Created by anaconda on Fri Nov 19 17:14:05 2010
#
# Accessible filesystems, by reference, are maintained under '/dev/disk'
# See man pages fstab(5), findfs(8), mount(8) and/or blkid(8) for more info
#
/dev/mapper/VolGroup-lv_root /                       ext4    defaults        1 1
UUID=78589435-35ad-4fb7-aab7-37c6a09a14b3 /boot                   ext4    defaults        1 2
/dev/mapper/VolGroup-lv_home /home                   ext4    defaults        1 2
/dev/mapper/VolGroup-lv_swap swap                    swap    defaults        0 0
UUID=497e765a-748a-44d1-af26-5ebeb6f0bf28 swap                    swap    defaults        0 0
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
=======Devices which don't seem to have a corresponding hard drive==============

sdb 
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically


```

---

### Post by Favux on 2010-11-20
Hi Robert.Thompson,

Just went through this yesterday.  Follow the Ubuntu wiki:  [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)  using the Simplest method to reinstall grub2 from the live CD.  Then 'sudo update-grub' will get you Fedora back.

---

### Post by Robert.Thompson on 2010-11-20
Did you mean that I would get my "Ubuntu" back?

I have Fedora and would like Ubuntu, or both.

Thanks,

---

### Post by oldfred on 2010-11-20
You just missed on the code tag.:)
DE] should be here.

[/CODE]

If you go back and add the DE] to the end of the [CO at the beginning it will convert to code tags display.

Installing grub2 from sda1 into the MBR will automatically boot Ubuntu and the sudo update-grub (after booting Ubuntu) should find Fedora & let you boot that also.

You can do this from Fedora or the liveCD.

#Install MBR from LiveCD, Ubuntu install on sda1 and want grub2 in drive sda's MBR:
#Find linux partition, change sda1 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by coffeecat on 2010-11-20
> **oldfred said:**
> Has Fedora finally converted to grub2?

No, it still uses legacy grub and its configuration file is grub.conf (just to be different) with menu.lst a symlink to grub.conf. Of course, what I'd forgotten is that left to its own devices it sets up a separate boot partition, which is why the OP couldn't open /boot/grub/menu.lst. I'd forgotten, because I always slap the Fedora installer firmly on the wrist to get it to install to the partitions I want rather than what it wants.


> **Robert.Thompson said:**
> Did you mean that I would get my "Ubuntu" back?

I have Fedora and would like Ubuntu, or both.

Thanks,

Go with Favux's link and post. It's much the simplest way. That will get you Ubuntu's grub menu back. Then after you boot into Ubuntu run 'sudo update-grub' and the Ubuntu menu will have an entry for Fedora when you next boot up. Sorry I misled you about /boot/grub/menu.lst. Memory lapse. Reason above.

---

### Post by Robert.Thompson on 2010-11-22
> **coffeecat said:**
> No, it still uses legacy grub and its configuration file is grub.conf (just to be different) with menu.lst a symlink to grub.conf. Of course, what I'd forgotten is that left to its own devices it sets up a separate boot partition, which is why the OP couldn't open /boot/grub/menu.lst. I'd forgotten, because I always slap the Fedora installer firmly on the wrist to get it to install to the partitions I want rather than what it wants.




Go with Favux's link and post. It's much the simplest way. That will get you Ubuntu's grub menu back. Then after you boot into Ubuntu run 'sudo update-grub' and the Ubuntu menu will have an entry for Fedora when you next boot up. Sorry I misled you about /boot/grub/menu.lst. Memory lapse. Reason above.

Sorry, again, for the delay - I was at my country house where the internet reception on Bell Mobility is very intermittent.

I did install separate root, boot, home and swap partitions when I installed Ubuntu.

So, before I start pressing the 'enter key' in a terminal, here are the commands I plan to use.
<BOOT FROM UBUNTU 10.10 LIVE-CD>
1) sudo mount /dev/sda1 /mnt
2) sudo mount /dev/sda2 /mnt/boot
3) sudo mount /dev/sda4 /mnt/home
4) sudo grub-install --root-directory=/mnt/ /dev/sda
<REBOOT>
5) sudo update-grub

 If anyone knows that they are correct, please let me know so that I can proceed.


Thanks

---

### Post by Robert.Thompson on 2010-11-22
I tried item # 1 and received no error msg; I was returned to the terminal prompt.

So I tried # 2 and received:

ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt/boot
mount: you must specify the filesystem type
ubuntu@ubuntu:~$ 


Then I tried:

ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda2 /mnt/boot
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
ubuntu@ubuntu:~$ 

Any ideas? Thanks.

---

### Post by oldfred on 2010-11-22
According to the boot script sda2 is the extended partition not /boot. So you cannot mount it.

In fact the script does not show a separate /boot. All the grub & kernel files for Ubuntu are in sda1.

---

### Post by Robert.Thompson on 2010-11-22
> **oldfred said:**
> According to the boot script sda2 is the extended partition not /boot. So you cannot mount it.

In fact the script does not show a separate /boot. All the grub & kernel files for Ubuntu are in sda1.

Thank you!

I thought that I had installed root, boot, home and swap - before I choose the resize option in Fedora - I guess I am, as always, confused.

So, would the following terminal commands be correct?

<BOOT FROM UBUNTU 10.10 LIVE-CD>
1) sudo mount /dev/sda1 /mnt
2) sudo mount /dev/sda4 /mnt/home
3) sudo grub-install --root-directory=/mnt/ /dev/sda
<REBOOT>
4) sudo update-grub

Thanks,

---

### Post by Robert.Thompson on 2010-11-22
Well, I tried:

<BOOT FROM UBUNTU 10.10 LIVE-CD>
1) sudo mount /dev/sda1 /mnt
2) sudo mount /dev/sda4 /mnt/home
3) sudo grub-install --root-directory=/mnt/ /dev/sda
<REBOOT>
4) sudo update-grub

Number 2 above failed but I proceeded anyway.

I rebooted, NOT WITH THE UBUNTU LIVE_CD, and I my ubuntu was back.

I did the sudo update-grub and rebooted.

Now the PC boots into my ubuntu and Fedora is nowhere to be seen!

This is not exactly what I wanted - can I get a dual-boot where I can pick between Ubuntu and Fedora?

Thanks,

---

### Post by oldfred on 2010-11-22
The script says sda4 is a LVM. I have never used LVM and do not know about it. I do not think you can just mount sda4. If /home is inside the LVM you have to mount that.

I am not sure you have to mount /home just to reinstall grub. I have seen it both ways?

---

### Post by nm_geo on 2010-11-22
*Fedora* default Logical Volume Management (*LVM*) configuration.  I had a similar experinece with my first installation of Fedora and just used Gparted to remove the Fedora partitions and made sure I pointed the Fedora boot to the first partition made for Fedora on the second install.

It does seem to me that reinstalling the Grub2 would solve the problems in the 1st Ubuntu partition.

---

### Post by nm_geo on 2010-11-22
This is not exactly what I wanted - can I get a dual-boot where I can pick between Ubuntu and Fedora?

Thanks,

You could delete the Fedora partitions and reinstall be sure the grub for Fedora is placed in it's first partition. It about the last screen you will see during the installation, then you will be booting with the Grub2 and Fedora will be found.

---

### Post by oldfred on 2010-11-22
We can try this:

copy this into your 40_custom

gksudo gedit /etc/grub.d/40_custom
then 
sudo update-grub

```
menuentry "Fedora (2.6.35.6-45.fc14.i686)" {
    recordfail=1
    if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,3)
    linux /vmlinuz-2.6.35.6-45.fc14.i686 ro root=/dev/mapper/VolGroup-lv_root rd_LVM_LV=VolGroup/lv_root rd_LVM_LV=VolGroup/lv_swap rd_NO_LUKS rd_NO_MD rd_NO_DM LANG=en_US.UTF-8 SYSFONT=latarcyrheb-sun16 KEYBOARDTYPE=pc KEYTABLE=us rhgb quiet
    initrd /initramfs-2.6.35.6-45.fc14.i686.img
}

```

---

### Post by Robert.Thompson on 2010-11-22
I gave up. see: [http://ubuntuforums.org/showthread.php?t=1628265](http://ubuntuforums.org/showthread.php?t=1628265)

Thank you all for your time and effort.

To say that I am discouraged about linux would be a vast understatement. There is sooooo much to learn and understand. I have books but I don't seem to get it. It's like there is no step by step way through this stuff.

Thanks again for all your help,

---

### Post by coffeecat on 2010-11-22
> **Robert.Thompson said:**
> To say that I am discouraged about linux would be a vast understatement.

I'm sorry to hear that. Please don't let your experience of trying to multi-boot with Fedora and Ubuntu put you off. Fedora is a damn-fine distro but it does have its own quirks, most of which seem to have tripped you up: its use of LVM, its obsession with separate boot partitions, and the anti-social way it ignores the presence of other Linux distros when setting up grub. 

Fedora feels very different from Ubuntu in many ways so you may be better off sticking with just Ubuntu until you are more confident with Linux generally.

---

