---
title: "Omg!! Help lost grub!"
date: 2010-01-19
forum: New to Ubuntu
---

### Post by appoloin on 2010-01-19
PLEASE PLEASE HELP ME!!!!

I have duel boot Ubuntu and Vista setup perfctly well but Vista start playing up so i re-install Vista.

How i setup my duelboot is 2 HDD i formatted Vista Hdd all went well but now when i reboot it goes directly to Vista it does not give me the optionon what i want to load anymore

PLEASE SOMEONE HELP ME!! My entire exam thesis is in UBUNTU!! :(

---

### Post by inobe on 2010-01-19
for now you can use a live cd to mount the linux drive and get your file, simply load the live cd and hit places, select the disk containing ubuntu, browse to the directory, drag the file on a thumb drive.

i am sure someone will be along to help you fix grub.

---

### Post by appoloin on 2010-01-19
Ok trying that Thank you!!..

Hope someone here can help me fix the dual boot again PLEASE PLEASE PLEASE!!

---

### Post by SumTingWong on 2010-01-19
Check your PMs.

---

### Post by inobe on 2010-01-19
i rarely dual boot' so the best i can do is google for you

[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

---

### Post by appoloin on 2010-01-19
thank you .. i done that.. but Can anyone help me fix GRUP? i dont really want to reformat again

---

### Post by r_s on 2010-01-19
I think windows overwrites your grub file , so you need to reinstall your grub.

---

### Post by SumTingWong on 2010-01-19
> **appoloin said:**
> thank you .. i done that.. but Can anyone help me fix GRUP? i dont really want to reformat again

Am I invisible? I offered to help you and seem to be being ignored.

---

### Post by appoloin on 2010-01-19
i have sent u a msg sum pls check ur pm

---

### Post by matamoscas on 2010-01-19
I have done this before.

What I am about to say, you probably already know, but I will say it anyway.

Windows rebuilds the MBR (master boot record) when it is installed. That is why is is generally recommended that you install Windows before Linux, so that GRUB can re-write it, recognizing Windows is already installed -- and sharing the system with it.

Unfortunately, if you re-install Windows, it will AGAIN re-write the MBR, so that it can reign supreme, and not recognize any other bootable systems.

It was a major pain for me to get it back, such that I cannot offer much advice, I just winged it, and got it to work.

From the experience, I learned never to do that =) I will likely install Windows 7, in the near future, and have been planning for this eventuality =(

There are a few thread in the ubuntu forums that will tell you how to do it, but unfortunately, it is not an easy, 1, 2, 3 step process. Well, it is, but depending on your technical savvy, it might seem archaic.

All this said, there are essentially two ways to do it, from what I remember.

1. Involves booting from Ubuntu DVD, and starting the install, and going up to (Don't do this!, just for general expecation setting) around where it says to format your drives.  Then, you quit the installer around there, BUT DO NOT FORMAT YOUR DRIVES.  Follow the instructions that you find that are more precise.

2. the other method involves dropping into a shell, and manually setting up GRUB. Not too hard (if I could do it), but I wouldn't say it was super easy for me, the first time I did it. 

Those are the two ways, generally, but you'll need to find precise information going forward, to get your GRUB back.

Sorry I cannot be of more help.

---

### Post by SumTingWong on 2010-01-19
I thought of one more thing.

On LiveCD.

In Terminal;
```

[COLOR=Red]**sudo grub**[/COLOR]

**[COLOR=Red]root (hd0,1)[/COLOR]** (also try) **[COLOR=Red]root (hd0,2)[/COLOR]**

[COLOR=Red]**setup (hd0)**[/COLOR]

Then **[COLOR=Red]quit[/COLOR]** (or exit whichever works)

```

If that doesn't work then you need someone more experienced with GRUB 2. Like I said, I've only ever done that on GRUB 1.

Good luck.

---

### Post by presence1960 on 2010-01-19
> **appoloin said:**
> PLEASE PLEASE HELP ME!!!!

I have duel boot Ubuntu and Vista setup perfctly well but Vista start playing up so i re-install Vista.

How i setup my duelboot is 2 HDD i formatted Vista Hdd all went well but now when i reboot it goes directly to Vista it does not give me the optionon what i want to load anymore

PLEASE SOMEONE HELP ME!! My entire exam thesis is in UBUNTU!! :(

Cut to the chase. I need way more info than you have provided. Do the following and I will give you precise, detailed instructions to restore your GRUB.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by presence1960 on 2010-01-19
> **SumTingWong said:**
> I thought of one more thing.

On LiveCD.

In Terminal;
```

[COLOR=Red]**sudo grub**[/COLOR]

**[COLOR=Red]root (hd0,1)[/COLOR]** (also try) **[COLOR=Red]root (hd0,2)[/COLOR]**

[COLOR=Red]**setup (hd0)**[/COLOR]

Then **[COLOR=Red]quit[/COLOR]** (or exit whichever works)

```

If that doesn't work then you need someone more experienced with GRUB 2. Like I said, I've only ever done that on GRUB 1.

Good luck.

It does not help to guess, if you read the OP original post he has 2 hard disks- one with Ubuntu and the other with windows. 

Start using the boot info script which will give you a plethora of information about the setup and boot process of a computer. It is a highly useful tool for trouble shooting setup & boot problems. here is mine so you can see what info it gives:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.
 => Testdisk is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   130,030,109   130,030,047   5 Extended
/dev/sda5                 126     8,385,929     8,385,804  82 Linux swap / Solaris
/dev/sda6           8,385,993    50,331,644    41,945,652  83 Linux
/dev/sda7          50,331,708    92,277,359    41,945,652  83 Linux
/dev/sda8          92,277,423   130,030,109    37,752,687  83 Linux
/dev/sda2         130,031,616   203,896,831    73,865,216   7 HPFS/NTFS
/dev/sda3         203,896,980   976,768,064   772,871,085  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02020202

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   104,855,551   104,853,504   7 HPFS/NTFS
/dev/sdc2         104,856,255   312,578,583   207,722,329   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda5: UUID="63538de2-1cc9-4451-ab42-5f8712695c89" TYPE="swap" 
sda6: LABEL="karmic" UUID="e0b415e6-168b-49e7-b62b-0fc42c83a6d7" TYPE="ext4" 
sda7: UUID="2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef" TYPE="ext4" 
sda8: LABEL="sabayon" UUID="6d4ef10b-0252-44b1-aeaf-5730ff73bd99" TYPE="ext4" 
sda2: UUID="280C57B90C5780AC" LABEL="win-backup" TYPE="ntfs" 
sda3: LABEL="backup" UUID="b37b51c7-cc17-4401-a66c-4d43193d508a" SEC_TYPE="ext2" TYPE="ext3" 
sdb1: LABEL="data" UUID="8f5b8ecd-2930-46a1-8256-88235c860965" TYPE="ext3" 
sdc1: UUID="1086EDD986EDBEFA" LABEL="vista" TYPE="ntfs" 
sdc2: UUID="42D35EE6525751C9" LABEL="win_data" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raz)
/dev/sdb1 on /media/data type ext3 (rw,nosuid,nodev,uhelper=devkit)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
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
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-10-generic (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro quiet splash
	initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro single
	initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 1086edd986edbefa
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/core.img
   4.2GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-17-generic
   4.2GB: boot/initrd.img-2.6.31-18-generic
   4.2GB: boot/vmlinuz-2.6.31-17-generic
   4.2GB: boot/vmlinuz-2.6.31-18-generic
   4.2GB: initrd.img
   4.2GB: initrd.img.old
   4.2GB: vmlinuz
   4.2GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
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
set locale_dir=/boot/grub/locale
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-10-generic" {
        recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro single 
	initrd	/boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-18-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 1086edd986edbefa
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  25.7GB: boot/grub/core.img
  25.7GB: boot/grub/grub.cfg
  25.7GB: boot/initrd.img-2.6.32-10-generic
  25.7GB: boot/vmlinuz-2.6.32-10-generic
  25.7GB: initrd.img
  25.7GB: vmlinuz

========================== sda8/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,7)
#          kernel /boot/kernel-genkernel real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99
#          initrd /boot/initramfs-genkernel
#boot=sda8
default=0
timeout=5
splashimage=(hd0,7)/boot/grub/splash.xpm.gz

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon)
	root (hd0,7)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode)
	root (hd0,7)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Other Operating System - Microsoft Windows
	rootnoverify (hd0,0)
	chainloader +1
	savedefaulttitle Other Operating System - Microsoft Windows
	rootnoverify (hd2,0)
	chainloader +1
	savedefaulttitle Other Operating System - Microsoft Windows
	rootnoverify (hd0,1)
	chainloader +1
	savedefault
### Other detected distributions
title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro quiet splash
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic


=============================== sda8/etc/fstab: ===============================

UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 swap                    swap    defaults        0 0

=================== sda8: Location of files loaded by Grub: ===================


  47.2GB: boot/grub/grub.conf
  47.2GB: boot/grub/menu.lst
  47.2GB: boot/grub/stage2
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```

AS you can see it gives a lot of info. I have Ubuntu 10.04 alpha2, Ubuntu 9.10, Sabayon 4.1 & windows Vista currently on my machine.

---

### Post by SumTingWong on 2010-01-19
> **presence1960 said:**
> It does not help to guess, if you read the OP original post he has 2 hard disks- one with Ubuntu and the other with windows. 

Start using the boot info script which will give you a plethora of information about the setup and boot process of a computer. It is a highly useful tool for trouble shooting setup & boot problems. here is mine so you can see what info it gives:

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub.
 => Testdisk is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   130,030,109   130,030,047   5 Extended
/dev/sda5                 126     8,385,929     8,385,804  82 Linux swap / Solaris
/dev/sda6           8,385,993    50,331,644    41,945,652  83 Linux
/dev/sda7          50,331,708    92,277,359    41,945,652  83 Linux
/dev/sda8          92,277,423   130,030,109    37,752,687  83 Linux
/dev/sda2         130,031,616   203,896,831    73,865,216   7 HPFS/NTFS
/dev/sda3         203,896,980   976,768,064   772,871,085  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   488,392,064   488,392,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02020202

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   104,855,551   104,853,504   7 HPFS/NTFS
/dev/sdc2         104,856,255   312,578,583   207,722,329   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda5: UUID="63538de2-1cc9-4451-ab42-5f8712695c89" TYPE="swap" 
sda6: LABEL="karmic" UUID="e0b415e6-168b-49e7-b62b-0fc42c83a6d7" TYPE="ext4" 
sda7: UUID="2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef" TYPE="ext4" 
sda8: LABEL="sabayon" UUID="6d4ef10b-0252-44b1-aeaf-5730ff73bd99" TYPE="ext4" 
sda2: UUID="280C57B90C5780AC" LABEL="win-backup" TYPE="ntfs" 
sda3: LABEL="backup" UUID="b37b51c7-cc17-4401-a66c-4d43193d508a" SEC_TYPE="ext2" TYPE="ext3" 
sdb1: LABEL="data" UUID="8f5b8ecd-2930-46a1-8256-88235c860965" TYPE="ext3" 
sdc1: UUID="1086EDD986EDBEFA" LABEL="vista" TYPE="ntfs" 
sdc2: UUID="42D35EE6525751C9" LABEL="win_data" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raz)
/dev/sdb1 on /media/data type ext3 (rw,nosuid,nodev,uhelper=devkit)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
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
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
    initrd    /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
    linux    /boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
    initrd    /boot/initrd.img-2.6.31-17-generic
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
menuentry "Ubuntu, with Linux 2.6.32-10-generic (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
    linux /boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro quiet splash
    initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode) (on /dev/sda7)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
    linux /boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro single
    initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
    linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
    initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
    linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
    initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 1086edd986edbefa
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/core.img
   4.2GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-17-generic
   4.2GB: boot/initrd.img-2.6.31-18-generic
   4.2GB: boot/vmlinuz-2.6.31-17-generic
   4.2GB: boot/vmlinuz-2.6.31-18-generic
   4.2GB: initrd.img
   4.2GB: initrd.img.old
   4.2GB: vmlinuz
   4.2GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
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
set locale_dir=/boot/grub/locale
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-10-generic" {
        recordfail
    set quiet=1
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
    linux    /boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode)" {
        recordfail
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
    linux    /boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro single 
    initrd    /boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root=(hd0,7)
    search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-18-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
    linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
    initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
    linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
    initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda6)" {
    insmod ext2
    set root=(hd0,6)
    search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
    linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
    initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
    linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
    initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sda8)" {
    insmod ext2
    set root=(hd0,8)
    search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
    linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
    initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
    insmod ntfs
    set root=(hd2,1)
    search --no-floppy --fs-uuid --set 1086edd986edbefa
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  25.7GB: boot/grub/core.img
  25.7GB: boot/grub/grub.cfg
  25.7GB: boot/initrd.img-2.6.32-10-generic
  25.7GB: boot/vmlinuz-2.6.32-10-generic
  25.7GB: initrd.img
  25.7GB: vmlinuz

========================== sda8/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,7)
#          kernel /boot/kernel-genkernel real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99
#          initrd /boot/initramfs-genkernel
#boot=sda8
default=0
timeout=5
splashimage=(hd0,7)/boot/grub/splash.xpm.gz

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon)
    root (hd0,7)
    kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
    initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
    savedefault

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode)
    root (hd0,7)
    kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
    initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
    savedefault

title Other Operating System - Microsoft Windows
    rootnoverify (hd0,0)
    chainloader +1
    savedefaulttitle Other Operating System - Microsoft Windows
    rootnoverify (hd2,0)
    chainloader +1
    savedefaulttitle Other Operating System - Microsoft Windows
    rootnoverify (hd0,1)
    chainloader +1
    savedefault
### Other detected distributions
title        Ubuntu 9.04, kernel 2.6.28-17-generic
uuid        236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro quiet splash
initrd        /boot/initrd.img-2.6.28-17-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid        236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel        /boot/vmlinuz-2.6.28-17-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro  single
initrd        /boot/initrd.img-2.6.28-17-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic


=============================== sda8/etc/fstab: ===============================

UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 swap                    swap    defaults        0 0

=================== sda8: Location of files loaded by Grub: ===================


  47.2GB: boot/grub/grub.conf
  47.2GB: boot/grub/menu.lst
  47.2GB: boot/grub/stage2
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 
```AS you can see it gives a lot of info. I have Ubuntu 10.04 alpha2, Ubuntu 9.10, Sabayon 4.1 & windows Vista currently on my machine.

Cool story bro. 

I haven't had to fix GRUB in AGES, and his disk gets weirdly mounted. You obviously know more than me, so hook the brother up with a fix =P

---

### Post by presence1960 on 2010-01-19
> **SumTingWong said:**
> Cool story bro. 

I haven't had to fix GRUB in AGES, and his disk gets weirdly mounted. You obviously know more than me, so hook the brother up with a fix =P

it is not about who knows more, it is about sharing knowledge/experience. I am sure you know your machine's setup, so run the boot info script and review the RESULTS.txt file so you can gain a deeper insight into that setup and the relationships of the devices & bootloader(s).

If you need help interpreting the info I will be glad to help.

---

### Post by SumTingWong on 2010-01-19
> **presence1960 said:**
> it is not about who knows more, it is about sharing knowledge/experience. I am sure you know your machine's setup, so run the boot info script and review the RESULTS.txt file so you can gain a deeper insight into that setup and the relationships of the devices & bootloader(s).

If you need help interpreting the info I will be glad to help.

But you obviously do know more! I wasn't being sarcastic {Q_Q} 

And thanks, I didn't know about that script thing. (Y)

---

### Post by presence1960 on 2010-01-19
> **SumTingWong said:**
> But you obviously do know more! I wasn't being sarcastic {Q_Q} 

And thanks, I didn't know about that script thing. (Y)

I didn't think you were being sarcastic. I try to help others as I have been helped in here. I have learned some and that is because people in here shared their knowledge.

---

### Post by SumTingWong on 2010-01-19
> **presence1960 said:**
> I didn't think you were being sarcastic. I try to help others as I have been helped in here. I have learned some and that is because people in here shared their knowledge.

Sweet. As long as you understood what I meant :)

