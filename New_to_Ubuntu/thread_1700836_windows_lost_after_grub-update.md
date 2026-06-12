---
title: "windows lost after grub-update"
date: 2011-03-05
forum: New to Ubuntu
---

### Post by Roger49 on 2011-03-05
Hi All,
I have Maverick Meercat installed on an external usb hard disk.
I had to edit the GRUB script and update GRUB because of a graphics problem.
(I had to delete "Quiet and splash" and insert "i915.modeset=1")
After running "sudo update-grub" I no longer had the option of booting into Windows from the GRUB menu.
 
Details of system are:
 
Monitor: CTX 1569SE
Machine: HP Compaq Pentium 4, 512MB RAM
Graphics: Intel 829158/GV/910GL Express 
ubuntu@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
/dev/sda: 4GB Quantum Bigfoot, Slave drive, from old Win95 machine.
/dev/sdb: 80GB Maxtor 6V080E0 Win XP Pro, bootable
/dev/sdc: 320GB Intenso USB hard disk, with GRUB2 resident.
/dev/sdc1: 80GB partition with Ubuntu 10.10 installed, ext3.
/dev/sdc2: 4GB partition, Linux Swap.
 
Any suggestions as to how I can get it back?
I read something on another thread about "osprobe" not recognising other resident OS's?
 
Regards,
Roger49

---

### Post by minigeek on 2011-03-05
> **Roger49 said:**
> Hi All,
I have Maverick Meercat installed on an external usb hard disk.
I had to edit the GRUB script and update GRUB because of a graphics problem.
(I had to delete "Quiet and splash" and insert "i915.modeset=1")
After running "sudo update-grub" I no longer had the option of booting into Windows from the GRUB menu.
 
Details of system are:
 
Monitor: CTX 1569SE
Machine: HP Compaq Pentium 4, 512MB RAM
Graphics: Intel 829158/GV/910GL Express 
ubuntu@ubuntu:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04)
/dev/sda: 4GB Quantum Bigfoot, Slave drive, from old Win95 machine.
/dev/sdb: 80GB Maxtor 6V080E0 Win XP Pro, bootable
/dev/sdc: 320GB Intenso USB hard disk, with GRUB2 resident.
/dev/sdc1: 80GB partition with Ubuntu 10.10 installed, ext3.
/dev/sdc2: 4GB partition, Linux Swap.
 
Any suggestions as to how I can get it back?
I read something on another thread about "osprobe" not recognising other resident OS's?
 
Regards,
Roger49

Hi 

Try supergrub
[http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/)

---

### Post by grahammechanical on 2011-03-05
You say

>  I no longer had the option of booting into Windows from the GRUB menu.

Is this with the external USB hard disc removed? I am just checking.

How did you modify grub? Perhaps you removed the part of the script that instructs Grub to probe for other OS.

Regards.

---

### Post by Roger49 on 2011-03-06
Hi Grahammechanical,
The only change I made to the grub script was to replace "quiet and splash" with "i915.modeset=1" Grub is resident on the external USB hard disk.
Regards,
Roger49

---

### Post by Roger49 on 2011-03-08
Hi Grahammechanical,
Any news yet?
There's no hurry though, as I can choose between a usb device or hard disk at bios stage.
I can use this to choose between Ubuntu and Windows.
All the best,
Roger49

---

### Post by garvinrick4 on 2011-03-08
While in Ubuntu run:
```
sudo grub-mkconfig
```If os-prober does not go out and find other operating systems and put in grub2 then
run. 
```
sudo grub-install --recheck  /dev/sdc
``````
sudo update-grub
``````
grep menuentry /boot/grub/grub.cfg
```after running last bit of code does it give you Windows as a menuentry?

---

### Post by Roger49 on 2011-03-13
Hi Garvinrick4,
Sorry to take so long about coming back to you. I tried the commands in your last message, but my Windows installations were not recognised. 

See code here:

