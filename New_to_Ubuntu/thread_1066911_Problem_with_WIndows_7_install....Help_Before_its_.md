---
title: "Problem with WIndows 7 install....Help Before its too late"
date: 2009-02-11
forum: New to Ubuntu
---

### Post by leenyx64 on 2009-02-11
So I followed the tutorial for [dual booting ubuntu/ win7 wiht ubuntu installed first]("http://ubuntuforums.org/showthread.php?t=1035999").  I repartitioned my hdd with a new ntfs partition for win7 and a fat32 for shared files between the two os. I installed win7 on the ntfs partition and reinstalled grub then edited grub to list win7.  heres my problem.  In gparted it say that the ntfs partition that win7 is on..... 

/dev/sda2 

When i edit the grub boot list i pointed to (hd0,2) and the when i try to boot into win7 i get

"Starting up..."

and it just hangs.  Nothing.  So i edited grub and point to (hd0,0) and got

"Error 13: Invalid or unsupported executable format"

Then i pointed to (hd0,1) and i get

"BOOTMGR missing
Press Ctrl+Alt+Del to restart"

i have tried to reinstall win7 and still nothing.  I am almost postive that pointing to (hd0,2) is correct however its not working.  Has anyone had this problem or know where i messed up. any help would be very appreciated.

---

### Post by jbrown96 on 2009-02-11
(hd0,1) is what you should be using. On almost all computer platforms, numbering starts at zero and goes up.

/dev/sda1 == (hd0,0)
/dev/sda2 == (hd0,1)
/dev/sdb1 == (hd1,0)

---

### Post by leenyx64 on 2009-02-11
okay that makes sense. then does anyone know what 

"BOOTMGR missing
Press Ctrl+Alt+Del to restart"

means and how to fix it.

---

### Post by caljohnsmith on 2009-02-11
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by leenyx64 on 2009-02-11
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 63. But according to the info from fdisk, 
                       sda3 starts at sector 262871595.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000de27c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   221,905,844   221,905,782  83 Linux
/dev/sda2         221,906,944   262,871,039    40,964,096   7 HPFS/NTFS
/dev/sda3         262,871,595   468,519,659   205,648,065   b W95 FAT32
/dev/sda4         468,519,660   488,392,064    19,872,405   5 Extended
/dev/sda5         468,519,723   488,392,064    19,872,342  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="c54287b0-9d34-4d7d-9564-963918f15eeb" TYPE="ext3" 
/dev/sda2: UUID="D43CAD213CAD001A" TYPE="ntfs" 
/dev/sda3: LABEL="Shared" UUID="4992-6116" TYPE="vfat" 
/dev/sda5: UUID="4cd59d5d-e5b4-43c1-abcc-c9d8ea50f6d9" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/shuttle/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=shuttle)

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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=c54287b0-9d34-4d7d-9564-963918f15eeb ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c54287b0-9d34-4d7d-9564-963918f15eeb

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

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c54287b0-9d34-4d7d-9564-963918f15eeb
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c54287b0-9d34-4d7d-9564-963918f15eeb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c54287b0-9d34-4d7d-9564-963918f15eeb
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c54287b0-9d34-4d7d-9564-963918f15eeb ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		c54287b0-9d34-4d7d-9564-963918f15eeb
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c54287b0-9d34-4d7d-9564-963918f15eeb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		c54287b0-9d34-4d7d-9564-963918f15eeb
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c54287b0-9d34-4d7d-9564-963918f15eeb ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c54287b0-9d34-4d7d-9564-963918f15eeb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c54287b0-9d34-4d7d-9564-963918f15eeb ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c54287b0-9d34-4d7d-9564-963918f15eeb
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c54287b0-9d34-4d7d-9564-963918f15eeb ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c54287b0-9d34-4d7d-9564-963918f15eeb
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title windows 7 beta (Loader)
root (hd0,2)
savedefault
makeactive
chainloader +1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda1 :
UUID=c54287b0-9d34-4d7d-9564-963918f15eeb / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda5 :
UUID=4cd59d5d-e5b4-43c1-abcc-c9d8ea50f6d9 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0

=================== sda1: Location of files loaded by Grub: ===================


 113.2GB: boot/grub/menu.lst
 113.4GB: boot/grub/stage2
 113.3GB: boot/initrd.img-2.6.27-11-generic
 113.2GB: boot/initrd.img-2.6.27-7-generic
 113.3GB: boot/initrd.img-2.6.27-9-generic
 113.3GB: boot/vmlinuz-2.6.27-11-generic
 113.3GB: boot/vmlinuz-2.6.27-7-generic
 113.3GB: boot/vmlinuz-2.6.27-9-generic
 113.3GB: initrd.img
 113.3GB: initrd.img.old
 113.3GB: vmlinuz
 113.3GB: vmlinuz.old
