---
title: "System 2: Stage one. Pre-Dual Boot Guidence."
date: 2009-05-05
forum: New to Ubuntu
---

### Post by Mortus Pryde on 2009-05-05
I am getting ready to embark on the next leg of my Ubuntu journey and preparing to transition my main tower to Linux. This system is a fair bit more involved than my T42 so before I jump I would like some guidance. The less bumps with this machine the better. The following are the specs on my machine, and I am considering dual-booting XP and Jaunty. Please let me know anything I should be cautious of.

MotherBoard	MB IA Skt 775 915GA uATX GbE P5GD1-VM/S v1.04
CPU	        Intel LGA775 P4 530 3.00Ghz 800FSB 1MB HT
Memory	        Mem DDR1 PC3200 3GB
Hard Drive	SATA150 80GB
Hard Drive 2    PATA133 160GB
Hard Drive 3    SATA150 250GB
CD Rom	        HP DVD-RW
Video Card      BFG Nvidia GeForce 8800GT
Monitor Primary Samsung SyncMaster T220
Monitor Secondary Dell 1901FP
Capture Card    ATI TVWonder Elite
Remote          SnapStream FireFly
Network Cards	Integrated Intel Pro 10/100/1000 LAN
Sound Cards	Integrated Intel High Definition Audio
Operating Systems OS COA WIN XP Pro

Now the way I have it laid out. The 80GB is partitioned 50%/50% and intended to store the OS(s) and programs only. The 160GB will be for data storage (My Documents and Home Folder). The remaining 250GB hard drive is my PVR drive and stores all my recorded TV programs.

All that being said. How hard will it be to set up the home folder on a separate hard drive, can I do that during the install? Does the NVidia accelerate drivers support screens of differing resolution/formats as I have widescreen and standard format displays? And what would you recommend for a PVR/Playback/TV program, and will I have any issue with my ATI Tuner?

---

### Post by coffeeaddict22 on 2009-05-05
Hi,
Can't answer all you quesions, but if you're worried just boot off the live CD and have a play; you should be able to figure out pretty quickly what you're going to have problems with.
A separate /home is considered good form; you can (and should) put it on its own partition- it makes reinstalling a little less likely to fritz data that you can't be bothered backing up but might want in 6 months.  If you select manual install you can select separate partitions as mount points for any (or all!) of the root directories.

Different display resolutions should be fine.  The Nvidia drivers are getting superseded by open ones, but there's a bit of work going in so you'll have to play.  Try the live CD.

Can't comment on TV card.  You could have a look in the Multimedia forum; there's a comprehensive sound and video troubleshooter there too.

---

### Post by DJonsson2008 on 2009-05-05
a few suggestions.

* considering dual booting on
  a separate drive rather than
  dual partitioning.

* unplug the other drives before 
  initially installing ubuntu, 
  unless you are 300 percent
  comfortable with linux 
  formating/partitioning

* buy a 10$ HD at the flea market
  or dig an old one out of a box 
  and try that if you have any doubt 
  you want to use your current
  drives for this, and want to attempt
  a trial install. I think most distros
  will fit on a 20 to 40 gig drive, if
  not smaller.

error on the side of caution.

---

### Post by Mortus Pryde on 2009-05-05
Have to say I am pretty confident with most aspects of the installation process by this point and I figured moving the home folder/partition was in the installation phase so YAY! +1 for another thing Linux/Ubuntu did right with the setup procedure. You have to do this manually in Windows after installation.

I am just looking for guidence on any issue I may encounter regarding my hardware as to smooth the transition. I did run the live disk, my Dell LCD was not so happy, otherwise it did seem to function so I am hoping that perhaps the restricted driver will help with that.

---

### Post by Mortus Pryde on 2009-05-08
Okay I completed all my clean up, DiskClean, Defrag, and resized the existing partition on Disk 2, this is currently where MyDocuments and general "Data" files are stored. So now my drives look like the following:

Disk 1 = ~40GB - NTFS (Existing WinXP install), ~40GB - Unpartitioned
Disk 2 = ~80GB - NTFS (Existing WinXP data/documents), ~80GB - Unpartitioned
Disk 3 = 250GB - NTFS (Existing PVR Drive) <= Will eventually phase our for an ext4 partition/drive, but am leaving it intact at this juncture.

Now I am looking at partitioning my system as follows.

Disk 1 = ~40GB - NTFS (Existing WinXP install), 3GB - Swap, ~37GB - ext4 Root
Disk 2 = ~80GB - NTFS (Existing WinXP data/documents), ~80GB - ext4 Home
Disk 3 = 250GB - NTFS (Existing PVR Drive) <= Will eventually phase our for an ext4 partition/drive.

Is there anything glaringly wrong with how I intend to partition? Finally to get my certainty to 300%, will it still install as a dual boot if I manually create the partitions? If not how would I tell it that XP is still there and I want to boot to it?

