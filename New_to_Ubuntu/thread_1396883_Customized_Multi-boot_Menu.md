---
title: "Customized Multi-boot Menu"
date: 2010-02-02
forum: New to Ubuntu
---

### Post by EG-Zero on 2010-02-02
Since this is Beginner's Talk and the version of of Linux I'm using is based off of Ubuntu, I'm guessing that this is the right place to post this question. . .

I currently have BackTrack4 installed on my flash drive set with persistent changes. I also would like to have Falcon's BootCD being able to boot off a flash drive. It is a diagnostic software similar to Hiren's but it also includes Hirens 9.9 in it which makes me want to use it even more.

The problem I'm having is that I can't boot anything from it but I can boot everything from BackTrack 4. I tried to just combine both "menu.lst" files and change the path to where the files and boot information to run the programs from Falcon's where located. This attempt failed miserably.

I was able to put Falcon's on a different flash drive and it booted just fine w/o any problems. I don't want to carry around 2 flash drives with me knowing that what I'm trying to do is possible with just 1 flash drive.

Can anyone shed some light on this and take pity on this n00b elite?

----------------
PS: I attached my menu.lst as it is right now, it's not in the order I want it in because of my testing attempts.
----------------

Muitissimo Obrigado!

---

### Post by Leppie on 2010-02-02
hi and welcome to the community,