---

### Post by CSdavid on 2010-01-19
my advice is to get rid of Vista and install Windows XP and if your processor can handle it maybe windows 7.  I am not sure how I feel about windows 7 because I haven't used it.  But some of my computer science professors say its okay and that its better than Vista, but most of them used Mac and they have a PC that dual boots with XP and some form of Linux (usually redhat).

---

### Post by presence1960 on 2010-01-19
> **CSdavid said:**
> my advice is to get rid of Vista and install Windows XP and if your processor can handle it maybe windows 7.  I am not sure how I feel about windows 7 because I haven't used it.  But some of my computer science professors say its okay and that its better than Vista, but most of them used Mac and they have a PC that dual boots with XP and some form of Linux (usually redhat).

What if the OP does not have a valid copy of XP or Windows 7? What you are proposing does absolutely nothing to help solve the OP's problem which is that GRUB was overwritten in the MBR by Windows. Even if the Op does have those and installs another windows version his/her Ubuntu still will not boot because windows will still be on the MBR. Try to think things through before responding or if unsure don't say anything but rather ask a question.

---

### Post by presence1960 on 2010-01-19
> **CSdavid said:**
> I have thought things through. <snip>   Vista has problems with running dual boot with linux.  I know a lot a of people with the same problems that couldnt figure it out.   All i was saying was start fresh at that point.   I know the paper was on the hard drive and i hope he figures out how to get it back.