Either way is there a way to make it so it boots into Windows automatically after a timeout?

---

### Post by durand on 2009-05-08
Everything looks fine. It would not have a timeout if you have more than one OS. There is one annoying problem with the boot menu. If you upgrade it in ubuntu, it will normally update the menu accordingly. However, if you change the menu and remove the "Other Operating Systems" line, then it will ignore the windows boot line in the next update. Just a heads up :)

---

### Post by Mortus Pryde on 2009-05-08
Thanks.

My reason for wanting the time out is to try and not inconvinience my habbits in the morning. The being that I wake up turn on my computer let it boot and settle while I bruch my tooth, hair, maybe grab some breakfast and sit down at my computer, so it would be nice if I could have Grub "Time out." after say 10 seconds and default to loading Windows for my dayly use.

Later when I am settled in on the machine with Ubuntu I want to switch this default to boot Linux, and then slowly wittle away at Windows as the funtions of its programs are replaced by Linux alternatives that I am confortable with, and hopefully eventually due away with Windows for the most part or all together.

---

### Post by durand on 2009-05-08
You can easily change the timeout value and the default boot option when you have ubuntu installed. Just open /boot/grub/menu.lst as root and it should be fairly self explanatory.

```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Mortus Pryde on 2009-05-08
Thanks again.

Hoping all goes well, I am wanting to reinstall my laptop and used a seperate root and home partition as it seems safer to reinstall that way, though granted does nothing for a hard drive failure.

---

### Post by Didius Falco on 2009-05-08
> **Mortus Pryde said:**
> Thanks.

My reason for wanting the time out is to try and not inconvinience my habbits in the morning. The being that I wake up turn on my computer let it boot and settle while I bruch my tooth, hair, maybe grab some breakfast and sit down at my computer, so it would be nice if I could have Grub "Time out." after say 10 seconds and default to loading Windows for my dayly use.

Later when I am settled in on the machine with Ubuntu I want to switch this default to boot Linux, and then slowly wittle away at Windows as the funtions of its programs are replaced by Linux alternatives that I am confortable with, and hopefully eventually due away with Windows for the most part or all together.

```
## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10
```

You can set the time before it boots the defaults entry by changing the timeout number to however many seconds you want it to wait.

```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default 0
```

You can set the default entry to your Windows boot by counting the entries in your menu.lst and changing the default  line above to the entry position number of your Windows boot. If you get a kernel update, you'll simply need top go and change it again to account for the extra entries.

BTW, the above is switched around from it's appearance in the actual menu.lst in order to answer you questions in the order asked.


Regards,

Didius

---

### Post by Mortus Pryde on 2009-05-09
Okay, did the install, major issue though! Ubuntu works great, but when I boot to Windows I get an NTLDR is missing error. The following is my boot info dump.

> ============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 in 
    partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /ubuntu/winboot/menu.lst /boot.ini /ntldr 
                       /NTDETECT.COM /ubuntu/winboot/wubildr.mbr

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sdb6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92600a7f

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   152,537,174   152,537,112   7 HPFS/NTFS
/dev/sda2         152,537,175   312,576,704   160,039,530   5 Extended
/dev/sda5         152,537,238   312,576,704   160,039,467  83 Linux


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8f278f27

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    81,915,434    81,915,372   7 HPFS/NTFS
/dev/sdb2          81,915,435   156,296,384    74,380,950   5 Extended
/dev/sdb5          81,915,498    87,779,159     5,863,662  82 Linux swap / Solaris
/dev/sdb6          87,779,223   156,296,384    68,517,162  83 Linux


Drive: sdc ___________________ _____________________________________________________

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x5c951cff

Partition  Boot         Start           End          Size  Id System

/dev/sdc1    *             63   488,392,064   488,392,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="F6CC57DBCC5794A9" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="3b7a8772-2aaf-4554-b68e-8d85174a3b0a" TYPE="ext4" 
/dev/sdb1: UUID="80A094DCA094D9CC" TYPE="ntfs" 
/dev/sdb5: UUID="efc3e72e-7b8a-4b05-a937-66eb7a4faa5f" TYPE="swap" 
/dev/sdb6: UUID="bc713823-6a51-467b-9ac0-32ab53fad0a3" TYPE="ext4" 
/dev/sdc1: UUID="3AECCBC1ECCB75A3" LABEL="Video" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sdb6 on / type ext4 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
/dev/sda5 on /home type ext4 (rw,relatime)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/mortus/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mortus)


======================== sdb1/ubuntu/winboot/menu.lst: ========================

debug off
hiddenmenu
default 0
timeout 0
fallback 1

title find /ubuntu/disks/boot/grub/menu.lst
	find --set-root --ignore-floppies /ubuntu/disks/boot/grub/menu.lst
	configfile /ubuntu/disks/boot/grub/menu.lst

title find /ubuntu/install/boot/grub/menu.lst
	fallback 2
	find --set-root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
	configfile /ubuntu/install/boot/grub/menu.lst

title find /menu.lst
	fallback 3
	find --set-root --ignore-floppies /menu.lst
	configfile /menu.lst

title find /boot/grub/menu.lst
	fallback 4
	find --set-root --ignore-floppies /boot/grub/menu.lst
	configfile /boot/grub/menu.lst

title find /grub/menu.lst
	fallback 5
	find --set-root --ignore-floppies /grub/menu.lst
	configfile /grub/menu.lst

title commandline
	commandline

title reboot
	reboot

title halt
	halt

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sdb6/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=bc713823-6a51-467b-9ac0-32ab53fad0a3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bc713823-6a51-467b-9ac0-32ab53fad0a3

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

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		bc713823-6a51-467b-9ac0-32ab53fad0a3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bc713823-6a51-467b-9ac0-32ab53fad0a3 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		bc713823-6a51-467b-9ac0-32ab53fad0a3
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=bc713823-6a51-467b-9ac0-32ab53fad0a3 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		bc713823-6a51-467b-9ac0-32ab53fad0a3
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
rootnoverify	(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


=============================== sdb6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sdb6 during installation
UUID=bc713823-6a51-467b-9ac0-32ab53fad0a3 /               ext4    relatime,errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=3b7a8772-2aaf-4554-b68e-8d85174a3b0a /home           ext4    relatime        0       2
# swap was on /dev/sdb5 during installation
UUID=efc3e72e-7b8a-4b05-a937-66eb7a4faa5f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sdb6: Location of files loaded by Grub: ===================


  46.8GB: boot/grub/menu.lst
  46.7GB: boot/grub/stage2
  46.7GB: boot/initrd.img-2.6.28-11-generic
  46.8GB: boot/vmlinuz-2.6.28-11-generic
  46.7GB: initrd.img
  46.8GB: vmlinuz

Thanks all in advance.

---

### Post by e_james on 2009-05-09
My experience of linux is limited and it is likely that some of my statements here will be at least partly incorrect but I think I might know where to look for your NTLDR problem. I currently have 6 PCs dual or triple booting Windows and Linux but only one has a mixture of Pata and Sata drives and that one boots from the Pata drive. From comments in other forum threads I believe that Grub and the bios sometimes disagree on the drive numbering, especially when Pata and Sata are both present. From your information above, it looks as if this may be the case here. I think what you call Disk 1 (the Windows boot drive) is identified by linux as sdb (grub (hd1)). I notice that grub seems to be swapping the drive identities before booting Windows. This is the usual strategy if Windows is installed on the second drive. If the Windows boot loader ends up trying to run NTLDR from the wrong drive you would likely get the error you describe. It might also be useful to use a partition editor to check the flags on another Windows boot partition to see if there may be a significant difference. I believe Windows XP doesn't care but Windows 98 won't boot if the partition isn't marked 'active'. It doesn't have NTLDR but the error message is similar. To dual boot XP and 98 using grub, you have to 'hide' one and 'unhide' the other. 

In your situation I would try experimenting with the grub settings for the Windows boot

e.g.

rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)  ->  # map (hd0) (hd1)
map (hd1) (hd0)  ->  # map (hd1) (hd0)
chainloader +1

or maybe even

rootnoverify (hd1,0)  ->  rootnoverify (hd0,0)
savedefault
map (hd0) (hd1)  ->  # map (hd0) (hd1)
map (hd1) (hd0)  ->  # map (hd1) (hd0)
chainloader +1

NB You can make a one time change of the grub settings by editing the menu lines when they appear at boot time. If you get a setting that works, then you can edit menu.lst to make it permanent.

You could also try a SuperGrub CD or a Gujin CD to verify that Windows will still boot without the installed grub 'helping'.

---

### Post by Mortus Pryde on 2009-05-10
Thanks e-james that worked! So I am guessing it confused my setup as Dual Boot with two hard drives for some reason and was switching hd0 and hd1, then trying to boot the origional hd0 which is just a data drive. Comenting out the map drives worked.

I don't think it gets all that confused as to the order, I think it uses the same order they are detected in BIOS, not how the user has set the boot drive priority. In my case the following is the order my BIOS sees my hard drives.

IDE0 = 160GB IDE Hard Drive -> sda (hd0)
SATA0 = 80GB SATA Hard Drive -> sdb (hd1)
SATA1 = 250GB SATA Hard Drive -> sdc (hd2)

Now that I am back in Windows I find I would much rather be in Ubuntu! LOL

---

### Post by e_james on 2009-05-10
I am happy I was able to help. Thanks for letting me know the outcome. It is my own intention to move from Windows to Linux but there are some things I still can't do as well with Linux as I can with Windows. I'm working on it.

---

