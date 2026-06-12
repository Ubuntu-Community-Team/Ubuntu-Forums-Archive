---
title: "Cannot boot into Vista after latest linux image 2.6.32-25upgrade"
date: 2010-09-06
forum: New to Ubuntu
---

### Post by scrypt on 2010-09-06
Cannot Boot into Vista after latest Ubuntu linux image 

The image upgrade that has stopped me from being able to boot into vista is called :

linux image: /boot/vmlinuz-2.6.32-25-generic

I have a dual boot Ubuntu 10:04 (lucid lynx) and Vista.
All has been working well until I upgraded to the new linux image release.

I have tried to repair grub-pc using these usual commands:

sudo fdisk -l

laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x18000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       31081   249550848    7  HPFS/NTFS
/dev/sda3           31081       38914    62915585    f  W95 Ext'd (LBA)
/dev/sda5           31081       38588    60302336   83  Linux


sudo mount /dev/sda5 /mnt

sudo grub-install --root-directory=/mnt/ /dev/sda

sudo update-grub

laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

---

### Post by garvinrick4 on 2010-09-06
Are you using a live CD so as not mounted?

I like this just a touch better.

sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

---

### Post by scrypt on 2010-09-06
Okay. I just rebooted. I cannot boot into anything now. Not even Ubuntu.

when I start my PC I am met with A black screen with this error message:

error: file not found
grub rescue>

I really would appreciate any help on rescuing my system.
I am using Ubuntu 10:04 (lucid lynx) live cd at the moment

---

### Post by scrypt on 2010-09-06
I am using ubuntu 10:04 (lucid lynx) live CD. with network connection. To try to repair my system

---

### Post by garvinrick4 on 2010-09-06
Use the live Cd and do this. I like labels

give your sda5 a label lets say lucid. In gparted right click on sda5 and choose label, label it lucid then apply with green arrow. Open a terminal and copy and paste these.

```
sudo mkdir /media/lucid
``````
sudo mount /dev/sda5 /media/lucid
``````
sudo grub-install --recheck --root-directory=/media/lucid /dev/sda
``````
sudo umount /media/lucid
```reboot into linux hdd install and.
```
sudo update-grub
```

---

### Post by scrypt on 2010-09-06
Hello garvinrick4 thank you for your help.

I followed your commands. I also Labled /dev/sda5 and called it lucid.

I then ran all the commands you suggested:

here are all the commands (copied and pasted from your last reply)
and their output. All seemed to work well untill last command sudo update-grub.

ubuntu@ubuntu:~$ sudo mkdir /media/lucid

ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/lucid

ubuntu@ubuntu:~$ sudo grub-install --recheck --root-directory=/media/lucid /dev/sda
Installation finished. No error reported.

ubuntu@ubuntu:~$ sudo umount /media/lucid

ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Any more help is appreciated

---

### Post by garvinrick4 on 2010-09-06
Boot into your HDD now and into Ubuntu install and then:
```
sudo update-grub
```

It should be fine now.

---

### Post by garvinrick4 on 2010-09-06
If you are up and going mark this thread as solved.

---

### Post by scrypt on 2010-09-06
hello garvinrick4

I can now successfully boot back into Ubuntu from normal grub boot screen. That is fixed. But...

There is no option to boot into Vista. only three different ubuntu linux images.

here is the sudo update-grub output:

laptop:~$ sudo update-grub
[sudo] password for mark: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

Can you help me fix this non Vista boot issue ??

---

### Post by garvinrick4 on 2010-09-06
[LEFT]Run this in terminal and see if Vista is in there. Copy and paste for me so I can see it.



```
grep menuentry [/boot/grub/grub.cfg]("file:///boot/grub/grub.cfg")
```[]("file:///boot/grub/grub.cfg")[/LEFT]

---

### Post by scrypt on 2010-09-06
Here is the grep menuentry /boot/grub/grub.cfg
output:

