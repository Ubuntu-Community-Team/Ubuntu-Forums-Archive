---
title: "I couldn't boot into my system through grub!!"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by MBG1987 on 2010-06-19
I've just installed ubuntu 10.04 lucid lynx, every thing went well ,except grub gave me an error message:
 error: > You need to load the Kernel First or something similar , i searched the web looking for similar problem, but unfortunately non of the solutions work! like reinstalling grub, and still got the same pretty message!

any help folks?

---

### Post by drs305 on 2010-06-19
We need to know some specifics to troubleshoot your problem. Please run *meierfra's* boot info script (from the LiveCD if necessary) and post the results between "code tags" (use the # icon in the post's menu to generate the tags):
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by MBG1987 on 2010-06-19
thanks 4 the replay 
```
$ sh boot_info_script055.sh 
Please use "sudo" or become "root" to run this script.
ubuntu@ubuntu:~/Downloads$ sudo sh boot_info_script055.sh 
ubuntu@ubuntu:~/Downloads$ sudo chmod +x boot_info_script055.sh 
ubuntu@ubuntu:~/Downloads$ ./boot_info_script055.sh 
Please use "sudo" or become "root" to run this script.
ubuntu@ubuntu:~/Downloads$ sudo ./boot_info_script055.sh 
Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda2 for information... 
Searching sda5 for information... 
Searching sda3 for information... 
Searching sda4 for information... 
Finished. The results are in the file RESULTS.txt located in /home/ubuntu/Downloads

```RESULT.txt file content:


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda4 starts at sector 61432623.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    41,381,887    41,379,840  83 Linux
/dev/sda2          41,383,501    58,786,559    17,403,059   f W95 Ext d (LBA)
/dev/sda5          41,383,503    58,786,559    17,403,057  83 Linux
/dev/sda3          58,797,900    60,902,414     2,104,515  82 Linux swap / Solaris
/dev/sda4    *     61,432,623   312,560,639   251,128,017   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        81add52c-6465-4fca-ae46-26411de6d52e   ext4                                     
/dev/sda2: PTTYPE="dos" 
/dev/sda3                                               swap                                     
/dev/sda4        62E4D538E4D50F63                       ntfs                                     
/dev/sda5        e26702ad-6147-4dd6-ae68-69da7dcde797   ext4                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/1                 ext4       (rw)
/dev/sda4        /media/62E4D538E4D50F63  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  set saved_entry=${prev_saved_entry}
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z ${boot_once} ]; then
    saved_entry=${chosen}
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n ${have_grubenv} ]; then if [ -z ${boot_once} ]; then save_env recordfail; fi; fi
}
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 81add52c-6465-4fca-ae46-26411de6d52e
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
insmod ext2
set root='(hd0,1)'
search --no-floppy --fs-uuid --set 81add52c-6465-4fca-ae46-26411de6d52e
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ ${recordfail} = 1 ]; then
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
menuentry 'Ubuntu, with Linux 2.6.32-21-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 81add52c-6465-4fca-ae46-26411de6d52e
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=81add52c-6465-4fca-ae46-26411de6d52e ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-21-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-21-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 81add52c-6465-4fca-ae46-26411de6d52e
    echo    'Loading Linux 2.6.32-21-generic ...'
    linux    /boot/vmlinuz-2.6.32-21-generic root=UUID=81add52c-6465-4fca-ae46-26411de6d52e ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-21-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 81add52c-6465-4fca-ae46-26411de6d52e
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,1)'
    search --no-floppy --fs-uuid --set 81add52c-6465-4fca-ae46-26411de6d52e
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

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
UUID=81add52c-6465-4fca-ae46-26411de6d52e /               ext4    errors=remount-ro 0       1
/dev/sda3       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  17.3GB: boot/grub/core.img
  17.3GB: boot/grub/grub.cfg
  17.3GB: boot/initrd.img-2.6.32-21-generic
  17.3GB: boot/vmlinuz-2.6.32-21-generic
  17.3GB: initrd.img
  17.3GB: vmlinuz