```

---

### Post by leenyx64 on 2009-02-11
Find anything?

---

### Post by caljohnsmith on 2009-02-11
Leenyx64, please be patient and observe the forum rules of not bumping your thread more than once every 24 hours. About your Win7 problem, it looks like Win7 put its boot files in your sda3 partition even though you installed Win7 to sda2. I would suggest doing the following:
```
sudo mkdir /media/sda2 /media/sda3
sudo mount /dev/sda2 /media/sda2
sudo mount /dev/sda3 /media/sda3
sudo mv /media/sda3/bootmgr /media/sda3/Boot /media/sda2
```
Also, change your Grub's menu.lst to use (hd0,1) in the Windows 7 entry. Next boot your Windows 7 install CD, go to the command line, and do:
```
bootrec /rebuildbcd
```
If that completes successfully, try booting Win7 from Grub and let me know exactly what happens. If you have any problems please post:
```
sudo mount /dev/sda2 /media/sda2 && ls -l /media/sda2
```

---

### Post by leenyx64 on 2009-02-11
sorry about the bump Caljohnsmith. I followed your last post and it didn't work.  In the command prompt it said: 

volume does not contain recognized file system. Make sure all file system drivers are loaded and that volume is not corrupted.

the posting you needed is here:

```
total 524700
drwxrwxrwx 1 root root      4096 2009-02-11 07:49 Boot
-rwxrwxrwx 1 root root    377151 2008-12-12 23:03 bootmgr
drwxrwxrwx 1 root root         0 2008-12-12 21:07 Documents and Settings
drwxrwxrwx 1 root root         0 2008-12-13 00:15 PerfLogs
drwxrwxrwx 1 root root      4096 2008-12-12 21:07 ProgramData
drwxrwxrwx 1 root root      4096 2008-12-13 12:55 Program Files
drwxrwxrwx 1 root root      4096 2008-12-13 12:28 Program Files (x86)
drwxrwxrwx 1 root root         0 2009-02-11 18:39 $Recycle.Bin
drwxrwxrwx 1 root root         0 2009-02-11 06:22 System Volume Information
drwxrwxrwx 1 root root      4096 2008-12-12 21:07 Users
drwxrwxrwx 1 root root     16384 2009-02-11 07:57 Windows
drwxrwxrwx 1 root root         0 2009-02-11 07:49 $WINDOWS.~BT
drwxrwxrwx 1 root root         0 2009-02-11 07:49 $WINDOWS.~LS
drwxrwxrwx 1 root root      4096 2009-02-11 07:50 Windows.old
-rwxrwxrwx 1 root root 536870912 2009-02-11 07:38 WinPEpge.sys
```

thanks for the help

---

### Post by caljohnsmith on 2009-02-11
OK, while you are in Ubuntu do:
```
sudo sfdisk -A2 /dev/sda
```
Next, how about booting your Win7 Install CD again, go to the command line and do:
```
diskpart
```
And at the diskpart prompt try:
```
list volume
exit
```
Find the drive letter of your Win7 partition (probably will be "C"), and then do:
```
chkdsk /r C:
```
Replace "C" with the correct drive letter if necessary, and also run the chkdsk command as many times as it takes until it reports no errors. If that works OK, proceed with:
```
bcdedit /store C:\boot\bcd /set {default} osdevice boot
bcdedit /store C:\boot\bcd /set {default} device boot
bcdedit /store C:\boot\bcd /set {default} path \Windows\system32\winload.exe
bcdedit /store C:\boot\bcd /set {bootmgr} device boot
bcdedit /store C:\boot\bcd /set {memdiag} device boot
```
And again replace "C" if necessary. Also, please make sure to get the above commands exactly right without any typos. If they all complete successfully, next do:
```
bcdedit /store C:\boot\bcd /deletevalue  {default} detecthal 
bcdedit /store C:\boot\bcd /deletevalue  {default} winpe
bcdedit /store C:\boot\bcd /deletevalue  {default} ems
```
If any or all of those commands give an "element not found" warning, that's OK. After you've done all the above commands, try booting Win7 from Grub again and let me know how far you get.

**CREDITS**: Many thanks to forum member meierfra for figuring out all the Win7 bcdedit commands.

---

### Post by leenyx64 on 2009-02-11
i tried it once and it worked but when i booted into windows it said for me to reinstall window 7. 

So deleted the partition in gparted and reinstalled from scratch. I did this whole thing all over again.  When i get to the 

```
chkdsk /r C:
```

at the end it says 

> Failed to transfer logged messages to the event log with status 50

then i ran

```
bcdedit /store C:\boot\bcd /set {default} osdevice boot
```

and it reads

> The boot configuration data store could not be opened. The system cannot find the file specified.

is this a sign that i should just dual boot xp and forget about win7?

---

### Post by caljohnsmith on 2009-02-11
Since Windows 7 is a new install, can you reinstall it, but first use gparted (System > Admin > Partition Editor) to reformat that partition? Or does the Win 7 CD give you the option to format the sda2 partition before installing? I would try that, because there seems to be something about that NTFS partition that Windows 7 does not like. If you do format the partition with gparted, before you install Win 7 again I would suggest running "chkdsk /r" from the Win 7 CD on the newly formatted partition to see what it returns. Let me know how that goes.

---

### Post by leenyx64 on 2009-02-11
I didn't format the partition with gparted.  I tried to but gparted didn't give me the option to partition in NTFS.  So i just deleted the partition and left it unallocated.   Then in windows 7 installation i pointed the install to the unallocated partition. was this horribly wrong?  If this was the problem i feel like an idiot.

---

### Post by sneeks on 2009-02-11
gparted didnt give you the option for ntfs???
was this the system gparted or the live cd g parted?
as the option should have been there.

---

### Post by leenyx64 on 2009-02-11
system gparted.  I saw NTFS but was unable to select it.  I dont know why.  If that sounds to be the issue i will try to figure it out when i get back to my computer.  thanks for the help.  I will reply again tonight when i figure out how to format the partition.  if you have anymore adivce i would appreciate it.

---

### Post by caljohnsmith on 2009-02-11
How about doing the following from a terminal:
```
apt-cache policy ntfsprogs
```
If it says that package is not installed, then do:
```
sudo apt-get install ntfsprogs
```
Then try running gparted again, and see if it will let you format sda2 as NTFS. If not, from the terminal try:
```
sudo mkntfs -v /dev/sda2
```
And please post the output.

---

### Post by leenyx64 on 2009-02-12
everything works now:P Thanks a lot...

---

### Post by sunbear on 2010-01-08
I'm having a very similar problem to the original poster and would really appreciate some help. 

I am getting the **"Starting up ..."** message followed by the system hanging whenever I try to boot Windows 7 x64 from my machine.

Like the original poster I have set up a dual boot of Ubuntu 9.04 64-bit and Window 7 Ultimate 64-bit. Unlike the original poster though I have installed both OSes on a dmraid (fakeraid) RAID 0 volume (see [https://wiki.ubuntu.com/FakeRaidHowto](https://wiki.ubuntu.com/FakeRaidHowto)).

I can get Ubuntu to boot fine, but Windows does not. Unfortunately I boot_info_script046.sh does not seem to work on my setup. It seems to get stuck so I'm guessing that it wasn't developed to gather diagnostic info for fakeraid volumes.

Here's how my volume is partitioned:
fdisk -l -u /dev/mapper/isw_bihfbccbec_RAID0Volume
```

