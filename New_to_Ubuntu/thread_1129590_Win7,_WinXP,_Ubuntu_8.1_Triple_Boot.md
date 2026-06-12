---
title: "Win7, WinXP, Ubuntu 8.1 Triple Boot"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Zopiac on 2009-04-18
I've seen a few posts concerning Win7, but nothing that concerns this, quite. Well, I installed Windows 7, and it was working great. I then took a bunch of that single partition and made it into Ubuntu. even just then i couldn't boot into Win7, but i didn't do anything about it. i later made two more partitions, one for a generic NTFS storage area, and one for Windows XP. When i boot up GRUB gives me the typical ubuntu choices, as well as Windows Vista/Longhorn. However, selecting this brings me to WinXP. How do i triple boot?

My menu.lst:

```
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=76422306-dd93-438d-886e-c89556b48aba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=76422306-dd93-438d-886e-c89556b48aba

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		76422306-dd93-438d-886e-c89556b48aba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=76422306-dd93-438d-886e-c89556b48aba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		76422306-dd93-438d-886e-c89556b48aba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=76422306-dd93-438d-886e-c89556b48aba ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		76422306-dd93-438d-886e-c89556b48aba
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

```
sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc85a3fbe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4714    37865173+   7  HPFS/NTFS
/dev/sda2            4715        8161    27688027+  83  Linux
/dev/sda3           11134       19390    66324352+   7  HPFS/NTFS
/dev/sda4            8162       11133    23872590    7  HPFS/NTFS

```

i believe sda1 is win7, sda2 is ubuntu, sda3 is winxp, and sda4 is the storage partition.

If more information is needed, just ask :) and thanks in advance for any help provided!

---

### Post by tjwoosta on 2009-04-18
change this part 
```

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

make it so it says

```

title		Windows 7
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


then add this entry underneath that


```

title		Windows XP
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

---

### Post by leef on 2009-04-18
you could try adding this to he end of the file

```

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda3
title		Windows Test
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

and see if that works, I noticed that fdisk says sda3 doesn't have he boot flag set but I'm no sure that will make a difference but here is no harm in trying.

Edit: tjwoosta beat me to it

---

### Post by meierfra. on 2009-04-18
> then took a bunch of that single partition and made it into Ubuntu. even just then i couldn't boot into Win 7 

You should have been able to boot into Win 7 at this stage. Since not, it means your Win 7 boot loader needs fixing.
> and one for Windows XP

Installing XP actually replaces the Win 7 boot loader by the XP boot loader. So there is some more work to do.

Anyway, in order to get a clearer picture of your setup, I suggest to boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

---

### Post by Zopiac on 2009-04-18
> **meierfra. said:**
> You should have been able to boot into Win 7 at this stage. Since not, it means your Win 7 boot loader needs fixing.


Installing XP actually replaces the Win 7 boot loader by the XP boot loader. So there is some more work to do.

Anyway, in order to get a clearer picture of your setup, I suggest to boot into  Ubuntu  and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it.

well, downloaded to home folder (deleted my desktop folder a long time ago; i dont use the desktop except for pretty images :P ) and i know about the code function; i used it in my first post, but anyways:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda3': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda3 sda3 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda3 sda3 ntfs-3g force 0 0
$LogFile indicates unclean shutdown (0, 1)
Failed to mount '/dev/sda3': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda3 sda3 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda3 sda3 ntfs-3g force 0 0

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xc85a3fbe

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    75,730,409    75,730,347   7 HPFS/NTFS
/dev/sda2          75,730,410   131,106,464    55,376,055  83 Linux
/dev/sda3         178,851,645   311,500,349   132,648,705   7 HPFS/NTFS
/dev/sda4         131,106,465   178,851,644    47,745,180   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="32F74A85096E3659" TYPE="ntfs" 
/dev/sda2: UUID="76422306-dd93-438d-886e-c89556b48aba" TYPE="ext3" 
/dev/sda3: UUID="4ACD70BF1074DF54" TYPE="ntfs" 
/dev/sda4: UUID="4361D8DF02E75592" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/zopiac/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=zopiac)


================================ sda1/boot.ini: ================================

[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /usepmtimer

=========================== sda2/boot/grub/menu.lst: ===========================

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=76422306-dd93-438d-886e-c89556b48aba ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=76422306-dd93-438d-886e-c89556b48aba

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

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		76422306-dd93-438d-886e-c89556b48aba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=76422306-dd93-438d-886e-c89556b48aba ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		76422306-dd93-438d-886e-c89556b48aba
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=76422306-dd93-438d-886e-c89556b48aba ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		76422306-dd93-438d-886e-c89556b48aba
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows 7
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title		Windows XP
root		(hd0,2)
savedefault
makeactive
chainloader	+1

=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=76422306-dd93-438d-886e-c89556b48aba /               ext3    relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda2: Location of files loaded by Grub: ===================


  39.0GB: boot/grub/menu.lst
  39.0GB: boot/grub/stage2
  39.1GB: boot/initrd.img-2.6.27-7-generic
  39.1GB: boot/vmlinuz-2.6.27-7-generic
  39.1GB: initrd.img
  39.1GB: vmlinuz
```