this is why we back up information.
 Are you suggesting using pirated software? Well if you are that does matter on here as the community has nor wants anything to do with pirated software. Only a fool would use pirated software because almost in every instance of such software malware has been embedded into it.

Vista dual boots fine with linux if you know what you  are doing or if you don't know what you are doing if you can follow directions.

Besides your solution is way off the mark. The OP can't boot Ubuntu because Vista was reinstalled which overwrote GRUB on the MBR and now the machine boots directly to windows. It has nothing to do with Vista. Once GRUB is restored to MBR both Vista & Ubuntu will boot again.

---

### Post by SirBismuth on 2010-01-20
I have used SuperGRUB to fix a Grub1 installation I broke, but as I don't dual-boot at home anymore, and will also change to a single-boot setup at work after 10.04 is released, not sure if it works with Grub2.

Here is the link for SuperGRUB disk: [Linky]("http://www.supergrubdisk.org/")

B

---

### Post by presence1960 on 2010-01-20
> **CSdavid said:**
> I really dont care,  my solution wasnt bad  a full reinstall would work, but not to get the files off.   Personally i dont really care.  I am not suggesting that he pirate the software, i buy all my software or I get it legally through the school.   If your solution works then I am glad.  My solution would fix the computer too.      

I am done with this conversation   like i said if you solution works then im happy for the person.