laptop:~$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {

---

### Post by scrypt on 2010-09-06
Can you give any insight into why you think the vista entry has disappeared from grub. ??

---

### Post by garvinrick4 on 2010-09-06
> **scrypt said:**
> Can you give any insight into why you think the vista entry has disappeared from grub. ?? Your sudo fdisk -l says it is there. 
Ok ready I am going to give you a site to download a script to your DESKTOP.
Make sure it is on your desk top then run this in a terminal and it will put a file on
your desktop to see your whole boot. Copy and paste it in this thread and highlight the
whole thing and then click on the # sign and it will make it easier to read.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
Above is the page to download script to DESKTOP and below is what you run in terminal.
to get the text file on desktop only takes a few minutes.
 

```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by scrypt on 2010-09-06
Here is the Results text file you asked for:

  ```
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /boot/grub/core.img

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   499,308,543   499,101,696   7 HPFS/NTFS
/dev/sda3         499,310,590   625,141,759   125,831,170   f W95 Ext d (LBA)
/dev/sda5         499,310,592   619,915,263   120,604,672  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9C32B29E32B27D38                       ntfs       System Reserved               
/dev/sda2        4640B62240B6189F                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ad3427a2-700b-4a6e-a1cd-cd627761e512   ext4       lucid                         
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/4640B62240B6189F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
	echo	'Loading Linux 2.6.32-25-generic ...'
	linux	/boot/vmlinuz-2.6.32-25-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
	echo	'Loading Linux 2.6.32-24-generic ...'
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
	echo	'Loading Linux 2.6.32-23-generic ...'
	linux	/boot/vmlinuz-2.6.32-23-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro single 
	echo	'Loading initial ramdisk ...'
	initrd	/boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
	linux16	/boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
	insmod ext2
	set root='(hd0,5)'
	search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
	linux16	/boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ccf82469-44d5-473b-9b6f-523e8ee43199 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 296.5GB: boot/grub/core.img
 258.6GB: boot/grub/grub.cfg
 296.7GB: boot/initrd.img-2.6.32-23-generic
 267.4GB: boot/initrd.img-2.6.32-24-generic
 267.3GB: boot/initrd.img-2.6.32-25-generic
 296.5GB: boot/vmlinuz-2.6.32-23-generic
 298.5GB: boot/vmlinuz-2.6.32-24-generic
 298.7GB: boot/vmlinuz-2.6.32-25-generic
 267.3GB: initrd.img
 267.4GB: initrd.img.old
 298.7GB: vmlinuz
 298.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  20 6e 61 6d 65 3d 22 62  72 61 73 65 72 6f 22 20  | name="brasero" |
00000010  65 78 65 63 3d 22 26 61  70 6f 73 3b 62 72 61 73  |exec="&apos;bras|
00000020  65 72 6f 20 2d 70 20 25  75 26 61 70 6f 73 3b 22  |ero -p %u&apos;"|
00000030  20 6d 6f 64 69 66 69 65  64 3d 22 32 30 31 30 2d  | modified="2010-|
00000040  30 31 2d 32 32 54 31 37  3a 33 34 3a 30 37 5a 22  |01-22T17:34:07Z"|
00000050  20 63 6f 75 6e 74 3d 22  35 22 2f 3e 0a 20 20 20  | count="5"/>.   |
00000060  20 20 20 20 20 3c 2f 62  6f 6f 6b 6d 61 72 6b 3a  |     </bookmark:|
00000070  61 70 70 6c 69 63 61 74  69 6f 6e 73 3e 0a 20 20  |applications>.  |
00000080  20 20 20 20 3c 2f 6d 65  74 61 64 61 74 61 3e 0a  |    </metadata>.|
00000090  20 20 20 20 3c 2f 69 6e  66 6f 3e 0a 20 20 3c 2f  |    </info>.  </|
000000a0  62 6f 6f 6b 6d 61 72 6b  3e 0a 20 20 3c 62 6f 6f  |bookmark>.  <boo|
000000b0  6b 6d 61 72 6b 20 68 72  65 66 3d 22 62 75 72 6e  |kmark href="burn|
000000c0  3a 2f 2f 2f 22 20 61 64  64 65 64 3d 22 32 30 31  |:///" added="201|
000000d0  30 2d 30 31 2d 32 32 54  31 37 3a 31 35 3a 35 31  |0-01-22T17:15:51|
000000e0  5a 22 20 6d 6f 64 69 66  69 65 64 3d 22 32 30 31  |Z" modified="201|
000000f0  30 2d 30 31 2d 32 32 54  31 37 3a 31 35 3a 35 31  |0-01-22T17:15:51|
00000100  5a 22 20 76 69 73 69 74  65 64 3d 22 32 30 31 30  |Z" visited="2010|
00000110  2d 30 31 2d 32 32 54 31  37 3a 31 35 3a 35 31 5a  |-01-22T17:15:51Z|
00000120  22 3e 0a 20 20 20 20 3c  69 6e 66 6f 3e 0a 20 20  |">.    <info>.  |
00000130  20 20 20 20 3c 6d 65 74  61 64 61 74 61 20 6f 77  |    <metadata ow|
00000140  6e 65 72 3d 22 68 74 74  70 3a 2f 2f 66 72 65 65  |ner="http://free|
00000150  64 65 73 6b 74 6f 70 2e  6f 72 67 22 3e 0a 20 20  |desktop.org">.  |
00000160  20 20 20 20 20 20 3c 6d  69 6d 65 3a 6d 69 6d 65  |      <mime:mime|
00000170  2d 74 79 70 65 20 74 79  70 65 3d 22 61 70 70 6c  |-type type="appl|
00000180  69 63 61 74 69 6f 6e 2f  6f 63 74 65 74 2d 73 74  |ication/octet-st|
00000190  72 65 61 6d 22 2f 3e 0a  20 20 20 20 20 20 20 20  |ream"/>.        |
000001a0  3c 62 6f 6f 6b 6d 61 72  6b 3a 61 70 70 6c 69 63  |<bookmark:applic|
000001b0  61 74 69 6f 6e 73 3e 0a  20 20 20 20 20 20 00 fe  |ations>.      ..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 30 07 00 00  |...........H0...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200
```

I do not understand what you mean when you ask me to click # to make it easier to read. 

>  Copy and paste it in this thread and highlight the
whole thing and then click on the # sign and it will make it easier to read.

Can you please clarify this for me. I always like to learn new Ubuntu tips and tricks.

---

### Post by garvinrick4 on 2010-09-06
```
Here is the Results text file you asked for:

  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #5 for /boot/grub.

sda1: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD /boot/grub/core.img

sda2: __________________________________________________  _______________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe /boot/grub/core.img

sda3: __________________________________________________  _______________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________  _______________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ __________________________________________________  ___

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048       206,847       204,800   7 HPFS/NTFS
/dev/sda2             206,848   499,308,543   499,101,696   7 HPFS/NTFS
/dev/sda3         499,310,590   625,141,759   125,831,170   f W95 Ext d (LBA)
/dev/sda5         499,310,592   619,915,263   120,604,672  83 Linux


blkid -c /dev/null: __________________________________________________  __________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        9C32B29E32B27D38                       ntfs       System Reserved               
/dev/sda2        4640B62240B6189F                       ntfs                                     
/dev/sda3: PTTYPE="dos" 
/dev/sda5        ad3427a2-700b-4a6e-a1cd-cd627761e512   ext4       lucid                         
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda5        /                        ext4       (rw,errors=remount-ro)
/dev/sda2        /media/4640B62240B6189F  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_  permissions)