> **tjwoosta said:**
> change this part 
```

title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

make it so it says

```

title		Windows 7
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


then add this entry underneath that


```

title		Windows XP
root		(hd0,2)
savedefault
makeactive
chainloader	+1

```

I tried this, but it didnt change anything, which is way whack :/ in fact, once i did this it took a considerably longer time to load the GRUB...

---

### Post by meierfra. on 2009-04-18
> know about the code function; i used it in my first post,
Sorry about that. I used my standard text, but usually I remove the "code tags" part, if somebody already used the code tags.


> Once i did this it took a considerably longer time to load the GRUB... 
Adding the Windows item does not have any influence on how long Grub takes to load.   


Anyway, first you need to take  care of the " indicates unclean shutdown".  Boot into XP and shutting down XP (don't hibernate).

Then boot into Ubuntu

Step 1 Move the XP boot files from the Win 7 partition to the XP partition.

```
sudo mkdir /mnt/{XP,Win}
sudo mount /dev/sda1 /mnt/Win
sudo mount /dev/sda3 /mnt/XP
cd /mnt/Win
mv boot.ini ntldr NTDETECT.COM /mnt/XP
```

If mounting XP failed,   boot from your XP or Win 7 CD and run "chdsk /r C:", but replace "C:" by the drive letter of your XP partition.
Then try again.

Step 2 Fix the boot sector of your XP and Win 7 partition.

Boot from the Win 7 DVD.  Select "Repair Computer" and then "Command Prompt". Type 

```
diskpart
list volume 
exit
```

to determine the drive letters of the  XP and  Win 7 partition and your DVD drive. In the following I assume that Win 7 is "C", XP is "D" and the DVD drive is "E". If this is not the case you will have to adjust the instructions accordingly.

Type

```
E:\boot\bootsect.exe  /nt52 D: /force

E:\boot\bootsect.exe  /nt60 C:  /force
```

Type exit and select "StartUp Repair".

Reboot and see whether you can boot into all your OSs
If booting XP or Win 7 fails, report any error messages. Also run the boot_info_script again and post the new RESULTS.txt (it might be called RESULTS1.txt)

---

### Post by Zopiac on 2009-04-19
> **meierfra. said:**
> Adding the Windows item does not have any influence on how long Grub takes to load.   

well, i dont know why, but it did. whether that was the case or not, it took longer after the addition.
> **meierfra. said:**
> Anyway, first you need to take  care of the " indicates unclean shutdown".  Boot into XP and shutting down XP (don't hibernate).

Then boot into Ubuntu

Step 1 Move the XP boot files from the XP partition to the Win 7 partition.

```
sudo mkdir /mnt/{XP,Win}
sudo mount /dev/sda1 /mnt/Win
sudo mount /dev/sda3 /mnt/XP
cd /mnt/Win
mv boot.ini ntldr /NTDETECT.COM /mnt/XP
```

If mounting XP failed,   boot from your XP or Win 7 CD and run "chdsk /r C:", but replace "C:" by the drive letter of your XP partition.
Then try again.

well i have about half a gig of space on each of the windows partitions xD so it'll take a while to do this...but i will get right on it :)

Edit: er, i skimmed it, and thought you meant the C:\Windows\ directory... my bad :P should work out fine, then.

---

### Post by meierfra. on 2009-04-19
> so it'll take a while to do this

???? You only will move three files totaling 270kb.


Oops. Didn't see your edit.

---

### Post by Zopiac on 2009-04-19
I followed step one, but when you tell me to input:

```
mv boot.ini ntldr /NTDETECT.COM /mnt/XP
```

```
mv: cannot stat `boot.ini': No such file or directory
mv: cannot stat `ntldr': No such file or directory
mv: cannot stat `/NTDETECT.COM': No such file or directory
```

Also, i looked ahead and read:

> Step 2 Fix the boot sector of your XP and Win 7 partition.

Boot from the Win 7 DVD. Select "Repair Computer" and then "Command Prompt".

Well, i downloaded an .iso and installed it using Daemon Tools from within XP (which i had before installing Win7)...not exactly sure how i would accomplish this?

---

### Post by meierfra. on 2009-04-19
> /NTDETECT.COM

This is supposed to be "NTDETECT.COM" (no backslash). Sorry about that.

But the other two files should be there.  Did you leave out the "cd /mnt/Win"?

Did you get any errors from  the "mount" commands?

Post the output of

```
ls /mnt/Win
```

---

### Post by Zopiac on 2009-04-19
```
zopiac@zopiac-desktop:~$ cd /mnt/Win
zopiac@zopiac-desktop:/mnt/Win$ mv boot.ini ntldr /NTDETECT.COM /mnt/XP
mv: cannot stat `/NTDETECT.COM': No such file or directory
zopiac@zopiac-desktop:/mnt/Win$ 
zopiac@zopiac-desktop:/mnt/Win$ mv boot.ini ntldr /NTDETECT.COM /mnt/XP
mv: cannot stat `boot.ini': No such file or directory
mv: cannot stat `ntldr': No such file or directory
mv: cannot stat `/NTDETECT.COM': No such file or directory
```

that is it all...

ls /mnt/Win:

```

zopiac@zopiac-desktop:/mnt/Win$ ls /mnt/Win
autoexec.bat            IO.SYS         RECYCLER
Boot                    MSDOS.SYS      System Volume Information
Boot.BAK                NTDETECT.COM   tmp
Boot.ini.saved          OgreSDK        UnrealTournament
bootmgr                 PerfLogs       Users
BOOTSECT.BAK            Plugins        UT2004
config.sys              ProgramData    window.blend
Documents and Settings  Program Files  window.blend1
EA_Keygen_FFF           Python26       Windows
Fallout.3-RELOADED      Recovery
hiberfil.sys            $Recycle.Bin
```

---

### Post by meierfra. on 2009-04-19
Thats strange. You still had whose files when you run the boot_info_script:

> Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM


What is the output of 

```
ls /mnt/XP
```

---

### Post by meierfra. on 2009-04-19
> i downloaded an .iso 

Do you still have that .iso?  If yes it would be easiest if you burn it to a DVD. 

If not, we'll have to revise plans. Although to get Win 7 to boot, you might have to download and  burn a Vista/Win 7 rescue CD.

---

### Post by Zopiac on 2009-04-19
> **meierfra. said:**
> Thats strange. You still had whose files when you run the boot_info_script:



What is the output of 

```
ls /mnt/XP
```

```
zopiac@zopiac-desktop:/mnt/Win$ ls /mnt/XP
boot.ini                pagefile.sys   Reference.html
Documents and Settings  Plugins        Sierra
DSPdsblr.exe            Program Files  System Volume Information
Nexon                   Python25       WINDOWS
ntldr                   RECYCLER
zopiac@zopiac-desktop:/mnt/Win$ 
```

---

### Post by meierfra. on 2009-04-19
It seems "boot.ini" and "ntldr" already  got moved.

So  do

```
sudo mv /mnt/Win/NTDETECT.COM /mnt/XP

```

and you should be done with Step 1.

---

### Post by Zopiac on 2009-04-19
> **meierfra. said:**
> and you should be done with Step 1.

now how do i accomplish step 2 without the dvd... :\
well im going to continue this later; going to bed. Thanks for all of your help so far, though :)

and if nothing else, i could probably borrow a win7 disk from someone eventually...or, even better, get a dvd-rw drive :)

---

### Post by meierfra. on 2009-04-19
```
now how do i accomplish step 2 without the dvd
```

Do  this in  a terminal in Ubuntu

```

sudo dd if=/dev/sda1 of=XPBoot count=9
sudo dd if=/dev/sda3 of=WinBoot count=9
sudo dd if=XPBoot of=/dev/sda3 bs=1 seek=80 skip=80
sudo dd if=WinBoot of=/dev/sda1 bs=1 seek=80 skip=80
```

Be very careful with the "dd" commands. If any of them run for more than just a couple of seconds,  stop the process with "Ctrl+C".

Reboot and try to boot into XP and Win7.  Booting into XP should work. But I'm not sure what will happen  if your try to boot Win7.

---

### Post by Zopiac on 2009-04-19
> **meierfra. said:**
> ```
now how do i accomplish step 2 without the dvd
```

Do  this in  a terminal in Ubuntu

```

sudo dd if=/dev/sda1 of=XPBoot count=9
sudo dd if=/dev/sda3 of=WinBoot count=9
sudo dd if=XPBoot of=/dev/sda3 bs=1 seek=80 skip=80
sudo dd if=WinBoot of=/dev/sda1 bs=1 seek=80 skip=80
```

Be very careful with the "dd" commands. If any of them run for more than just a couple of seconds,  stop the process with "Ctrl+C".

Reboot and try to boot into XP and Win7.  Booting into XP should work. But I'm not sure what will happen  if your try to boot Win7.

All right...windows XP works fine, and windows 7 booted up the first time i tried, but it gave me a BSOD before long. tried again, and it just restarts a little while after hitting the Loading Windows screen, or whatever it says. it then gives me the option when i boot into it again to go into a repair mode, but after loading for a little bit BSODs me...

However, when i was searching for a solution earlier i did see someone with this sort of problem, it crashing while loading. gonna look for that again...

I can feel closer to success! oh, and btw if you hadn't noticed, you used [code] params insteam of [quote] :P

---

### Post by Zopiac on 2009-04-19
[This]("http://ubuntuforums.org/showthread.php?t=1037421") was the thread i was talking about that i had seen. I tried what was listed in the first post, though changing 

```
title Microsoft Windows XP Professional
root (hd1,0)
chainloader +1
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
```

to

```
title Windows 7
root (hd0,0)
chainloader +1
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
```

and booted windows 7 (although the fix was for winxp) and it gave me an error about boot settings. is there anything i should do to those last two lines? is there a different thing i can do similar that is for win7?

---

### Post by meierfra. on 2009-04-19
The correct entry for Win 7 is

> title Windows 7
root (hd0,0)
chainloader +1

The BSOD is a Windows problem. I only see two ways to fix your problem.


1) Get hold of a CDrom drive, burn a  Win 7 CD  or [Vista Rescue CD]("http://www.pcworld.com/downloads/file/fid,71039/description.html") and run "Start Up Repair"


2)  Reinstall Win 7 from your .iso file.


> Well, i downloaded an .iso and installed it using Daemon Tools from within XP (which i had before installing Win7)

I don't now anything about Daemon Tools. Could  Daemon  Tools be used the access the "Repair Console" on the iso file and run "Start Up Repair"?

---