If you really don't care then you should not post anything on here because it is not your machine that will suffer the consequences of your misinformed suggestions. Most of us on here do care, that is why we spend our own free time trying to help those who want to use & learn linux. Maybe you would be better served by joining a windows community.

You have a lot to learn about linux & dual booting with windows. Your solution will put a different windows version on the computer but still leave linux unable to boot. The problem is not linux or windows but the fact that when the OP reinstalled Vista the GRUB bootloader on the MBR was overwritten by windows. Without GRUB there will be no menu to choose whether to boot windows or ubuntu. Sheeesh some people are thick!

---

### Post by a2z on 2010-01-20
ugh! after all this reading, I still have a missing grub!! With no solution.

---

### Post by CSdavid on 2010-01-20
I wanted to apologize to the person who made this post.   I did google a little bit and my have found a recovery option.   I have not had a chance to read the whole thing but I think if might help


[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by CSdavid on 2010-01-20
I found another website,  this one was designed for Windows XP,  but I believe it might work for Vista to.

If someone else would like to check this site out and decide whether or not it will work.

[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

i believe this is easier than the last website i posted.

---

### Post by Sef on 2010-01-20
Appoloin:

What version of Ubuntu do you have?   If it is karmic, then did you upgrade from Jaunty, or did you do a clean install?

Note: Karmic used GRUB 2 except when it was upgraded from Jaunty, then if upgrade it and all previous Ubuntu versions use GRUB 1.

---

### Post by presence1960 on 2010-01-20
> **CSdavid said:**
> I wanted to apologize to the person who made this post.   I did google a little bit and my have found a recovery option.   I have not had a chance to read the whole thing but I think if might help


[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

**_*Helloooooo!!!!*_** that is what I have been saying all along. All that needs to be done is to restore GRUB. The boot info script I asked to be run and post the results back here will give me the info to give appolin the exact commands to run to restore GRUB!!!

Plus the boot info script results will show the answers to all the other questions such as what version of ubuntu, what GRUB, etc.

CSdavid for your info here is my results of the boot info script since appolin (OP) has not returned for a while. If you take a look at it you will see it shows your bootloader(s) which type and installed where, all disks and partition tables, UUID & label of every partition(device) and much more. This is a very useful tool for troubleshooting setup & boot problems. Especially since experience does show that a lot of times what people say they have on their machine and what they actually have are not the same. Take a chance and learn something for yourself not me, run the boot info script on your machine and study the results. It will shed light on your setup of devices and their relationship to the boot process. If you need help interpreting the info I would gladly help.

```
============================= Boot Info Summary: ==============================

 => Grub 1.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #7 for /boot/grub.
 => Testdisk is installed in the MBR of /dev/sdb
 => Windows is installed in the MBR of /dev/sdc
sda1: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu lucid (development 
                       branch)
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda8: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:   This is .()
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.conf /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sdc2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x05f07bc0

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   130,030,109   130,030,047   5 Extended
/dev/sda5                 126     8,385,929     8,385,804  82 Linux swap / Solaris
/dev/sda6           8,385,993    50,331,644    41,945,652  83 Linux
/dev/sda7          50,331,708    92,277,359    41,945,652  83 Linux
/dev/sda8          92,277,423   130,030,109    37,752,687  83 Linux
/dev/sda2         130,031,616   203,896,831    73,865,216   7 HPFS/NTFS
/dev/sda3         203,896,980   976,768,064   772,871,085  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000a49f9

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   488,392,064   488,392,002  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x02020202

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *          2,048   104,854,377   104,852,330   7 HPFS/NTFS
/dev/sdc2         104,856,255   312,578,583   207,722,329   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda5: UUID="63538de2-1cc9-4451-ab42-5f8712695c89" TYPE="swap" 
sda6: LABEL="karmic" UUID="e0b415e6-168b-49e7-b62b-0fc42c83a6d7" TYPE="ext4" 
sda7: LABEL="lucid" UUID="2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef" TYPE="ext4" 
sda8: LABEL="sabayon" UUID="6d4ef10b-0252-44b1-aeaf-5730ff73bd99" TYPE="ext4" 
sda2: UUID="280C57B90C5780AC" LABEL="win-backup" TYPE="ntfs" 
sda3: LABEL="backup" UUID="b37b51c7-cc17-4401-a66c-4d43193d508a" SEC_TYPE="ext2" TYPE="ext3" 
sdb1: LABEL="data" UUID="8f5b8ecd-2930-46a1-8256-88235c860965" TYPE="ext3" 
sdc1: UUID="1086EDD986EDBEFA" LABEL="vista" TYPE="ntfs" 
sdc2: UUID="42D35EE6525751C9" LABEL="win_data" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda7 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/raz/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=raz)
/dev/sdb1 on /media/data type ext3 (rw,nosuid,nodev,uhelper=devkit)


=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
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
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet  quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd	/boot/initrd.img-2.6.31-17-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, with Linux 2.6.32-10-generic (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro quiet splash
	initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode) (on /dev/sda7)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux /boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro single
	initrd /boot/initrd.img-2.6.32-10-generic
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 1086edd986edbefa
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0

=================== sda6: Location of files loaded by Grub: ===================


   4.2GB: boot/grub/core.img
   4.2GB: boot/grub/grub.cfg
   4.2GB: boot/initrd.img-2.6.31-17-generic
   4.2GB: boot/initrd.img-2.6.31-18-generic
   4.2GB: boot/vmlinuz-2.6.31-17-generic
   4.2GB: boot/vmlinuz-2.6.31-18-generic
   4.2GB: initrd.img
   4.2GB: initrd.img.old
   4.2GB: vmlinuz
   4.2GB: vmlinuz.old

=========================== sda7/boot/grub/grub.cfg: ===========================

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
set root=(hd0,7)
search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
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
set locale_dir=/boot/grub/locale
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
set menu_color_highlight=black/white
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, with Linux 2.6.32-10-generic" {
        recordfail
	set quiet=1
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-10-generic
}
menuentry "Ubuntu, with Linux 2.6.32-10-generic (recovery mode)" {
        recordfail
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux	/boot/vmlinuz-2.6.32-10-generic root=UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef ro single 
	initrd	/boot/initrd.img-2.6.32-10-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root=(hd0,7)
	search --no-floppy --fs-uuid --set 2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu, Linux 2.6.31-18-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-18-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro splash quiet quiet splash
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode) (on /dev/sda6)" {
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set e0b415e6-168b-49e7-b62b-0fc42c83a6d7
	linux /boot/vmlinuz-2.6.31-17-generic root=UUID=e0b415e6-168b-49e7-b62b-0fc42c83a6d7 ro single splash quiet
	initrd /boot/initrd.img-2.6.31-17-generic
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode) (on /dev/sda8)" {
	insmod ext2
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 6d4ef10b-0252-44b1-aeaf-5730ff73bd99
	linux /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
}
menuentry "Windows Vista (loader) (on /dev/sdc1)" {
	insmod ntfs
	set root=(hd2,1)
	search --no-floppy --fs-uuid --set 1086edd986edbefa
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda7/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=2e8ec50d-7a26-4d49-82b6-2dc641f7d2ef /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda7: Location of files loaded by Grub: ===================


  25.7GB: boot/grub/core.img
  25.7GB: boot/grub/grub.cfg
  25.7GB: boot/initrd.img-2.6.32-10-generic
  25.7GB: boot/vmlinuz-2.6.32-10-generic
  25.7GB: initrd.img
  25.7GB: vmlinuz

========================== sda8/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You do not have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /, eg.
#          root (hd0,7)
#          kernel /boot/kernel-genkernel real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99
#          initrd /boot/initramfs-genkernel
#boot=sda8
default=0
timeout=5
splashimage=(hd0,7)/boot/grub/splash.xpm.gz

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon)
	root (hd0,7)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon  root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 CONSOLE=/dev/tty1 quiet resume=swap:/dev/sda5
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Sabayon Linux x86-64 (genkernel-x86_64-2.6.29-sabayon) (safe mode)
	root (hd0,7)
	kernel /boot/kernel-genkernel-x86_64-2.6.29-sabayon root=/dev/ram0 ramdisk=8192 real_root=UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 dolvm init=/linuxrc CONSOLE=/dev/tty1 resume=swap:/dev/sda5 nox acpi=off ide=nodma vga=normal
	initrd /boot/initramfs-genkernel-x86_64-2.6.29-sabayon
	savedefault

title Other Operating System - Microsoft Windows
	rootnoverify (hd0,0)
	chainloader +1
	savedefaulttitle Other Operating System - Microsoft Windows
	rootnoverify (hd2,0)
	chainloader +1
	savedefaulttitle Other Operating System - Microsoft Windows
	rootnoverify (hd0,1)
	chainloader +1
	savedefault
### Other detected distributions
title		Ubuntu 9.04, kernel 2.6.28-17-generic
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro quiet splash
initrd		/boot/initrd.img-2.6.28-17-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-17-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro quiet splash
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		236c5365-8de4-4ddf-abd2-9e5aa9d6e323
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=236c5365-8de4-4ddf-abd2-9e5aa9d6e323 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic


=============================== sda8/etc/fstab: ===============================

UUID=6d4ef10b-0252-44b1-aeaf-5730ff73bd99 /                       ext4    user_xattr,noatime 1 1
/dev/shm                /dev/shm                tmpfs   defaults        0 0
UUID=63538de2-1cc9-4451-ab42-5f8712695c89 swap                    swap    defaults        0 0

=================== sda8: Location of files loaded by Grub: ===================


  47.2GB: boot/grub/grub.conf
  47.2GB: boot/grub/menu.lst
  47.2GB: boot/grub/stage2
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg
```

---

### Post by QuimNuss on 2010-01-20
Hello appolloin, a2z and other people losing grub,

I've done what you ask several times last week with a windows xp installation, I believe it doesn't make any real difference so here's what I did.

Anyway, if your first concern is recovering the thesis, use a LiveCD and save it in you windows installation or an external hard drive.

Prior notice:
I am assuming you have a karmic install and a karmic LiveCD and that you know how to boot from CD. I may be assuming more things (that's why everybody was asking more information), so I suggest you back up your files with your liveCD to an external USB hard drive as an habit when you mess with the system. Btw, you need root privileges to do so, so either you start every command with 'sudo' or make a 'sudo su' at the beginning.

Given that you have two hard drives, you must know which one the bios boots from, this is usually displayed on the bios setup at startup. Probably it will be the one with Vista on it, but I'm guessing... on the grub installation step you'll have to know if either is sda, hada, sdb or hdb. If you're unsure ask again about how to display the BIOS information. (that'll pressing F2 or F12 or a combination of keys on startup)

Here it goes:

1. First, locate grub!

```
# fdisk -l
```

to get the Linux partitions. (Labeled "Linux") Note the partition name; /dev/sda**X** or /dev/hda**X**

1.1 Now Mount that partition
```
# mkdir /media/root
# mount /dev/sda**X** /media/root
```
Replacing X with the partition name (hdaX for non-SATA disks). You can check it doing

    ```
ls /media/root/boot
```
with a listing of the kernels and the grub folder

2. Re-install grub!

Run
```
# grub-install --root-directory=/media/root /dev/sda
```
Notice that its sda (o hda) without any number (it points to the Master Boot Record)

3. Refresh grub

```
# update-grub
```

Reboot.

When you reinstall windows, the MBR get erased by the Windows boot loader, you just have to replace it with the GRUB from your linux installation as explained above. Mainly its taken from a tutorial somebody may have already pointed you to, but assuming some stuff, so be careful.

Hope it helps...!

---

### Post by kansasnoob on 2010-01-20
> **presence1960 said:**
> **_*Helloooooo!!!!*_** that is what I have been saying all along. All that needs to be done is to restore GRUB. The boot info script I asked to be run and post the results back here will give me the info to give appolin the exact commands to run to restore GRUB!!!

Plus the boot info script results will show the answers to all the other questions such as what version of ubuntu, what GRUB, etc.

+1! Just provide the output of the Boot Info Script.

Then we know what you have and we can figure out what steps are needed to fix it.

It's usually very simple, but just trying this and that without knowing is reckless and often creates problems rather than solving them.

---

### Post by blingenfelter on 2010-01-31
Hi, I don't know if anyone ever answered the original question, but I have a similar one. I had ubuntu 9.10 loaded and then added a Sabayon partition. Like some others, I've now essentially lost my Ubuntu. I ran the shell script, and here's the output: You'll notice that I've begun editing the grub.cfg, but that the ubuntu-generic section is way too simple.

```

 => Grub 0.97 is installed in the MBR of /dev/sda and looks at sector 67137 on 
    boot drive #1 for the stage2 file. A stage2 file is at this location on 
    /dev/sda. Stage2 looks on partition #1 for /grub/grub.conf.
sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /grub/menu.lst 
                       /boot/grub/grub.conf /grub/grub.conf

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       LVM2_member
    Boot sector type:  -
    Boot sector info:  

VolGroup00-LogVol00: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: /dev/mapper/VolGroup00-LogVol00 already mounted or LVM/VolGroup00-LogVol00 busy

VolGroup00-LogVol01: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb83ee7c5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63       208,844       208,782  83 Linux
/dev/sda2         115,684,065   234,436,544   118,752,480   5 Extended
/dev/sda5         228,476,493   234,436,544     5,960,052  82 Linux swap / Solaris
/dev/sda6    *    115,684,191   223,769,384   108,085,194  83 Linux
/dev/sda7         223,769,448   228,476,429     4,706,982  82 Linux swap / Solaris
/dev/sda3    *        208,845   115,684,064   115,475,220  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/VolGroup00-LogVol00 69258c0c-302b-4905-bac5-89595ffa70e8   ext4       Ubuntu                        
/dev/mapper/VolGroup00-LogVol01 4f1ddc4a-c6cd-4c47-8c0b-6330147faa2d   swap                                     
/dev/sda1        b266bb26-bab0-40d1-ba4a-148eba68bd0c   ext4       /boot                         
/dev/sda3        zWvpHR-Gp2f-WpV4-A4gw-psor-irWe-UL1CAp LVM2_member                               
/dev/sda5        b833d278-00a4-4d2f-a63b-d55815cb4bfa   swap                                     
/dev/sda6        f40512ac-898e-42c4-a0fe-f7144e911476   ext4       Ubuntu                        
/dev/sda7        71fa8143-3be0-47cf-add2-24eb3cd5d861   swap                                     

=============================== "ls -R /dev/mapper/" output: ===============================
/dev/mapper:
control
VolGroup00-LogVol00
VolGroup00-LogVol01

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/VolGroup00/LogVol00 /                        ext4       (rw,noatime,barrier=1,data=ordered)
/dev/shm         /dev/shm                 tmpfs      (rw,relatime)
/dev/sda1        /boot                    ext4       (rw,noatime,user_xattr)
/dev/sda6        /media/disk              ext4       (rw,nosuid,nodev,uhelper=hal)


========================== sda1/boot/grub/grub.conf: ==========================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /kernel-genkernel real_root=/dev/VolGroup00/LogVol00
#          initrd /initramfs-genkernel
### AUTOMAGIC BOOT DEVICE DETECTION -- DO NOT REMOVE ###
#boot=sda
### AUTOMAGIC BOOT DEVICE DETECTION END ###
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz


title Ubuntu Net Remix (kernel-genkernel-x86_64-2.6.17-generic)
	root (hd0,6)
	kernel /boot/vmlinuz-2.6.17-generic
	initrd /boot/initrd.img-2.6.31-17-generic
	
title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon)
	root (hd0,0)
	kernel /kernel-genkernel-x86_64-2.6.31-sabayon  root=/dev/ram0 ramdisk=8192 real_root=/dev/VolGroup00/LogVol00 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda5 real_resume=/dev/sda5
	initrd /initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode)
	root (hd0,0)
	kernel /kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/VolGroup00/LogVol00 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sda5 real_resume=/dev/sda5 nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


============================= sda1/grub/grub.conf: =============================

# grub.conf generated by the Sabayon Linux Installer
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,0)
#          kernel /kernel-genkernel real_root=/dev/VolGroup00/LogVol00
#          initrd /initramfs-genkernel
### AUTOMAGIC BOOT DEVICE DETECTION -- DO NOT REMOVE ###
#boot=sda
### AUTOMAGIC BOOT DEVICE DETECTION END ###
default=0
timeout=5
splashimage=(hd0,0)/grub/splash.xpm.gz


title Ubuntu Net Remix (kernel-genkernel-x86_64-2.6.17-generic)
	root (hd0,6)
	kernel /boot/vmlinuz-2.6.17-generic
	initrd /boot/initrd.img-2.6.31-17-generic
	
title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon)
	root (hd0,0)
	kernel /kernel-genkernel-x86_64-2.6.31-sabayon  root=/dev/ram0 ramdisk=8192 real_root=/dev/VolGroup00/LogVol00 dolvm init=/linuxrc splash=silent,theme:sabayon vga=791 console=tty1 quiet resume=swap:/dev/sda5 real_resume=/dev/sda5
	initrd /initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


title Sabayon Linux (kernel-genkernel-x86_64-2.6.31-sabayon) (safe mode)
	root (hd0,0)
	kernel /kernel-genkernel-x86_64-2.6.31-sabayon root=/dev/ram0 ramdisk=8192 real_root=/dev/VolGroup00/LogVol00 dolvm init=/linuxrc console=tty1 resume=swap:/dev/sda5 real_resume=/dev/sda5 nox gentoo=nox acpi=off ide=nodma vga=normal
	initrd /initramfs-genkernel-x86_64-2.6.31-sabayon
	savedefault


=================== sda1: Location of files loaded by Grub: ===================


    .0GB: boot/grub/grub.conf
    .0GB: boot/grub/menu.lst
    .0GB: boot/grub/stage2
    .0GB: boot/initramfs-genkernel-x86_64-2.6.31-sabayon
    .0GB: grub/grub.conf
    .0GB: grub/menu.lst
    .0GB: grub/stage2
    .0GB: initramfs-genkernel-x86_64-2.6.31-sabayon

=========================== sda6/boot/grub/grub.cfg: ===========================

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
set root=(hd0,6)
search --no-floppy --fs-uuid --set f40512ac-898e-42c4-a0fe-f7144e911476
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
menuentry "Ubuntu, Linux 2.6.31-17-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set f40512ac-898e-42c4-a0fe-f7144e911476
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=f40512ac-898e-42c4-a0fe-f7144e911476 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-17-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set f40512ac-898e-42c4-a0fe-f7144e911476
	linux	/boot/vmlinuz-2.6.31-17-generic root=UUID=f40512ac-898e-42c4-a0fe-f7144e911476 ro single 
	initrd	/boot/initrd.img-2.6.31-17-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	set quiet=1
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set f40512ac-898e-42c4-a0fe-f7144e911476
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f40512ac-898e-42c4-a0fe-f7144e911476 ro   quiet splash
	initrd	/boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
	insmod ext2
	set root=(hd0,6)
	search --no-floppy --fs-uuid --set f40512ac-898e-42c4-a0fe-f7144e911476
	linux	/boot/vmlinuz-2.6.31-14-generic root=UUID=f40512ac-898e-42c4-a0fe-f7144e911476 ro single 
	initrd	/boot/initrd.img-2.6.31-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set dcfe5bb1-1a4b-4d5f-bda9-f49d1b8fa352
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=dcfe5bb1-1a4b-4d5f-bda9-f49d1b8fa352 ro quiet splash
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set dcfe5bb1-1a4b-4d5f-bda9-f49d1b8fa352
	linux /boot/vmlinuz-2.6.28-17-generic root=UUID=dcfe5bb1-1a4b-4d5f-bda9-f49d1b8fa352 ro single
	initrd /boot/initrd.img-2.6.28-17-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set dcfe5bb1-1a4b-4d5f-bda9-f49d1b8fa352
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=dcfe5bb1-1a4b-4d5f-bda9-f49d1b8fa352 ro quiet splash
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode) (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set dcfe5bb1-1a4b-4d5f-bda9-f49d1b8fa352
	linux /boot/vmlinuz-2.6.28-15-generic root=UUID=dcfe5bb1-1a4b-4d5f-bda9-f49d1b8fa352 ro single
	initrd /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu 9.04, memtest86+ (on /dev/sda1)" {
	insmod ext2
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set dcfe5bb1-1a4b-4d5f-bda9-f49d1b8fa352
	linux /boot/memtest86+.bin 
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=f40512ac-898e-42c4-a0fe-f7144e911476 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=71fa8143-3be0-47cf-add2-24eb3cd5d861 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


  59.2GB: boot/grub/core.img
  59.2GB: boot/grub/grub.cfg
  59.2GB: boot/initrd.img-2.6.31-14-generic
  59.2GB: boot/initrd.img-2.6.31-17-generic
  59.2GB: boot/vmlinuz-2.6.31-14-generic
  59.2GB: boot/vmlinuz-2.6.31-17-generic
  59.2GB: initrd.img
  59.2GB: initrd.img.old
  59.2GB: vmlinuz
  59.2GB: vmlinuz.old
=============================== StdErr Messages: ===============================

mdadm: No arrays found in config file or automatically
```

Thanks for any advice. I'd be happy to just know where to look if there's a simple solution elsewhere. 

Thanks, 
Ben

---