=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=========================== sda5/boot/grub/grub.cfg: ===========================

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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
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
set root='(hd0,5)'
search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
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
menuentry 'Ubuntu, with Linux 2.6.32-25-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-25-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
    echo    'Loading Linux 2.6.32-25-generic ...'
    linux    /boot/vmlinuz-2.6.32-25-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-25-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-24-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
    echo    'Loading Linux 2.6.32-24-generic ...'
    linux    /boot/vmlinuz-2.6.32-24-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-24-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-23-generic
}
menuentry 'Ubuntu, with Linux 2.6.32-23-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
    echo    'Loading Linux 2.6.32-23-generic ...'
    linux    /boot/vmlinuz-2.6.32-23-generic root=UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.32-23-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod ext2
    set root='(hd0,5)'
    search --no-floppy --fs-uuid --set ad3427a2-700b-4a6e-a1cd-cd627761e512
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

=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ad3427a2-700b-4a6e-a1cd-cd627761e512 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=ccf82469-44d5-473b-9b6f-523e8ee43199 none            swap    sw              0       0

=================== sda5: Location of files loaded by Grub: ===================


 296.5GB: boot/grub/core.img
 258.6GB: boot/grub/grub.cfg
 296.7GB: boot/initrd.img-2.6.32-23-generic
 267.4GB: boot/initrd.img-2.6.32-24-generic
 267.3GB: boot/initrd.img-2.6.32-25-generic
 296.5GB: boot/vmlinuz-2.6.32-23-generic
 298.5GB: boot/vmlinuz-2.6.32-24-generic
 298.7GB: boot/vmlinuz-2.6.32-25-generic
 267.3GB: initrd.img
 267.4GB: initrd.img.old
 298.7GB: vmlinuz
 298.5GB: vmlinuz.old
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sda3