```

```
roger@HP-Compaq-dc5100-MT-EC955ET:~$ sudo grub-install --recheck /dev/sdd
Installation finished. No error reported.
roger@HP-Compaq-dc5100-MT-EC955ET:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-22-generic
Found initrd image: /boot/initrd.img-2.6.35-22-generic
Found memtest86+ image: /boot/memtest86+.bin
done
roger@HP-Compaq-dc5100-MT-EC955ET:~$ grep menuentry /boot/grub/grub.cfg
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
menuentry "Memory test (memtest86+)" {
menuentry "Memory test (memtest86+, serial console 115200)" {
roger@HP-Compaq-dc5100-MT-EC955ET:~$ ^C
roger@HP-Compaq-dc5100-MT-EC955ET:~$ 
```

```

Interestingly, although I installed to "/dev/sdc", partitions 1 and 2, Ubuntu now thinks it is installed on "/dev/sdd" partitions 1 and 2. I do have other usb devices installed now, but "sudo grub-install --recheck /dev/sdc" tells me there is no such drive.
Other than that, everything is going swimmingly.
Regards,
Roger49

---

### Post by Roger49 on 2011-04-05
Hi all,
Any thoughts on this?
Apologies for "CODE" not appearing at front and end of the listing - it was there before I uploaded the message - will preview in future.
Regards,
Roger49

---

### Post by Hippytaff on 2011-04-05
It might be worth posting the results.txt generated by running the boot-info script found [here ]("http://sourceforge.net/projects/bootinfoscript/")so that people know whats what on your system rather than guessing solutions :-)
 
Edit - the code tags would be excellent when you post it :-)

---

### Post by Roger49 on 2011-04-13
Hi All,
Sorry to take so long coming back - real life keeps on getting in the way!

Regret unable to post results.txt.
I put in the code header and footer, but they are stripped out, and disappear from my post when I preview!


[LEFT] I look forward to any suggestions.
All the best,
Roger49[IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG] [/LEFT]

---