there's no attachment...
anyways, for analysis it would be more usefull if you would [download and run meierfra's script]("http://sourceforge.net/projects/bootinfoscript/") and post the generated RESULTS.txt.

---

### Post by EG-Zero on 2010-02-02
Ah, obrigado Leppie. I swear I thought I attached my menu.lst file.
Below are the results from the script:

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda
 => Grub 0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst /menu.lst

sdb2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /etc/fstab

hdc: _________________________________________________________________________

    File system:       iso9660
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /boot/grub/menu.lst

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 1073 MB, 1073741824 bytes
128 heads, 32 sectors/track, 512 cylinders, total 2097152 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000000

Partition  Boot         Start           End          Size  Id System

Invalid MBR Signature found


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 16.0 GB, 16039018496 bytes
64 heads, 32 sectors/track, 15296 cylinders, total 31326208 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2d5545fa

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32    29,876,223    29,876,192   b W95 FAT32
/dev/sdb2          29,878,272    31,326,207     1,447,936  83 Linux


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/hdc                                                iso9660    BT4                           
/dev/loop0                                              squashfs                                 
/dev/sdb1        4B63-A324                              vfat       ALAN                          
/dev/sdb2        93a0c11f-5de9-49a0-a5ef-e77a400abc7a   ext3       casper-rw                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

rootfs           /                        rootfs     (rw)
/dev/hdc         /media/cdrom0            iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/ALAN              vfat       (rw,nosuid,nodev,noatime,uhelper=hal,flush,uid=0,utf8,shortname=lower)
/dev/sdb2        /media/casper-rw         ext3       (rw,nosuid,nodev,uhelper=hal,data=ordered)


=========================== sdb1/boot/grub/menu.lst: ===========================

# By default, boot the first entry.
default 4 

# Boot automatically after 10 secs.
timeout 10

splashimage=/boot/grub/bt4.xpm.gz
foreground e3e3e3
background 303030

title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet vga=0x317 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title Boot First Hard Drive (hd0)
rootnoverify (hd0)
chainloader (hd0)+1

title Find and Start Windows XP\n\nAttempts to locate and load Windows even with a damaged boot sector
find --set-root /f4_ubcd/ntldr
chainloader /f4_ubcd/ntldr

title Find and Start Windows Vista/7\n\nAttempts to locate and load Windows even with a damaged boot sector
find --set-root /f4_ubcd/bootmgr
chainloader /f4_ubcd/bootmgr

title Kon-Boot v1.1\n\nLog into Windows with blank password; bypass login without breaking it
map --mem /f4_ubcd/images/konboot.img (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)

title MiniXP "Enhanced"
title Memtest86+ v2.11\n\nTest basic system functionality by stress-testing RAM, FSB, and CPU
map --mem /f4_ubcd/images/memtest.img (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)
fallback 1
find --set-root /f4_ubcd/HBCD/XPLOADER.BIN
chainloader /f4_ubcd/HBCD/XPLOADER.BIN

title Hiren's BootCD 9.9
map --mem /f4_ubcd/HBCD/boot.img (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)

title ERD Commander XP  (WinXP)\n\nA RAM-based modification of ERD Commander 5.0, with highly specialized tools for Windows XP
fallback 1
find --set-root /f4_ubcd/ERD5/XPLOADER.BIN
chainloader /f4_ubcd/ERD5/XPLOADER.BIN

title ERD Commander VISTA (Vista)\n\nMicrosoft Diagnostics and Recovery Toolset 6.0 for Vista
fallback 1
find --set-root /f4_ubcd/BOOT/bootmgr
chainloader /f4_ubcd/BOOT/bootmgr

title Dell System Restore MBR Repair Utility\n\nHelps you restore a Dell MBR and access restore partition w/ Ctrl+F11
fallback 1
map --mem /f4_ubcd/images/dell.img (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)

title Windows Recovery Console
fallback 1
find --set-root /f4_ubcd/CMDC/SETUPLDR.BIN
chainloader /f4_ubcd/CMDC/SETUPLDR.BIN
#####################################################################
# write string "cmdcons" to memory 0000:7C03 in 2 steps:
#####################################################################
# step 1. Write 4 chars "cmdc" at 0000:7C03
write 0x7C03 0x63646D63
# step 2. Write 3 chars "ons" and an ending null at 0000:7C07
write 0x7C07 0x00736E6F
================================ sdb1/menu.lst: ================================

splashimage=/images/bg.xpm.gz
foreground=FFFFFF
background=000000

default     6

title Boot First Hard Drive (hd0)
rootnoverify (hd0)
chainloader (hd0)+1

title Boot First HDD's Boot Sector
root (hd0,0)
chainloader (hd0,0)+1

title Find and Start Windows XP\n\nAttempts to locate and load Windows even with a damaged boot sector
find --set-root /ntldr
chainloader /ntldr

title Find and Start Windows Vista/7\n\nAttempts to locate and load Windows even with a damaged boot sector
find --set-root /bootmgr
chainloader /bootmgr

title Memtest86+ v2.11\n\nTest basic system functionality by stress-testing RAM, FSB, and CPU
map --mem /images/memtest.img (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)

title Kon-Boot v1.1\n\nLog into Windows with blank password; bypass login without breaking it
map --mem /images/konboot.img (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)

title Hiren's XP BootCD 9.9 "Enhanced"
fallback 1
find --set-root /HBCD/XPLOADER.BIN
chainloader /HBCD/XPLOADER.BIN

title Hiren's DOS BootCD 9.9
map --mem /HBCD/boot.img (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)

title MS DaRT / ERD Commander 5.0 (WinXP)\n\nA RAM-based modification of ERD Commander 5.0, with highly specialized tools for Windows XP
fallback 1
find --set-root /ERD5/XPLOADER.BIN
chainloader /ERD5/XPLOADER.BIN

title MS DaRT / ERD Commander 6.0 (Vista)\n\nMicrosoft Diagnostics and Recovery Toolset 6.0 for Vista
fallback 1
find --set-root /BOOT/bootmgr
chainloader /BOOT/bootmgr

title Dell System Restore MBR Repair Utility\n\nHelps you restore a Dell MBR (blue "www.dell.com") and access restore partition w/ Ctrl+F11
fallback 1
map --mem /images/dell.img (fd0)
map --hook
chainloader (fd0)+1
rootnoverify (fd0)

title Windows Recovery Console
fallback 1
find --set-root /CMDC/SETUPLDR.BIN
chainloader /CMDC/SETUPLDR.BIN
#####################################################################
# write string "cmdcons" to memory 0000:7C03 in 2 steps:
#####################################################################
# step 1. Write 4 chars "cmdc" at 0000:7C03
write 0x7C03 0x63646D63
# step 2. Write 3 chars "ons" and an ending null at 0000:7C07
write 0x7C07 0x00736E6F



=================== sdb1: Location of files loaded by Grub: ===================


   1.5GB: boot/grub/menu.lst
   1.5GB: boot/grub/stage2
    .0GB: boot/initrd800.gz
    .0GB: boot/initrdfr.gz
    .0GB: boot/initrd.gz
    .0GB: boot/vmlinuz
   3.2GB: menu.lst

=============================== sdb2/etc/fstab: ===============================

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0

=========================== hdc/boot/grub/menu.lst: ===========================

# By default, boot the first entry.
default 0

# Boot automatically after 30 secs.
timeout 30

splashimage=/boot/grub/bt4.xpm.gz
foreground e3e3e3
background 303030

title                Start BackTrack FrameBuffer (1024x768)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x317
initrd                /boot/initrd.gz

title                Start BackTrack FrameBuffer (800x600)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw quiet vga=0x314
initrd                /boot/initrd800.gz

title                Start BackTrack Forensics (no swap)
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent rw vga=0x317
initrd                /boot/initrdfr.gz

title                Start BackTrack in Safe Graphical Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper xforcevesa rw quiet 
initrd                /boot/initrd.gz

title                Start Persistent Live CD
kernel                /boot/vmlinuz BOOT=casper boot=casper persistent rw quiet 
initrd                /boot/initrd.gz

title                Start BackTrack in Text Mode
kernel                /boot/vmlinuz BOOT=casper boot=casper nopersistent textonly rw quiet
initrd                /boot/initrd.gz

title                Start BackTrack Graphical Mode from RAM
kernel                /boot/vmlinuz BOOT=casper boot=casper toram nopersistent rw quiet 
initrd                /boot/initrd.gz

title                Memory Test
kernel                /boot/memtest86+.bin

title                Boot the First Hard Disk
root                (hd0)
chainloader +1

==================== hdc: Location of files loaded by Grub: ====================


    .0GB: boot/grub/menu.lst
    .0GB: boot/initrd800.gz
    .0GB: boot/initrdfr.gz
    .0GB: boot/initrd.gz
    .0GB: boot/vmlinuz
--------------------------------------------------------

I can't analyze this at all, its 100x more complicated than a boot.ini file.

---

