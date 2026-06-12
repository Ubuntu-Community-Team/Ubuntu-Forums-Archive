---
title: "Problem activating swap - etc/fstab can't be mounted"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by robine on 2010-02-28
Hi... I have no idea what to do :|

It started this evening after Firefox crashed while I was trying to watch a YouTube video (another poster here mentioned something similar). I can't boot normally; right now I'm on the live CD to seek help.

I went to System > Administration > GParted to find the swap partition UUID (760878d8-6c0f-4841-9b96-3c80672605e1). I thought maybe that was the problem - the swap partition not mounting at boot up. I tried "sudo nano -Bw /etc/fstab" in terminal. Here is what I ended up with:

> # /etc/fstab: static file system information
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
# <file system>  <mount point>  <type>  <options>  <dump>  <pass>
proc   /proc   proc   defaults   0   0
# / was on /dev/sdb1 during installation
UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158  /  ext3  errors=remount=ro 0  1
# /home was on /dev/sda1 during installation
UUID=a31097ec-c78d-4760-9cf0-2cfcd5aff759  /home  ext3  defaults  0  2
# swap was on /dev/sdb5 during installation
UUID=760878d8-6c0f-4841-9b96-3c80672605e1  none  swap  sw  0  0
/dev/scd0   media/cdrom0   udf , iso9660 user,noauto,exec,utf8  0  0
/dev/fd0 media/floppy0 auto rw,user,noauto,exec,utf8 0 0I am only a beginner here... but I'm wondering if, from the info above, this means that one drive isn't being "seen" on boot up? It says "remount" - is this something I have to do; unmount the drive and then remount? If so... how? The UUID for the swap partition is correct, and I haven't changed any settings at all today, so I've no idea how this came about!