Disk /dev/mapper/isw_bihfbccbec_RAID0Volume: 600.1 GB, 600132812800 bytes
255 heads, 63 sectors/track, 72961 cylinders, total 1172134400 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d3b0c

                                 Device Boot      Start         End      Blocks   Id  System
/dev/mapper/isw_bihfbccbec_RAID0Volume1   *        2048   629146623   314572288    7  HPFS/NTFS
/dev/mapper/isw_bihfbccbec_RAID0Volume2       629148672  1136659456   253755392+  83  Linux
/dev/mapper/isw_bihfbccbec_RAID0Volume3      1138564097  1172118464    16777184    5  Extended
/dev/mapper/isw_bihfbccbec_RAID0Volume5      1138564172  1172118464    16777146+  82  Linux swap / Solaris

```

Here's some output from parted too:
```
Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_bihfbccbec_RAID0Volume: 1172134400s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start        End          Size        Type      File system     Flags
 4      2048s        629146623s   629144576s  primary   ntfs
 1      629148672s   1136659456s  507510785s  primary   ext3
 2      1138564097s  1172118464s  33554368s   extended
 5      1138564172s  1172118464s  33554293s   logical   linux-swap(v1)
```

Here's my menu.lst:
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
timeout	10	

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
# Windows 7 
#
title Windows 7 
root (hd0,0)
makeactive
chainloader	+1

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
# kopt=root=/dev/mapper/isw_bihfbccbec_RAID0Volume1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=quiet splash nohz=off

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

title		Ubuntu 9.04, kernel 2.6.28-17-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.28-17-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro quiet splash nohz=off 
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-17-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.28-17-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro  single
initrd		/boot/initrd.img-2.6.28-17-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.28-16-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro quiet splash nohz=off 
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.28-16-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.28-16-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro  single
initrd		/boot/initrd.img-2.6.28-16-generic

title		Ubuntu 9.04, kernel 2.6.27-15-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-15-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro quiet splash nohz=off 
initrd		/boot/initrd.img-2.6.27-15-generic

title		Ubuntu 9.04, kernel 2.6.27-15-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-15-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro  single
initrd		/boot/initrd.img-2.6.27-15-generic
title		Ubuntu 9.04, kernel 2.6.27-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro quiet splash nohz=off 
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.27-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-14-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro quiet splash nohz=off 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.27-11-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-11-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 9.04, kernel 2.6.27-9-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro quiet splash nohz=off 
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 9.04, kernel 2.6.27-9-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-9-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/isw_bihfbccbec_RAID0Volume2 ro quiet splash nohz=off 
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, kernel 2.6.27-7-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.27-7-generic root=/dev/mapper/isw_bihfbccbec_R
AID0Volume2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 9.04, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST


```

Many thanks

---

### Post by sunbear on 2010-01-09
Sorry, false alarm, I managed to get things working. My grub setup wasn't the problem at all. The key thing I was missing was that you have to let Windows 7 reboot a couple of times before it is fully installed. I was only allowing one reboot, then moving straight on to setup Grub. It seems that the windows boot configuration isn't fully operational until it has booted a couple of times through its own booting process first.

---