### Post by Roger49 on 2011-04-13
Hi All,
Having another go.

                       
```

[LEFT]============================= Boot Info Summary: ==============================[/LEFT]
    
    [LEFT] => Windows is installed in the MBR of /dev/sda[/LEFT]
    [LEFT] => No boot loader is installed in the MBR of /dev/sdb[/LEFT]
    [LEFT] => Grub 2 is installed in the MBR of /dev/sdd and looks on the same drive in [/LEFT]
    [LEFT]    partition #1 for (,msdos1)/boot/grub.[/LEFT]
    [LEFT] => No boot loader? is installed in the MBR of /dev/sdf[/LEFT]
    [LEFT] => No boot loader? is installed in the MBR of /dev/sdg[/LEFT]
    
    [LEFT]sda1: _________________________________________________________________________[/LEFT]
    
    [LEFT]    File system:       vfat[/LEFT]
    [LEFT]    Boot sector type:  MSWIN4.1: Fat 32[/LEFT]
    [LEFT]    Boot sector info:  No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  Windows 95[/LEFT]
    [LEFT]    Boot files/dirs:   /IO.SYS /MSDOS.SYS /COMMAND.COM[/LEFT]
    
    [LEFT]sdb1: _________________________________________________________________________[/LEFT]
    
    [LEFT]    File system:       ntfs[/LEFT]
    [LEFT]    Boot sector type:  Windows XP[/LEFT]
    [LEFT]    Boot sector info:  No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  Windows XP[/LEFT]
    [LEFT]    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM[/LEFT]
    
    [LEFT]sdd1: _________________________________________________________________________[/LEFT]
    
    [LEFT]    File system:       ext3[/LEFT]
    [LEFT]    Boot sector type:  -[/LEFT]
    [LEFT]    Boot sector info:  [/LEFT]
    [LEFT]    Operating System:  Ubuntu 10.10[/LEFT]
    [LEFT]    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img[/LEFT]
    
    [LEFT]sdd2: _________________________________________________________________________[/LEFT]
    
    [LEFT]    File system:       swap[/LEFT]
    [LEFT]    Boot sector type:  -[/LEFT]
    [LEFT]    Boot sector info:  [/LEFT]
    
    [LEFT]sdf1: _________________________________________________________________________[/LEFT]
    
    [LEFT]    File system:       vfat[/LEFT]
    [LEFT]    Boot sector type:  Fat16[/LEFT]
    [LEFT]    Boot sector info:  According to the info in the boot sector, sdf1 has 0 [/LEFT]
    [LEFT]                       sectors.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files/dirs:   [/LEFT]
    
    [LEFT]sdg1: _________________________________________________________________________[/LEFT]
    
    [LEFT]    File system:       vfat[/LEFT]
    [LEFT]    Boot sector type:  Fat16[/LEFT]
    [LEFT]    Boot sector info:  No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files/dirs:   [/LEFT]
    
    [LEFT]sde: _________________________________________________________________________[/LEFT]
    
    [LEFT]    File system:       vfat[/LEFT]
    [LEFT]    Boot sector type:  Unknown[/LEFT]
    [LEFT]    Boot sector info:  No errors found in the Boot Parameter Block.[/LEFT]
    [LEFT]    Operating System:  [/LEFT]
    [LEFT]    Boot files/dirs:   [/LEFT]
    
    [LEFT]=========================== Drive/Partition Info: =============================[/LEFT]
    
    [LEFT]Drive: sda ___________________ _____________________________________________________[/LEFT]
    
    [LEFT]Disk /dev/sda: 4335 MB, 4335206400 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 527 cylinders, total 8467200 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
    
    [LEFT]Partition  Boot         Start           End          Size  Id System[/LEFT]
    
    [LEFT]/dev/sda1    *             63     8,450,189     8,450,127   b W95 FAT32[/LEFT]
    
    
    [LEFT]Drive: sdb ___________________ _____________________________________________________[/LEFT]
    
    [LEFT]Disk /dev/sdb: 80.0 GB, 80026361856 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
    
    [LEFT]Partition  Boot         Start           End          Size  Id System[/LEFT]
    
    [LEFT]/dev/sdb1    *             63   156,280,319   156,280,257   7 HPFS/NTFS[/LEFT]
    
    
    [LEFT]Drive: sdd ___________________ _____________________________________________________[/LEFT]
    
    [LEFT]Disk /dev/sdd: 320.1 GB, 320072933376 bytes[/LEFT]
    [LEFT]255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
    
    [LEFT]Partition  Boot         Start           End          Size  Id System[/LEFT]
    
    [LEFT]/dev/sdd1    *          2,048   156,250,111   156,248,064  83 Linux[/LEFT]
    [LEFT]/dev/sdd2         156,250,112   164,062,611     7,812,500  82 Linux swap / Solaris[/LEFT]
    
    
    [LEFT]Drive: sdf ___________________ _____________________________________________________[/LEFT]
    
    [LEFT]Disk /dev/sdf: 4 MB, 4718592 bytes[/LEFT]
    [LEFT]2 heads, 32 sectors/track, 144 cylinders, total 9216 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
    
    [LEFT]Partition  Boot         Start           End          Size  Id System[/LEFT]
    
    [LEFT]/dev/sdf1    *             32         9,215         9,184   1 FAT12[/LEFT]
    
    
    [LEFT]Drive: sdg ___________________ _____________________________________________________[/LEFT]
    
    [LEFT]Disk /dev/sdg: 247 MB, 247463936 bytes[/LEFT]
    [LEFT]16 heads, 32 sectors/track, 944 cylinders, total 483328 sectors[/LEFT]
    [LEFT]Units = sectors of 1 * 512 = 512 bytes[/LEFT]
    [LEFT]Sector size (logical/physical): 512 bytes / 512 bytes[/LEFT]
    
    [LEFT]Partition  Boot         Start           End          Size  Id System[/LEFT]
    
    [LEFT]/dev/sdg1    *             32       482,815       482,784   6 FAT16[/LEFT]
    
    
    [LEFT]blkid -c /dev/null: ____________________________________________________________[/LEFT]
    
    [LEFT]Device           UUID                                   TYPE       LABEL                         [/LEFT]
    
    [LEFT]/dev/sda1        1033-1101                              vfat                                     [/LEFT]
    [LEFT]/dev/sda: PTTYPE="dos" [/LEFT]
    [LEFT]/dev/sdb1        0D722CC16758D0E8                       ntfs                                     [/LEFT]
    [LEFT]/dev/sdb: PTTYPE="dos" [/LEFT]
    [LEFT]/dev/sdd1        c01e751f-bfc1-45b5-b73b-53c3944ee7e3   ext3                                     [/LEFT]
    [LEFT]/dev/sdd2        68dc41c4-be9c-4ef4-8402-fa501f3f70e6   swap                                     [/LEFT]
    [LEFT]/dev/sdd: PTTYPE="dos" [/LEFT]
    [LEFT]/dev/sde         6C85-2F2F                              vfat       STORE'N'GO                    [/LEFT]
    [LEFT]/dev/sdf1        6B09-71AA                              vfat                                     [/LEFT]
    [LEFT]/dev/sdf: PTTYPE="dos" [/LEFT]
    [LEFT]/dev/sdg1                                               vfat                                     [/LEFT]
    [LEFT]/dev/sdg: PTTYPE="dos" [/LEFT]
    [LEFT]error: /dev/sdc: No medium found[/LEFT]
    
    [LEFT]============================ "mount | grep ^/dev  output: ===========================[/LEFT]
    
    [LEFT]Device           Mount_Point              Type       Options[/LEFT]
    
    [LEFT]/dev/sdd1        /                        ext3       (rw,errors=remount-ro,commit=0)[/LEFT]
    [LEFT]/dev/sde          /media/STORE'N'GO        vfat        (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)[/LEFT]
    [LEFT]/dev/sdf1         /media/6B09-71AA         vfat        (ro,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)[/LEFT]
    [LEFT]/dev/sdg1         /media/disk              vfat        (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)[/LEFT]
    
    
    [LEFT]================================ sdb1/boot.ini: ================================[/LEFT]
    
    [LEFT][boot loader][/LEFT]
    [LEFT]timeout=30[/LEFT]
    [LEFT]default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS[/LEFT]
    
    [LEFT][operating systems][/LEFT]
    [LEFT]multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect[/LEFT]
    
    [LEFT][spybotsd][/LEFT]
    [LEFT]timeout.old=30[/LEFT]
    
    
    [LEFT]=========================== sdd1/boot/grub/grub.cfg: ===========================[/LEFT]
    
    #
    [LEFT]# DO NOT EDIT THIS FILE[/LEFT]
    #
    [LEFT]# It is automatically generated by grub-mkconfig using templates[/LEFT]
    [LEFT]# from /etc/grub.d and settings from /etc/default/grub[/LEFT]
    #
    
    [LEFT]### BEGIN /etc/grub.d/00_header ###[/LEFT]
    [LEFT]if [ -s $prefix/grubenv ]; then[/LEFT]
    [LEFT]  set have_grubenv=true[/LEFT]
    [LEFT]  load_env[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]set default="0"[/LEFT]
    [LEFT]if [ "${prev_saved_entry}" ]; then[/LEFT]
    [LEFT]  set saved_entry="${prev_saved_entry}"[/LEFT]
    [LEFT]  save_env saved_entry[/LEFT]
    [LEFT]  set prev_saved_entry=[/LEFT]
    [LEFT]  save_env prev_saved_entry[/LEFT]
    [LEFT]  set boot_once=true[/LEFT]
    [LEFT]fi[/LEFT]
    
    [LEFT]function savedefault {[/LEFT]
    [LEFT]  if [ -z "${boot_once}" ]; then[/LEFT]
    [LEFT]    saved_entry="${chosen}"[/LEFT]
    [LEFT]    save_env saved_entry[/LEFT]
    [LEFT]  fi[/LEFT]
    }
    
    [LEFT]function recordfail {[/LEFT]
    [LEFT]  set recordfail=1[/LEFT]
    [LEFT]  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi[/LEFT]
    }
    
    [LEFT]function load_video {[/LEFT]
    [LEFT]  insmod vbe[/LEFT]
    [LEFT]  insmod vga[/LEFT]
    }
    
    [LEFT]insmod part_msdos[/LEFT]
    [LEFT]insmod ext2[/LEFT]
    [LEFT]set root='(hd2,msdos1)'[/LEFT]
    [LEFT]search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]if loadfont /usr/share/grub/unicode.pf2 ; then[/LEFT]
    [LEFT]  set gfxmode=640x480[/LEFT]
    [LEFT]  load_video[/LEFT]
    [LEFT]  insmod gfxterm[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]terminal_output gfxterm[/LEFT]
    [LEFT]insmod part_msdos[/LEFT]
    [LEFT]insmod ext2[/LEFT]
    [LEFT]set root='(hd2,msdos1)'[/LEFT]
    [LEFT]search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]set locale_dir=($root)/boot/grub/locale[/LEFT]
    [LEFT]set lang=en[/LEFT]
    [LEFT]insmod gettext[/LEFT]
    [LEFT]if [ "${recordfail}" = 1 ]; then[/LEFT]
    [LEFT]  set timeout=-1[/LEFT]
    [LEFT]else[/LEFT]
    [LEFT]  set timeout=10[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]### END /etc/grub.d/00_header ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/05_debian_theme ###[/LEFT]
    [LEFT]set menu_color_normal=white/black[/LEFT]
    [LEFT]set menu_color_highlight=black/light-gray[/LEFT]
    [LEFT]### END /etc/grub.d/05_debian_theme ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/10_linux ###[/LEFT]
    [LEFT]menuentry 'Ubuntu, with Linux 2.6.35-27-generic' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]    recordfail[/LEFT]
    [LEFT]    insmod part_msdos[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root='(hd2,msdos1)'[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=c01e751f-bfc1-45b5-b73b-53c3944ee7e3 ro   i915.modeset=1[/LEFT]
    [LEFT]    initrd    /boot/initrd.img-2.6.35-27-generic[/LEFT]
    }
    [LEFT]menuentry 'Ubuntu, with Linux 2.6.35-27-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]    recordfail[/LEFT]
    [LEFT]    insmod part_msdos[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root='(hd2,msdos1)'[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]    echo    'Loading Linux 2.6.35-27-generic ...'[/LEFT]
    [LEFT]    linux    /boot/vmlinuz-2.6.35-27-generic root=UUID=c01e751f-bfc1-45b5-b73b-53c3944ee7e3 ro single [/LEFT]
    [LEFT]    echo    'Loading initial ramdisk ...'[/LEFT]
    [LEFT]    initrd    /boot/initrd.img-2.6.35-27-generic[/LEFT]
    }
    [LEFT]menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]    recordfail[/LEFT]
    [LEFT]    insmod part_msdos[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root='(hd2,msdos1)'[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c01e751f-bfc1-45b5-b73b-53c3944ee7e3 ro   i915.modeset=1[/LEFT]
    [LEFT]    initrd    /boot/initrd.img-2.6.35-22-generic[/LEFT]
    }
    [LEFT]menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {[/LEFT]
    [LEFT]    recordfail[/LEFT]
    [LEFT]    insmod part_msdos[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root='(hd2,msdos1)'[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]    echo    'Loading Linux 2.6.35-22-generic ...'[/LEFT]
    [LEFT]    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=c01e751f-bfc1-45b5-b73b-53c3944ee7e3 ro single [/LEFT]
    [LEFT]    echo    'Loading initial ramdisk ...'[/LEFT]
    [LEFT]    initrd    /boot/initrd.img-2.6.35-22-generic[/LEFT]
    }
    [LEFT]### END /etc/grub.d/10_linux ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/20_linux_xen ###[/LEFT]
    [LEFT]### END /etc/grub.d/20_linux_xen ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/20_memtest86+ ###[/LEFT]
    [LEFT]menuentry "Memory test (memtest86+)" {[/LEFT]
    [LEFT]    insmod part_msdos[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root='(hd2,msdos1)'[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]    linux16    /boot/memtest86+.bin[/LEFT]
    }
    [LEFT]menuentry "Memory test (memtest86+, serial console 115200)" {[/LEFT]
    [LEFT]    insmod part_msdos[/LEFT]
    [LEFT]    insmod ext2[/LEFT]
    [LEFT]    set root='(hd2,msdos1)'[/LEFT]
    [LEFT]    search --no-floppy --fs-uuid --set c01e751f-bfc1-45b5-b73b-53c3944ee7e3[/LEFT]
    [LEFT]    linux16    /boot/memtest86+.bin console=ttyS0,115200n8[/LEFT]
    }
    [LEFT]### END /etc/grub.d/20_memtest86+ ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/30_os-prober ###[/LEFT]
    [LEFT]### END /etc/grub.d/30_os-prober ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/40_custom ###[/LEFT]
    [LEFT]# This file provides an easy way to add custom menu entries.  Simply type the[/LEFT]
    [LEFT]# menu entries you want to add after this comment.  Be careful not to change[/LEFT]
    [LEFT]# the 'exec tail' line above.[/LEFT]
    [LEFT]### END /etc/grub.d/40_custom ###[/LEFT]
    
    [LEFT]### BEGIN /etc/grub.d/41_custom ###[/LEFT]
    [LEFT]if [ -f  $prefix/custom.cfg ]; then[/LEFT]
    [LEFT]  source $prefix/custom.cfg;[/LEFT]
    [LEFT]fi[/LEFT]
    [LEFT]### END /etc/grub.d/41_custom ###[/LEFT]
    
    [LEFT]=============================== sdd1/etc/fstab: ===============================[/LEFT]
    
    [LEFT]# /etc/fstab: static file system information.[/LEFT]
    #
    [LEFT]# Use 'blkid -o value -s UUID' to print the universally unique identifier[/LEFT]
    [LEFT]# for a device; this may be used with UUID= as a more robust way to name[/LEFT]
    [LEFT]# devices that works even if disks are added and removed. See fstab(5).[/LEFT]
    #
    [LEFT]# <file system> <mount point>   <type>  <options>       <dump>  <pass>[/LEFT]
    [LEFT]proc            /proc           proc    nodev,noexec,nosuid 0       0[/LEFT]
    [LEFT]# / was on /dev/sdc1 during installation[/LEFT]
    [LEFT]UUID=c01e751f-bfc1-45b5-b73b-53c3944ee7e3 /               ext3    errors=remount-ro 0       1[/LEFT]
    [LEFT]# swap was on /dev/sdc2 during installation[/LEFT]
    [LEFT]UUID=68dc41c4-be9c-4ef4-8402-fa501f3f70e6 none            swap    sw              0       0[/LEFT]
    [LEFT]/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0[/LEFT]
    
    [LEFT]=================== sdd1: Location of files loaded by Grub: ===================[/LEFT]
    
    
    [LEFT]  70.8GB: boot/grub/core.img[/LEFT]
    [LEFT]  70.8GB: boot/grub/grub.cfg[/LEFT]
    [LEFT]  70.8GB: boot/initrd.img-2.6.35-22-generic[/LEFT]
    [LEFT]  70.8GB: boot/initrd.img-2.6.35-27-generic[/LEFT]
    [LEFT]  70.7GB: boot/vmlinuz-2.6.35-22-generic[/LEFT]
    [LEFT]  70.7GB: boot/vmlinuz-2.6.35-27-generic[/LEFT]
    [LEFT]  70.8GB: initrd.img[/LEFT]
    [LEFT]  70.8GB: initrd.img.old[/LEFT]
    [LEFT]  70.7GB: vmlinuz[/LEFT]
    [LEFT]  70.7GB: vmlinuz.old[/LEFT]
    [LEFT]=========================== Unknown MBRs/Boot Sectors/etc =======================[/LEFT]
    
    [LEFT]Unknown BootLoader  on sde[/LEFT]
    
    [LEFT]00000000  eb 3c 90 4d 53 57 49 4e  34 2e 31 00 02 40 20 00  |.<.MSWIN4.1..@ .|[/LEFT]
    [LEFT]00000010  02 00 02 00 00 f8 00 01  3f 00 ff 00 00 00 00 00  |........?.......|[/LEFT]
    [LEFT]00000020  00 40 3c 00 80 00 29 2f  2f 85 6c 4e 4f 20 4e 41  |.@<...)//.lNO NA|[/LEFT]
    [LEFT]00000030  4d 45 20 20 20 20 46 41  54 31 36 20 20 20 fa 33  |ME    FAT16   .3|[/LEFT]
    [LEFT]00000040  c9 8e d1 bc fc 7b 16 07  bd 78 00 c5 76 00 1e 56  |.....{...x..v..V|[/LEFT]
    [LEFT]00000050  16 55 bf 22 05 89 7e 00  89 4e 02 b1 0b fc f3 a4  |.U."..~..N......|[/LEFT]
    [LEFT]00000060  06 1f bd 00 7c c6 45 fe  0f 8b 46 18 88 45 f9 38  |....|.E...F..E.8|[/LEFT]
    [LEFT]00000070  4e 24 7d 22 8b c1 99 e8  77 01 72 1a 83 eb 3a 66  |N$}"....w.r...:f|[/LEFT]
    [LEFT]00000080  a1 1c 7c 66 3b 07 8a 57  fc 75 06 80 ca 02 88 56  |..|f;..W.u.....V|[/LEFT]
    [LEFT]00000090  02 80 c3 10 73 ed 33 c9  8a 46 10 98 f7 66 16 03  |....s.3..F...f..|[/LEFT]
    [LEFT]000000a0  46 1c 13 56 1e 03 46 0e  13 d1 8b 76 11 60 89 46  |F..V..F....v.`.F|[/LEFT]
    [LEFT]000000b0  fc 89 56 fe b8 20 00 f7  e6 8b 5e 0b 03 c3 48 f7  |..V.. ....^...H.|[/LEFT]
    [LEFT]000000c0  f3 01 46 fc 11 4e fe 61  bf 00 07 e8 23 01 72 39  |..F..N.a....#.r9|[/LEFT]
    [LEFT]000000d0  38 2d 74 17 60 b1 0b be  d8 7d f3 a6 61 74 39 4e  |8-t.`....}..at9N|[/LEFT]
    [LEFT]000000e0  74 09 83 c7 20 3b fb 72  e7 eb dd be 7f 7d ac 98  |t... ;.r.....}..|[/LEFT]
    [LEFT]000000f0  03 f0 ac 84 c0 74 17 3c  ff 74 09 b4 0e bb 07 00  |.....t.<.t......|[/LEFT]
    [LEFT]00000100  cd 10 eb ee be 82 7d eb  e5 be 80 7d eb e0 98 cd  |......}....}....|[/LEFT]
    [LEFT]00000110  16 5e 1f 66 8f 04 cd 19  be 81 7d 8b 7d 1a 8d 45  |.^.f......}.}..E|[/LEFT]
    [LEFT]00000120  fe 8a 4e 0d f7 e1 03 46  fc 13 56 fe b1 04 e8 c1  |..N....F..V.....|[/LEFT]
    [LEFT]00000130  00 72 d6 ea 00 02 70 00  b4 42 eb 2d 60 66 6a 00  |.r....p..B.-`fj.|[/LEFT]
    [LEFT]00000140  52 50 06 53 6a 01 6a 10  8b f4 74 ec 91 92 33 d2  |RP.Sj.j...t...3.|[/LEFT]
    [LEFT]00000150  f7 76 18 91 f7 76 18 42  87 ca f7 76 1a 8a f2 8a  |.v...v.B...v....|[/LEFT]
    [LEFT]00000160  e8 c0 cc 02 0a cc b8 01  02 8a 56 24 cd 13 8d 64  |..........V$...d|[/LEFT]
    [LEFT]00000170  10 61 72 0a 40 75 01 42  03 5e 0b 49 75 77 c3 03  |.ar.@u.B.^.Iuw..|[/LEFT]
    [LEFT]00000180  18 01 27 0d 0a 49 6e 76  61 6c 69 64 20 73 79 73  |..'..Invalid sys|[/LEFT]
    [LEFT]00000190  74 65 6d 20 64 69 73 6b  ff 0d 0a 44 69 73 6b 20  |tem disk...Disk |[/LEFT]
    [LEFT]000001a0  49 2f 4f 20 65 72 72 6f  72 ff 0d 0a 52 65 70 6c  |I/O error...Repl|[/LEFT]
    [LEFT]000001b0  61 63 65 20 74 68 65 20  64 69 73 6b 2c 20 61 6e  |ace the disk, an|[/LEFT]
    [LEFT]000001c0  64 20 74 68 65 6e 20 70  72 65 73 73 20 61 6e 79  |d then press any|[/LEFT]
    [LEFT]000001d0  20 6b 65 79 0d 0a 00 00  49 4f 20 20 20 20 20 20  | key....IO      |[/LEFT]
    [LEFT]000001e0  53 59 53 4d 53 44 4f 53  20 20 20 53 59 53 7f 01  |SYSMSDOS   SYS..|[/LEFT]
    [LEFT]000001f0  00 41 bb 00 07 80 7e 02  0e e9 40 ff 00 00 55 aa  |.A....~...@...U.|[/LEFT]
    00000200
    
    
    [LEFT]=======Devices which don't seem to have a corresponding hard drive==============[/LEFT]
    
    [LEFT]sdc [/LEFT]

```

SUCCESS!

I look forward to any comments.
Regards,
Roger49

---

### Post by Roger49 on 2011-04-21
Hi All,
Will spend part of Easter reinstalling.
May try 10.04 Lucid.
TTFN
Roger49

---

### Post by Roger49 on 2011-05-10
FIXED!
Checking, I found another person with the same problem.
"os-prober" is used at installation, but not actually installed.
Hence, when I ran "update-grub", my Windows installations vanished from the GRUB menu.
I installed "os-prober" from Synaptic, re-ran "update-grub" and hey presto!
Thanks for all the help,
Roger49

---

### Post by oliveryty on 2011-05-10
I retreated to 10.10. 

And ubuntu 10.10 is the best so far.

---