Also, when trying to reboot from recovery shell, here is the information on the screen (it wouldn't progress any further than this):

> init: mountall-shell main process (763) killed by TERM signal
Hangup
root@robine-desktop: ~# mountall start/starting
General error mounting filesystems.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@robine-desktop: ~# swapon: /dev/disk/by-uuid/760878d8-6c0f-4841-9b96-3c80672605e1: swapon failed: Device or resource busy
mountall: swapon /dev/disk/by-uuid/760878d8-6c0f-4841-9b96-3c80672605e1 [1158] terminated with status 255
mountall: Problem activating swap: /dev/disk/by-uuid/760878d8-6c0f-4841-9b96-3c80672605e1
One or more of the mounts listed in etc/fstab cannot yet be mounted: (ESC for recovery shell)
/home: waiting for UUID=a31097ec-c78d-47b0-9cf0-2cfcd5aff759
mountall: CancelledAny help is very appreciated, as I am very lost right now!!

---

### Post by presence1960 on 2010-02-28
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by robine on 2010-02-28
That worked just as you said it would. Thanks for responding so fast!
Here it is:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xadece77e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    39,070,079    39,070,017  83 Linux
/dev/sda2          39,070,080    72,292,499    33,222,420   5 Extended
/dev/sda5          39,070,143    72,292,499    33,222,357  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        bea739ac-dc3a-4af4-ba1b-9430e11d5158   ext3                                     
/dev/sda5        760878d8-6c0f-4841-9b96-3c80672605e1   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=a31097ec-c78d-47b0-9cf0-2cfcd5aff759 /home           ext3    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=760878d8-6c0f-4841-9b96-3c80672605e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .5GB: boot/grub/core.img
    .5GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-16-generic-pae
    .6GB: boot/vmlinuz-2.6.31-16-generic-pae
    .5GB: initrd.img
    .6GB: vmlinuz
```

---

### Post by robine on 2010-03-01
Help? Please :|

---

### Post by plucky on 2010-03-01
I think you have lost a drive as the /dev/sdb drive seems to be missing. > Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xadece77e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    39,070,079    39,070,017  83 Linux
/dev/sda2          39,070,080    72,292,499    33,222,420   5 Extended
/dev/sda5          39,070,143    72,292,499    33,222,357  82 Linux swap / Solaris

Your /home partition is mounted on what should be /dev/sda1,but because the drive is missing,the second drive is being seen as /dev/sda.

Post output of ```
sudo fdisk -l
```

Check in the BIOS and see if you can see both drives.

```
# /home was on /dev/sda1 during installation
UUID=a31097ec-c78d-47b0-9cf0-2cfcd5aff759 /home           ext3    defaults        0       2
```


Good Luck

---

### Post by presence1960 on 2010-03-01
```
=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[COLOR="Red"]# / was on /dev/sdb1 during installation
UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 /               ext3 [/COLOR]   errors=remount-ro 0       1
[COLOR="Red"]# /home was on /dev/sda1 during installation
UUID=a31097ec-c78d-47b0-9cf0-2cfcd5aff759 /home           ext3  [/COLOR]  defaults        0       2
[COLOR="Red"]# swap was on /dev/sdb5 during installation
UUID=760878d8-6c0f-4841-9b96-3c80672605e1 none            swap    sw              0       0[/COLOR]
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
```

change:```
# / was on /dev/sdb1 during installation
UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 /  
```

To: ```
# / was on /dev/sda1 during installation
UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 /
```

Change: ```
# swap was on /dev/sdb5 during installation
UUID=760878d8-6c0f-4841-9b96-3c80672605e1 none            swap    sw              0       0
```

To: ```
# swap was on /dev/sda5 during installation
UUID=760878d8-6c0f-4841-9b96-3c80672605e1 none            swap    sw              0       0
```

Delete this entire entry: ```
/home was on /dev/sda1 during installation
UUID=a31097ec-c78d-47b0-9cf0-2cfcd5aff759 /home           ext3    defaults        0       2  
```

It looks like you removed the disk that was formerly sda which had your /home partition. Now the former sdb becomes sda. If you removed the former sda follow this. if you did not remove a hard disk then you have other problems.

To accomplish the above I would boot from the ubuntu Live CD & choose "try ubuntu without any changes". When the desktop loads go Places > Computer to open a file browser. On the left pane highlight your sda1 (ubuntu / partition) to mount it. You will know it is mounted when you see directories to right.

Now open a terminal and run ```
gksu nautilus
```This will open a file browser with root priviledge. Again on the left pane highlight the sda1 partition. Now navigate to /etc and open the fstab file. Make the changes noted above. Click Save on toolbar & close file. Close both file browsers and reboot without the live cd. See what happens.

---

### Post by robine on 2010-03-02
Hi - thanks for your response! :)

I can't imagine why one of my hard disks would suddenly disappear. After a few more reboots, suddenly "grub loading..." was displayed (this had not been the case so far while having this problem). And then, my desktop and all settings were restored.

The difference was this: I have an external hard drive that I use for storing music. This has its own power switch and turns on separately from my desktop. When I switched it on before the desktop, nothing happened - still had the issue. But when I switched it on just after switching on the desktop power, suddenly everything was restored. 

How can this be? I don't have Ubuntu installed on my external drive.

I'm hesitant to change the settings as mentioned before I know the source of the problem. I didn't remove or switch any hard drives - why would one suddenly stop being seen?

---

### Post by presence1960 on 2010-03-02
> **robine said:**
> Hi - thanks for your response! :)

I can't imagine why one of my hard disks would suddenly disappear. After a few more reboots, suddenly "grub loading..." was displayed (this had not been the case so far while having this problem). And then, my desktop and all settings were restored.

The difference was this: I have an external hard drive that I use for storing music. This has its own power switch and turns on separately from my desktop. When I switched it on before the desktop, nothing happened - still had the issue. But when I switched it on just after switching on the desktop power, suddenly everything was restored. 

How can this be? I don't have Ubuntu installed on my external drive.

I'm hesitant to change the settings as mentioned before I know the source of the problem. I didn't remove or switch any hard drives - why would one suddenly stop being seen?

If your hard disk suddenly reappeared then you need do nothing as I mentioned above to fstab. The problem was the disappearing hard disk. Note what I said in my post > It looks like you removed the disk that was formerly sda which had your /home partition. Now the former sdb becomes sda. If you removed the former sda follow this. if you did not remove a hard disk then you have other problems.

Now that you have both disks working why don't you run another boot info script with the external plugged in and we will see what you have now. If you can boot into ubuntu do the following, if not do as before with the Live CD to run the script:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

 This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

P.S. I would check power connection from hard disk to PSU and from connections from hard disk to mobo. make sure all are seated properly. Hopefully it is something that simple as loose connection.

---

### Post by robine on 2010-03-02
Okay. I've stayed logged in with Ubuntu (without shutting down hard disk from yesterday, just in case same problem occurred!), so no need to use the live CD just yet. The external drive remains switched on.

Here we go:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks for 
    (UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158)/boot/grub.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdc1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sdc1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdc1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe919e919

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,296,384   156,296,322  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xadece77e

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63    39,070,079    39,070,017  83 Linux
/dev/sdb2          39,070,080    72,292,499    33,222,420   5 Extended
/dev/sdb5          39,070,143    72,292,499    33,222,357  82 Linux swap / Solaris


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x481225b1

Partition  Boot         Start           End          Size  Id System

/dev/sdc1                  63   490,234,751   490,234,689   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        a31097ec-c78d-47b0-9cf0-2cfcd5aff759   ext3                                     
/dev/sdb1        bea739ac-dc3a-4af4-ba1b-9430e11d5158   ext3                                     
/dev/sdb5        760878d8-6c0f-4841-9b96-3c80672605e1   swap                                     
/dev/sdc1        71AB-1F06                              vfat       EXTERNAL HD                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sdb1        /                        ext3       (rw,errors=remount-ro)
/dev/sda1        /home                    ext3       (rw)
/dev/sdc1        /media/EXTERNAL HD       vfat       (rw,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sdb1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sdb1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=a31097ec-c78d-47b0-9cf0-2cfcd5aff759 /home           ext3    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=760878d8-6c0f-4841-9b96-3c80672605e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb1: Location of files loaded by Grub: ===================


    .5GB: boot/grub/core.img
    .5GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-16-generic-pae
    .6GB: boot/vmlinuz-2.6.31-16-generic-pae
    .5GB: initrd.img
    .6GB: vmlinuz
```

---

### Post by robine on 2010-03-02
Also: I haven't yet checked connections to motherboard etc as this will require that I power off computer and take off entire case, etc. However, if necessary I will do so.

---

### Post by presence1960 on 2010-03-02
I would open a terminal and run ```
sudo update-grub
```

I would then power down and check those connections as everything looks OK. the only concern I had was with the root (hd0,1) in grub.cfg- but running sudo update-grub should take care of that. 

It doesn't look like a software/GRUB issue but rather a hardware issue. I would check those connections as that can be a reason why your 80 GB (sda) went offline.

---

### Post by plucky on 2010-03-02
The 80Gb drive is the one that went missing and I assume it is the first one inside your system.It also has your /home partition.

You are actually booting off the HD1 drive,which is the 37Gb drive.Check your Bios is set to boot off HD1 and not HD0.

The external drive is /dev/sdc and is formatted as Fat32 and holds your music collection.

The Problem was that the 80Gb drive went missing and the 37Gb drive became the /dev/sda drive and I assume the external drive then became the /dev/sdb drive.Your Bios is set to boot from the second drive and as your external drive cannot be booted,it would fail.

What you need to find out is why the 80Gb drive went missing.It could be that it is on the way out and about to fail, or it could also be a loose connection or power lead on the drive.

I would seriously consider backing up the data on it in case it fails.

If it happens again,change your Bios to boot from HD0 and see if that works.But remember,without the 80Gb drive,you will have no /home partition.

Good Luck

---

### Post by robine on 2010-03-07
Hi Presence1960 & Plucky! My apologies for my extended absence. I've been away for a few days. I came home to my computer having the same problem as before. It won't boot normally and the 80 gb drive is again not being "seen". I've tried multiple times to boot to no avail. I'm online now with the (wonderful) live CD.

Plucky: At last, here is the output from "sudo fdisk -l". How do I check the BIOS to see if I can see both drives? (Sorry if that's a dumb question, but I'm very new to this.)
```
Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xadece77e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2432    19535008+  83  Linux
/dev/sda2            2433        4500    16611210    5  Extended
/dev/sda5            2433        4500    16611178+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x481225b1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30516   245117344+   b  W95 FAT32
```Presence1960: I will try changing UUID numbers as you suggested.

I think that, if all else fails, I may have to reinstall Karmic completely. This will be challenging as I have no experience doing this at all. But I will try your ideas first.

---

### Post by robine on 2010-03-07
> **plucky said:**
> The 80Gb drive is the one that went missing and I assume it is the first one inside your system.It also has your /home partition.

You are actually booting off the HD1 drive,which is the 37Gb drive.Check your Bios is set to boot off HD1 and not HD0.

The external drive is /dev/sdc and is formatted as Fat32 and holds your music collection.

The Problem was that the 80Gb drive went missing and the 37Gb drive became the /dev/sda drive and I assume the external drive then became the /dev/sdb drive.Your Bios is set to boot from the second drive and as your external drive cannot be booted,it would fail.

What you need to find out is why the 80Gb drive went missing.It could be that it is on the way out and about to fail, or it could also be a loose connection or power lead on the drive.

I would seriously consider backing up the data on it in case it fails.

If it happens again,change your Bios to boot from HD0 and see if that works.But remember,without the 80Gb drive,you will have no /home partition.

Good Luck

Thanks also for the advice. I did quickly back up a few things a few days ago, but not everything. If I have to lose a few files and photos, though, it's not a big deal. I just want my computer to function properly :|

---

### Post by robine on 2010-03-07
Here is the results.txt file from today (just in case something has changed... which it shouldn't, but who knows?). It looks the same to me as before:

```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  BSD4.4: Fat32
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 37.0 GB, 37019566080 bytes
255 heads, 63 sectors/track, 4500 cylinders, total 72303840 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xadece77e

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    39,070,079    39,070,017  83 Linux
/dev/sda2          39,070,080    72,292,499    33,222,420   5 Extended
/dev/sda5          39,070,143    72,292,499    33,222,357  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders, total 490234752 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x481225b1

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   490,234,751   490,234,689   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        bea739ac-dc3a-4af4-ba1b-9430e11d5158   ext3                                     
/dev/sda5        760878d8-6c0f-4841-9b96-3c80672605e1   swap                                     
/dev/sdb1        71AB-1F06                              vfat       EXTERNAL HD                   

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)
/dev/sdb1        /media/EXTERNAL HD       vfat       (rw,nosuid,nodev,uhelper=devkit,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,flush)


=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
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
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
menuentry "Ubuntu, Linux 2.6.31-16-generic-pae (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set bea739ac-dc3a-4af4-ba1b-9430e11d5158
    linux    /boot/vmlinuz-2.6.31-16-generic-pae root=UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic-pae
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
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

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb1 during installation
UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 /               ext3    errors=remount-ro 0       1
# /home was on /dev/sda1 during installation
UUID=a31097ec-c78d-47b0-9cf0-2cfcd5aff759 /home           ext3    defaults        0       2
# swap was on /dev/sdb5 during installation
UUID=760878d8-6c0f-4841-9b96-3c80672605e1 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .5GB: boot/grub/core.img
    .5GB: boot/grub/grub.cfg
    .5GB: boot/initrd.img-2.6.31-16-generic-pae
    .6GB: boot/vmlinuz-2.6.31-16-generic-pae
    .5GB: initrd.img
    .6GB: vmlinuz
```

---

### Post by egalvan on 2010-03-07
> **robine said:**
> 
I can't imagine why one of my hard disks would suddenly disappear.
 After a few more reboots, suddenly "grub loading..." was displayed (this had not been the case so far while having this problem).
 And then, my desktop and all settings were restored.

see below for the reason the drive designations changed...

> [B]The difference was this: I have an external hard drive that I use for storing music.
 This has its own power switch and turns on separately from my desktop.
 When I [COLOR="Red"]switched it on before the desktop,[/COLOR] nothing happened - still had the issue.
 But when I [COLOR="Red"]switched it on just after switching on the desktop power[/COLOR], suddenly everything was restored. [/B]

When your **external** drive is switched on early enough in the boot process, Linux sees it and designates it in one order...
when your **external** drive is switched on later in the boot process, Linux sees it in a different order, and now has a different designation.


> **I didn't remove or switch any hard drives - why would one suddenly stop being seen?**

Yes you did :), switching on the **external** drive at different times causes this.

Clues to this can be seen here...

**Grub 2 is installed in the MBR of [COLOR="Red"]/dev/sda[/COLOR] and looks on the same drive in partition #1 for /boot/grub.**

and here...

[B]# [COLOR="Red"]/ was on /dev/sdb1 during installation[/COLOR]
UUID=bea739ac-dc3a-4af4-ba1b-9430e11d5158 / ext3 errors=remount=ro 0 1
# [COLOR="Red"]/home was on /dev/sda1 during installation[/COLOR]
UUID=a31097ec-c78d-4760-9cf0-2cfcd5aff759 /home ext3 defaults 0 2
# [COLOR="Red"]swap was on /dev/sdb5 during installation[/COLOR]
UUID=760878d8-6c0f-4841-9b96-3c80672605e1 none swap sw 0 0[/B]


Now, having said all this, I must point out that **UUID** is designed to reduce just this kind of problem...

quote

[B] /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; [COLOR="Red"]this may be used with UUID= as a more robust way to name[/COLOR]
# [COLOR="Red"]devices that works even if disks are added and removed. See fstab(5)[/COLOR][/B]


Of course, this will fail if the drive is not present at the time it is needed in the boot process...

And your VFAT drive (which is the external one, I believe) has this further problem...

> [B]According to the info in the boot sector,
 sdb1 starts 
                       at sector 0. But according to the info from fdisk,
 
                       sdb1 starts at sector 63.
[/B]



So there are problems that require further study.

---

### Post by egalvan on 2010-03-07
Switch on the external drive such that you can boot the system and all drives are present...

go to a terminal

```
sudo blkid
```

paste the results here, please.

thank you.

---

### Post by robine on 2010-03-07
> **egalvan said:**
> Switch on the external drive such that you can boot the system and all drives are present...

go to a terminal
```
sudo blkid
```paste the results here, please.
thank you.

Thanks for your advice and coming to my rescue. :) I am actually unable to boot the system normally at all. No matter in what order I switch on the external hard drive (relative to switching on the desktop's power), I cannot boot normally. Right now I'm using the 9.10 live CD in order to seek help.

So, here are the results of "sudo blkid":

```
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="bea739ac-dc3a-4af4-ba1b-9430e11d5158" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="760878d8-6c0f-4841-9b96-3c80672605e1" TYPE="swap" 
/dev/sdb1: LABEL="EXTERNAL HD" UUID="71AB-1F06" TYPE="vfat" 

```

---

### Post by robine on 2010-03-08
> **presence1960 said:**
> It looks like you removed the disk that was formerly sda which had your /home partition. Now the former sdb becomes sda. If you removed the former sda follow this. if you did not remove a hard disk then you have other problems.

To accomplish the above I would boot from the ubuntu Live CD & choose "try ubuntu without any changes". When the desktop loads go Places > Computer to open a file browser. On the left pane highlight your sda1 (ubuntu / partition) to mount it. You will know it is mounted when you see directories to right.

Now open a terminal and run ```
gksu nautilus
```This will open a file browser with root priviledge. Again on the left pane highlight the sda1 partition. Now navigate to /etc and open the fstab file. Make the changes noted above. Click Save on toolbar & close file. Close both file browsers and reboot without the live cd. See what happens.

I booted from the live CD and followed your exact instructions.

When I get to /etc, I can't find the fstab file. There doesn't seem to BE one. :|

Should I just reinstall Karmic completely? And if so, should I try to save the existing partitions, or just wipe it all and start anew?

---