00000000  20 6e 61 6d 65 3d 22 62  72 61 73 65 72 6f 22 20  | name="brasero" |
00000010  65 78 65 63 3d 22 26 61  70 6f 73 3b 62 72 61 73  |exec="&apos;bras|
00000020  65 72 6f 20 2d 70 20 25  75 26 61 70 6f 73 3b 22  |ero -p %u&apos;"|
00000030  20 6d 6f 64 69 66 69 65  64 3d 22 32 30 31 30 2d  | modified="2010-|
00000040  30 31 2d 32 32 54 31 37  3a 33 34 3a 30 37 5a 22  |01-22T17:34:07Z"|
00000050  20 63 6f 75 6e 74 3d 22  35 22 2f 3e 0a 20 20 20  | count="5"/>.   |
00000060  20 20 20 20 20 3c 2f 62  6f 6f 6b 6d 61 72 6b 3a  |     </bookmark:neutral:
00000070  61 70 70 6c 69 63 61 74  69 6f 6e 73 3e 0a 20 20  |applications>.  |
00000080  20 20 20 20 3c 2f 6d 65  74 61 64 61 74 61 3e 0a  |    </metadata>.|
00000090  20 20 20 20 3c 2f 69 6e  66 6f 3e 0a 20 20 3c 2f  |    </info>.  </|
000000a0  62 6f 6f 6b 6d 61 72 6b  3e 0a 20 20 3c 62 6f 6f  |bookmark>.  <boo|
000000b0  6b 6d 61 72 6b 20 68 72  65 66 3d 22 62 75 72 6e  |kmark href="burn|
000000c0  3a 2f 2f 2f 22 20 61 64  64 65 64 3d 22 32 30 31  |:///" added="201|
000000d0  30 2d 30 31 2d 32 32 54  31 37 3a 31 35 3a 35 31  |0-01-22T17:15:51|
000000e0  5a 22 20 6d 6f 64 69 66  69 65 64 3d 22 32 30 31  |Z" modified="201|
000000f0  30 2d 30 31 2d 32 32 54  31 37 3a 31 35 3a 35 31  |0-01-22T17:15:51|
00000100  5a 22 20 76 69 73 69 74  65 64 3d 22 32 30 31 30  |Z" visited="2010|
00000110  2d 30 31 2d 32 32 54 31  37 3a 31 35 3a 35 31 5a  |-01-22T17:15:51Z|
00000120  22 3e 0a 20 20 20 20 3c  69 6e 66 6f 3e 0a 20 20  |">.    <info>.  |
00000130  20 20 20 20 3c 6d 65 74  61 64 61 74 61 20 6f 77  |    <metadata ow|
00000140  6e 65 72 3d 22 68 74 74  70 3a 2f 2f 66 72 65 65  |ner="http://free|
00000150  64 65 73 6b 74 6f 70 2e  6f 72 67 22 3e 0a 20 20  |desktop.org">.  |
00000160  20 20 20 20 20 20 3c 6d  69 6d 65 3a 6d 69 6d 65  |      <mime:mime|
00000170  2d 74 79 70 65 20 74 79  70 65 3d 22 61 70 70 6c  |-type type="appl|
00000180  69 63 61 74 69 6f 6e 2f  6f 63 74 65 74 2d 73 74  |ication/octet-st|
00000190  72 65 61 6d 22 2f 3e 0a  20 20 20 20 20 20 20 20  |ream"/>.        |
000001a0  3c 62 6f 6f 6b 6d 61 72  6b 3a 61 70 70 6c 69 63  |<bookmark:applic|
000001b0  61 74 69 6f 6e 73 3e 0a  20 20 20 20 20 20 00 fe  |ations>.      ..|
000001c0  ff ff 83 fe ff ff 02 00  00 00 00 48 30 07 00 00  |...........H0...|
000001d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200

I do not understand what you mean when you ask me to click # to make it easier to read. 

     Quote:
                                                  Copy and paste it in this thread and highlight the