```

---

### Post by garvinrick4 on 2010-06-19
You need to install grub2 in sda

Put in live CD,  your install CD and choose try Ubuntu. When it boots up go into gparted  right click on your sda install choose sda1 (that you say is your Ubuntu  install) and choose
label. Now label your partition to whatever you want I am going to use  lucid for this, make sure you click green apply arrow on top to apply  label. And sda1 for your partition with Ubuntu. Change either one if  different. Now open a terminal and use these commands.

     Code:
     sudo mkdir /media/lucid 
     
Code:
     sudo mount /dev/sda1 /media/lucid 
                               
Code:
     sudo grub-install --recheck --root-directory=/media/lucid [/dev/sda]("file:///media/dev/sda") 
     
Code:
     sudo umount /media/lucid 
 (not a typo)

You are making a directory for lucid install
you are mounting the drive
you are putting grub in sda in mbr. Not sda1 or sda5 but always sda
you are unmounting lucid and umount is right command
after labeling lucid mount point is now /media/lucid
I find it easier to use labels on partitions for learning purposes when  over 1 install.

Take out CD and boot into Ubuntu and run.

sudo update-grub

sudo grub-mkconfig

Done.    Sorry code was not in code tags copied and pasted from a previous post of mine.                                                                                           __________________
                Remember hence where you come and pass it down.
            Ubuntu member #899097
[http://psychocats.net/ubuntu/index.php](http://psychocats.net/ubuntu/index.php)
[http://ubuntuguide.org/wiki/Main_Page](http://ubuntuguide.org/wiki/Main_Page)

---

### Post by arrange on 2010-06-19
Everything seems OK, strange...

Can you check the partition filesystem, for example with *GParted* or *fsck*?
Can you check the state of the HDD (*Palimpsest Disk Utility*)?
Are the necessary files readable? Boot into LiveCD, mount the */dev/sda1* (Ubuntu) partition and run```

md5sum /media/*/boot/initrd.img-2.6.32-21-generic /media/*/boot/vmlinuz-2.6.32-21-generic

```

---

### Post by MBG1987 on 2010-06-19
> You need to install grub2 in sda

Put in live CD,  your install CD and choose try Ubuntu. When it boots up  go into gparted  right click on your sda install choose sda1 (that you  say is your Ubuntu  install) and choose
label. Now label your partition to whatever you want I am going to use   lucid for this, make sure you click green apply arrow on top to apply   label. And sda1 for your partition with Ubuntu. Change either one if   different. Now open a terminal and use these commands.

     Code:
     sudo mkdir /media/lucid 
     
Code:
     sudo mount /dev/sda1 /media/lucid 
                               
Code:
     sudo grub-install --recheck --root-directory=/media/lucid [/dev/sda]("file:///media/dev/sda") 
     
Code:
     sudo umount /media/lucid 
 (not a typo)

You are making a directory for lucid install
you are mounting the drive
you are putting grub in sda in mbr. Not sda1 or sda5 but always sda
you are unmounting lucid and umount is right command
after labeling lucid mount point is now /media/lucid
I find it easier to use labels on partitions for learning purposes when   over 1 install.

thank you, but i did all these steps as i mentioned above, still getting that error message preventing me from logging into my ubuntu 
> 

Take out CD and boot into Ubuntu and run.

sudo update-grub

sudo grub-mkconfig

ohh, it will be very nice if could boot into ubuntu that on sda1, but like i said that's that's the issue

any more suggestions ?

---

### Post by garvinrick4 on 2010-06-19
I am sorry I did not see a boot flag on sda1 which is your Ubuntu install and figured if you put grub2 in sda's mbr would boot into your installs. There are a lot of people around these forums that have a lot of grub experience that will help. Ask them if not having a boot flag in sda1 with not having a seperate boot partition with a boot flag has any effect. But after you put in this code it gave you a message that all went OK or not?
```

sudo grub-install --recheck --root-directory=/media/lucid [/dev/sda]("file:///media/dev/sda") 
```

---

### Post by MBG1987 on 2010-06-19
> Everything seems OK, strange...

Can you check the partition filesystem, for example with *GParted*  or *fsck*?
Can you check the state of the HDD (*Palimpsest Disk Utility*)?
Are the necessary files readable? Boot into LiveCD, mount the */dev/sda1*  (Ubuntu) partition and run     Code:
     md5sum /media/*/boot/initrd.img-2.6.32-21-generic /media/*/boot/vmlinuz-2.6.32-21-generic
```
ubuntu@ubuntu:/media$ md5sum /media/1/boot/initrd.img-2.6.32-21-generic /media/1/boot/vmlinuz-2.6.32-21-generic
78a8403742a3a3c2740778a58b8ab75b  /media/1/boot/initrd.img-2.6.32-21-generic
1c0d4864792ec0bb7660f303f805a2fe  /media/1/boot/vmlinuz-2.6.32-21-generic