whole thing and then click on the # sign and it will make it easier to read.                                 
Can you please clarify this for me. I always like to learn new Ubuntu tips and tricks.
```

---

### Post by garvinrick4 on 2010-09-06
I do not understand what you mean when you ask me to click # to make it easier to read. 

     Quote:
                                                  Copy and paste it in this thread and highlight the
whole thing and then click on the # sign and it will make it easier to read.                                 
Can you please clarify this for me. I always like to learn new Ubuntu tips and tricks.

There is a # sign upper right after you highlight your input and click that
# sign it puts it like mine above so not to take up a lot of space. 
They are called code tags.

---

### Post by scrypt on 2010-09-06
Okay. your last post has threw me a bit. I'm not sure what I am supposed to do with it.

Can you also tell me where the # sign is located. I would like to know how to make a scrolling page like that. to make larger text files easier to read

---

### Post by garvinrick4 on 2010-09-06
You notice in the boot script the unknown bootloader in sda3 which is just a extended partition to house linux installs. We know we can get Ubuntu booting anytime so lets
work on Windows. Vista is not in your boot script it stops soon as sda3 pops up with junk. Second time today I have seen Extended partition get this way after upgrade. 
wierd.

Lets try and get vista bootable going to give you a couple of commands for your live CD again. This is to put boot back in Vista hopefully. Once you get Vista back to bootable
Then put live cd back in and overwrite it with Ubuntu grub2 again. The instructions that you
used before remember this time you install grub2 to boot back into ubuntu then update grub. Ok here is the commands to try to get vista booting first.

```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```

When Vista boots then remember you have to put Live CD back in and do the:
Previous instructions with sudo mkdir /media/lucid ect. ect. ect. and install grub to
sda again.
Keep me appraised I will stay up while you do this. 3:25 AM here. I will hang out till you get up and going.

---

### Post by garvinrick4 on 2010-09-06
> **scrypt said:**
> Okay. your last post has threw me a bit. I'm not sure what I am supposed to do with it.

Can you also tell me where the # sign is located. I would like to know how to make a scrolling page like that. to make larger text files easier to read
Upper right of page that you type into. # is third from right in upper right hand corner.

---

### Post by garvinrick4 on 2010-09-06
Hold up a minute I think I see something we can do.
You with me or did you already start?

---

### Post by scrypt on 2010-09-06
Okay

---

### Post by scrypt on 2010-09-06
Im still here. i have not started yet. waiting for you to get back.
before i start anything

---

### Post by garvinrick4 on 2010-09-06
Ok, live cd and make your sda1 label easier just name it system. Will come out in CAPS.
Do not worry about that. Allready says system reserved make it system

sudo mkdir /media/SYSTEM
sudo mkdir /media/lucid
sudo mount /dev/sda1 /media/SYSTEM
sudo mount /dev/sda5 /media/lucid
sudo grub-install --recheck --root-directory=/media/lucid /dev/sda
sudo umount /media/SYSTEM
sudo umount /media/lucid

REBOOT take out CD and boot off of hard drive. Go into Ubuntu and.
```
sudo update-grub
```Now sda1 is a boot partition but you still put it in sda everytime.
If for any reason SYSTEM stays in lower case (system) use that in commands.
should be SYSTEM though.
 Have to mount boot partition if you have one (that is what I want to try before anything) You never put a grub in sda1 did you?
The normal Vista recovery is there but has been deleted and a boot partition in its place. Hope this does it to boot both.

---

### Post by scrypt on 2010-09-06
Okay. i will run caommandsd and post back asap

---

### Post by scrypt on 2010-09-06
Im writing this from inside a live cd session.

SYSTEM did indeed come out in lowercase so I needed to try the alst commands you gave me again.

I am about to reboot into ubuntu proper. and run grub update now...

---

### Post by scrypt on 2010-09-06
Hello I followed all your commands to the letter.But I still have no option to boot into vista on my Grub screen.

here is my newest sudo update-grub output  :

laptop:~$ sudo update-grub
[sudo] password for mark: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-25-generic
Found initrd image: /boot/initrd.img-2.6.32-25-generic
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found linux image: /boot/vmlinuz-2.6.32-23-generic
Found initrd image: /boot/initrd.img-2.6.32-23-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

Im still at a loss. maybe you can carry on helping later

---

### Post by garvinrick4 on 2010-09-06
does this come out in small case letters for system:

```
sudo blkid
``` (small L second letter)

Okay we will not give up, if I cannot get it figured out I have people
out there who can help. See ya later

the sudo blkid I just wanted to see if Upper or lower case letters for system label.
All my ntfs format are upper case when labeled by default.

=================== sda1: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img

=================== sda2: Location of files loaded by Grub: ===================


    ??GB: boot/grub/core.img


Grub cannot find!!   Have a user by the name of kansasnoob looking into this thread to see if he has fix. I will stay in close touch with this thread.

---

### Post by garvinrick4 on 2010-09-06
Did you delete the recovery partition in sda1 or D: in Vista there is a /boot partition their now but had the old Label? Leave anything that was done to drive so as to figure this out a little easier. Lets not give this up until it is fixed.

---

### Post by oldfred on 2010-09-06
You have some extra grub folders in you windows.

sda1
Boot files/dirs: /bootmgr /Boot/BCD [COLOR=Red]/boot/grub/core.img[/COLOR]
sda2
Boot files/dirs: /Windows/System32/winload.exe [COLOR=Red]/boot/grub/core.img[/COLOR]


Windows & grub's osprober will get confused with /Boot & /boot. Windows cannot tell them apart and grub thinks it may be a partial Ubuntu entry but not complete so it ignores the windows settings.

Delete the two /boot folders in windows. [COLOR=DarkRed]Do not delete the windows /Boot folder that has the BCD file. [/COLOR]

---

### Post by garvinrick4 on 2010-09-06
Thanks for helping out oldfred I appreciate it. So user (scrypt) will work in Windows as administrater in command line: bcdedit and delete the entry without the BCD in it. Which would be.

```
bcdedit delete {the indentifier number} 
```

Reboot back into Ubuntu install and:
```
sudo update-grub
```

If any problems reinstall Windows boot and then reinstall grub2 to overwrite Windows boot manager using Live CD and do not forget to mount both sda1 and sda5 and put grub in sda
Below is link for Windows boot loader. If you do not have windows disk the use the lilo  code with Ubuntu disk I gave you earlier. Post outcome please scrypt.

Here is instructions fro windows. 
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708") 
Here is one for grub2
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub")

---

### Post by oldfred on 2010-09-06
Windows does not know capital letters from small letters, so it sees /Boot as exactly the same as /boot and you cannot have two identical folders. In linux of course capitals are different from small letters. 

I think you just have to delete the grub folders from the windows partitions. Then sudo update-grub should work.

---

### Post by kansasnoob on 2010-09-07
> **oldfred said:**
> You have some extra grub folders in you windows.

sda1
Boot files/dirs: /bootmgr /Boot/BCD [COLOR=Red]/boot/grub/core.img[/COLOR]
sda2
Boot files/dirs: /Windows/System32/winload.exe [COLOR=Red]/boot/grub/core.img[/COLOR]


Windows & grub's osprober will get confused with /Boot & /boot. Windows cannot tell them apart and grub thinks it may be a partial Ubuntu entry but not complete so it ignores the windows settings.

Delete the two /boot folders in windows. [COLOR=DarkRed]Do not delete the windows /Boot folder that has the BCD file. [/COLOR]

+1! Meierfra wrote a bit on that:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows)

---

### Post by garvinrick4 on 2010-09-07
Grub2 was installed with  Windows system partition chosen as the  root-directory. This causes the folder /boot/grub to be created on the  Windows system partition. Since ntfs partitions are  case insensitive   this leads  to confusions  between  "/boot" and the already existing  folder "/Boot
[LIST]
[*]Solution
[*]Boot into your Linux OS and deleted or rename the folder /boot  on the Windows system partition. Make sure that your don't delete the  /Boot folder. The /Boot folder contains the file "bcd" which is  necessary to boot Windows Vista/7.
[/LIST]

         This seems to be a big problem in the forums lately with everyone upgrading and or installing 10.10. Kansasnoob and oldfred I hope a lot of users see the solution you all have came up with. It is handy at this time of release schedule.

---

### Post by scrypt on 2010-09-10
Hello guys.

Apologies for not getting back sooner.
Something happened and I not had access to a computer.

I am still having the same problem. But I am going to spend today trying to fix it. I will review the last posts to this thread and post back anything needed.

Thnak's for your help guys

---