```> 
I am sorry I did not see a boot flag on sda1 which is your Ubuntu  install and figured if you put grub2 in sda's mbr would boot into your  installs. There are a lot of people around these forums that have a lot  of grub experience that will help. Ask them if not having a boot flag in  sda1 with not having a seperate boot partition with a boot flag has any  effect. But after you put in this code it gave you a message that all  went OK or not?
     Code:
     sudo grub-install --recheck --root-directory=/media/lucid [/dev/sda]("file:///media/dev/sda")
```
ubuntu@ubuntu:/media$ sudo grub-install --recheck --root-directory=/media/1 /dev/sda
Installation finished. No error reported.

```

---

### Post by drs305 on 2010-06-20
I can't see a problem with your system from the RESULTS.txt.

I was looking for a simpler solution, but since you have made a new post asking how to install a kernel through the LiveCD, I'll provide a possible solution here.

I can think of two things you could try, both from the LiveCD using the chroot procedure. It would have you mount the Linux partition, then mount the necessary system folders and chroot to allow you to make changes to the real installation rather than the LiveCD files.

First: Attempt to reinstall the kernel via chroot.
This command mounts sda1 and then chroot's into it after mounting the appropriate systems folders.
```

sudo mount /dev/sda1 /mnt && sudo mount --bind /dev /mnt/dev && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys && sudo mount --bind /dev/pts /mnt/dev/pts && sudo cp /etc/resolv.conf /mnt/etc/resolv.conf && sudo chroot /mnt

```
Next, install or reinstall the latest generic kernel:
```
apt-get update
apt-get install linux-image-generic
```
If you get a message that it is already installed, run this command:
```
apt-get install --reinstall linux-image-generic
```

Once you have installed the kernel, update grub, umount what you mounted, and then exit chroot:
```
update-grub
sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /dev/sda1
exit
```
Finally, unmount what you previously mounted:
```

sudo umount /mnt/dev/pts && sudo umount /mnt/sys && sudo umount /mnt/proc && sudo umount /mnt/dev && sudo umount /mnt

```
Reboot.

If this did not correct the problem the other option I'd recommend would be to completely uninstall and reinstall Grub2. Only do this if you have a reliable power source and internet connection. The reason is that for a minute or so you will have no bootloader on your machine.

Accomplish the same chroot procedures as above, then run these commands. The packages aren't the same but due to dependencies *grub-common* and *grub-pc* will both be removed and then reinstalled with these commands.

After mounting and chrooting as above:
```
apt-get purge grub-common
apt-get install grub-pc
```
Accept whatever comes up in the linux options and tab to "OK" and then press ENTER.

When it shows the partitions, highlight **sda** only and press the space bar to place an asterisk next to it. Do not select any of the partitions, only the *sda *drive. Tab to OK and again press ENTER.

Exit and unmount as previously. Reboot.

If Windows isn't found on reboot, run "sudo update-grub".

---

### Post by MBG1987 on 2010-06-20
I've successfully installed latest kernel as you told me, but nothing fixed, i figure out that problem not from the kernel nor grub but from installation process, so i reinstall ubutnu 10.4 from scratch, and that fixed the problem.

thanks for all replays especially from @drs305 
see you in other problem lol

---

### Post by drs305 on 2010-06-20
> **MBG1987 said:**
> i figure out that problem not from the kernel nor grub but from installation process, so i reinstall ubutnu 10.4 from scratch, and that fixed the problem.


Glad you figured out a solution, even though a reinstall was necessary.

If you would mark this thread SOLVED via the Thread Tools link at the top right of the first post it will give us more time to concentrate on other problems, *including your next one*!  ;-)

---

### Post by george2064 on 2010-06-22
I have the same issue ... how do you reinstall 10.04 ... since I can't get into the system at all?

---

### Post by arrange on 2010-06-22
Boot into a LiveCD... Back up your */home*... Reinstall.

---

