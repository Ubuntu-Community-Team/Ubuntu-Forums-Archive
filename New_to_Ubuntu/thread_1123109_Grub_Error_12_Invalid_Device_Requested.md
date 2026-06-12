---
title: "Grub Error 12: Invalid Device Requested"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by Neurosynapse on 2009-04-11
**_First of All:_** I have searched, and I found no solutions that worked for me, I have also checked outside sources, and used a Windows Vista repair disk to attempt to repair the boot for Windows.

That said; Every time I attempt to boot my Windows Vista partition, I get this error:

```
Error 12: Invalid Device Requested
Press Any Key To Continue...
```I suffered this error after resizing the Vista NTFS partition (after it had been defragged and such) with gparted...I'm not sure what to do at this point, I've made sure the correct /dev/sda1 was listed on menu.lst.

If anyone can help me, I'd appreciate any help!

Thank you,
Neuro

---

### Post by meierfra. on 2009-04-11
In order to get a clearer picture of your setup, I suggest to boot into  Ubuntu and  download the Boot Info Script to  your desktop:

[https://sourceforge.net/projects/bootinfoscript/]("https://sourceforge.net/projects/bootinfoscript/")

Then open a terminal (Applications > Accessories > Terminal) and type:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post,  highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be

---

### Post by Neurosynapse on 2009-04-11
The Results.txt! Thanks for the quick reply! I shall save that script for later usage.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda1 starts 
                       at sector 98304. But according to the info from fdisk, 
                       sda1 starts at sector 63.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000080

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   165,228,524   165,228,462   7 HPFS/NTFS
/dev/sda2         165,228,525   234,436,544    69,208,020   f W95 Ext d (LBA)
/dev/sda5         165,228,651   175,220,954     9,992,304  82 Linux swap / Solaris
/dev/sda6         175,221,018   234,436,544    59,215,527  83 Linux


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="5EF6D23BF6D2135F" TYPE="ntfs" 
/dev/sda5: UUID="b46bf762-bcaa-44fd-be2a-fe6a1979cd09" TYPE="swap" 
/dev/sda6: UUID="bf842c67-dcd1-4941-81fc-6ff626ab6fbf" TYPE="ext3" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/neuro/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=neuro)


=========================== sda6/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color white/blue blink-blue/light-gray

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=bf842c67-dcd1-4941-81fc-6ff626ab6fbf ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=bf842c67-dcd1-4941-81fc-6ff626ab6fbf

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
# defoptions=splash vga=792 quiet

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
# howmany=1

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

title        Ubuntu 8.10 - Linux-2.6.27-11
uuid        bf842c67-dcd1-4941-81fc-6ff626ab6fbf
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=bf842c67-dcd1-4941-81fc-6ff626ab6fbf ro splash vga=792 quiet 
initrd        /boot/initrd.img-2.6.27-11-generic
quiet

title        Ubuntu 8.10 - Linux-2.6.27-11 (Recovery Mode)
uuid        bf842c67-dcd1-4941-81fc-6ff626ab6fbf
kernel        /boot/vmlinuz-2.6.27-11-generic root=UUID=bf842c67-dcd1-4941-81fc-6ff626ab6fbf ro  single
initrd        /boot/initrd.img-2.6.27-11-generic

title        Ubuntu 8.10 - Memtest86+
uuid        bf842c67-dcd1-4941-81fc-6ff626ab6fbf
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista
root        (hd0,4)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=bf842c67-dcd1-4941-81fc-6ff626ab6fbf /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=b46bf762-bcaa-44fd-be2a-fe6a1979cd09 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 105.6GB: boot/grub/menu.lst
 105.7GB: boot/grub/stage2
  96.9GB: boot/initrd.img-2.6.27-11-generic
  96.8GB: boot/initrd.img-2.6.27-7-generic
  96.9GB: boot/initrd.img-2.6.27-9-generic
  96.9GB: boot/vmlinuz-2.6.27-11-generic
 107.9GB: boot/vmlinuz-2.6.27-7-generic
  96.8GB: boot/vmlinuz-2.6.27-9-generic
  96.9GB: initrd.img
  96.9GB: initrd.img.old
  96.9GB: vmlinuz
  96.8GB: vmlinuz.old
```

---

### Post by presence1960 on 2009-04-11
looking at your text you posted above, try changing your vista entry in menu.lst to 

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista
root        (hd0,0)
savedefault
makeactive
chainloader    +1

---

### Post by meierfra. on 2009-04-11
Grub Error 12 is caused by the wrong entry on menu.lst
Open menu.lst via 

```
gksudo gedit /boot/grub/menu.lst 
```

and  change  "root (hd0,4)" in the Windows entry to "root (hd0,0)".


That should take care of the grub error 12. But you have more problems:

> Boot sector info: According to the info in the boot sector, sda1 starts at sector 98304. But according to the info from fdisk,
sda1 starts at sector 63. 

To fix this, boot from the Vista DVD (if you don't have a Vista  DVD, you can get a Vista Recovery CD from [here]("http://www.pcworld.com/downloads/file/fid,71039/description.html"))
and choose "Repair Computer".  

The Vista DVD might automatically detected  a "start up problem" and offer to fix the problem. If it  does, say no.
At the new screen choose "command line". In the command line type

```
bootrec  /fixboot
```

and then 

```
exit
```

to get back to the previous screen.

Choose  "StartUp Repair"

Hopefully that will be enough to fix your booting problem. If not,  come back here and report all error messages you got.

---

### Post by Neurosynapse on 2009-04-11
> **presence1960 said:**
> looking at your text you posted above, try changing your vista entry in menu.lst to

Trying that now. Will report in a second. :)

---

### Post by presence1960 on 2009-04-11
BTW neurosynapse that is a cool avatar!

---

### Post by Neurosynapse on 2009-04-11
Thanks Presence1960 :)

Unfortunately just switching it to hd0,0 didn't work, it hangs at "Starting Up..." so I'm going to attempt the vista disk fix.

Will report in a minute.

---

### Post by Neurosynapse on 2009-04-11
Unfortunately, fixboot, and modifying the menu.lst hasn't worked. Vista hangs at:
```
Starting Up...
_
```

So back to square one?

---

### Post by meierfra. on 2009-04-11
Plan B:


Download the [testdisk-6.10.linux26.tar.bz2 package](http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2) to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```


Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Vista.

---

### Post by Neurosynapse on 2009-04-11
> **meierfra. said:**
> Plan B:


Download the [testdisk-6.10.linux26.tar.bz2 package]("http://www.cgsecurity.org/testdisk-6.10.linux26.tar.bz2") to your desktop, and then do:

```


cd ~/Desktop
tar xvf testdisk-6.10.linux26.tar.bz2
sudo testdisk-6.10/linux/testdisk_static /dev/sda

```
Choose "proceed" on the first screen, then
"intel"
"advanced",
Select the Windows partition (although it should be selected already) and choose
"boot"
"RebuildBS"
"Write"  

then press "q" a few times to quit  testdisk, reboot and see whether you can boot into Vista.

And Meierfra has saved the day! I've no idea how to thank you other than...
[FONT=Impact][SIZE=7][COLOR=Red]THANK YOU!!![/COLOR][/SIZE][/FONT]

I do sincerely appreciate your time and quick responses! And you taught me quite a bit about boot records, and a few new terminal commands. I appreciate everyone's help!

---

### Post by meierfra. on 2009-04-11
> And Meierfra has saved the day! 

Glad that testdisk did the trick. Fixboot is supposed to do the same thing, but it just fails from while to while.

Have fun with Vista and  Ubuntu.

---

### Post by Neurosynapse on 2009-04-11
> **meierfra. said:**
> Glad that testdisk did the trick. Fixboot is supposed to do the same thing, but it just fails from while to while.

Have fun with Vista and  Ubuntu.

Thanks, Will Do! :D

---

### Post by meierfra. on 2009-04-12
Neurosynapse:  Could you do me a favor?  The "starting up" error you got seems to be due to a bug in "gparted". Could you tell my which version of gparted you used. Go to 'Help'-->'About', while in GParted.

Thanks.

---

### Post by Neurosynapse on 2009-04-12
> **meierfra. said:**
> Neurosynapse:  Could you do me a favor?  The "starting up" error you got seems to be due to a bug in "gparted". Could you tell my which version of gparted you used. Go to 'Help'-->'About', while in GParted.

Thanks.

Sure, I'm using version 0.3.8 (Which I believe is the newest one) of Gparted. If this is a bug, I'd be happy to provide a recount of what I did to reproduce it, if that's necessary.

---

### Post by meierfra. on 2009-04-12
> If this is a bug,
Well, it seems to be a bug nobody bothered to report yet.

>  I'd be happy to provide a recount of what I did to reproduce it, if that's necessary.

That would be nice.

---

### Post by Neurosynapse on 2009-04-12
> **meierfra. said:**
> That would be nice.

Sure. I use a Dell Inspiron 1525, Due to a foul up with Dell's technical support on a broken Windows installation, they had me install Dell Media Direct 3 times. Dell MediaDirect is a 3gig partition specially used to run media without booting an OS.

I removed these three partitions (Since I never used MediaDirect anyway) and decided to use gparted to expand my Windows and Linux partitions to use up that unallocated 9gigs. Doing so on Linux took only a few minutes, and worked perfectly. I defragged Windows twice, to make sure it would work properly, and extended it to the left, unfortunately creating the boot problem.

However, everything is fine, no data is missing, as far as I could tell, but that's pretty much all I did. I did this, mind you, in a gparted LiveCD of the same version, using all the default settings and such.

Hope this helps!
Neuro

---

### Post by meierfra. on 2009-04-12
Thanks.  Unfortunately I still have no idea what triggers the bug. 
I'll probably do some experiments  and, if I'm able to recreate the bug, file a bug report.

One last question:  You said that you extended Vista to the left.  By how much did you extend it to the left? That is, how much unallocated space was to the left of Vista  just before you extended it?

---

### Post by Neurosynapse on 2009-04-12
> **meierfra. said:**
> Thanks.  Unfortunately I still have no idea what triggers the bug. 
I'll probably do some experiments  and, if I'm able to recreate the bug, file a bug report.

One last question:  You said that you extended Vista to the left.  By how much did you extend it to the left? That is, how much unallocated space was to the left of Vista  just before you extended it?

6 Gigs left of Vista, 3 left of Linux. Hopefully it can be fixed, when I couldn't reboot into Vista I panicked, thinking I broke the partition and lost/destroyed data. Hate to see it happen to someone else.

---

### Post by meierfra. on 2009-04-12
> 6 Gigs left of Vista,

>  sda1 starts  at sector 98304.  

Strange, these numbers don't match.  98304 sectors are only about 50MB.
I always thought that the  "startup'  error occurs because gparted  forgets to update to boot sector. This  now seems to indicate, that gparted updates the boot sector, but does it wrongly.

Thanks again for you help.

---

### Post by Neurosynapse on 2009-04-12
> **meierfra. said:**
> Strange, these numbers don't match.  98304 sectors are only about 50MB.
I always thought that the  "startup'  error occurs because gparted  forgets to update to boot sector. This  now seems to indicate, that gparted updates the boot sector, but does it wrongly.

Thanks again for you help.

O.o Only 50mb? Now that is weird...I figured it was a bug on windows because I expanded it in gparted! In Gparted it said 3gig, in Windows it shows only 50mb more space. O_o

So, does that mean gparted was wrong? Or there's a random 3gigs of my hard drive...missing?

---

### Post by Herman on 2009-04-16
> Sure, I'm using version 0.3.8 (Which I believe is the newest one) of Gparted. If this is a bug, I'd be happy to provide a recount of what I did to reproduce it, if that's necessary.Neurosynapse, Thank you for that information.

Was the GParted 0.3.8 you used in a GParted LiveCD or in a Ubuntu 'Desktop' CD? Hopefully this problem is restricted to only the one version of GParted Live CD.

My Jaunty Jackalope beta has GParted 0.4.3 in it.

Thanks for any information,
Regards, Herman :smile:

---

### Post by Neurosynapse on 2009-04-16
> **Herman said:**
> Neurosynapse, Thank you for that information.

Was the GParted 0.3.8 you used in a GParted LiveCD or in a Ubuntu 'Desktop' CD? Hopefully this problem is restricted to only the one version of GParted Live CD.

My Jaunty Jackalope beta has GParted 0.4.3 in it.

Thanks for any information,
Regards, Herman :smile:

It was a GParted LiveCD, and hopefully it is =)

---

### Post by Herman on 2009-04-16
Yes, I think it has been fixed in GParted Live CD 0.4.3-4 and later, from what I have been reading.
Thank you very much for your kind co-operation, that news is important to me and it's what I was hoping to find out.

Your feedback will help me decide how to edit my website appropriately.

Thanks again,
Regards, Herman :smile:

---

### Post by Romonov on 2009-10-04
I am a linux/ubuntu beginner and would appreciate any advice. I am having the same error as posted in the topic:
Error 12: Invalid Device Requested 

Here is a quick summary of events.

- I already have Windows XP in C drive in Windows and I installed Ubuntu 9.0.4. The dual boot worked fine.
- I logged on to windows and deleted, created and formatted D partition. When I restarted, I got the following error:
grub
error 17
- I read through threads in ubuntu forums and went to ubuntu trial using Live CD. I tried
```

sudo grub
grub> find /boot/grub/stage1
(hd0,5)
grub>setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  17 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,5)/boot/grub/stage2
/boot/grub/menu.lst"... failed

Error 12: Invalid device requested

grub>

```- I downloaded bootinfoscript as advised in this thread and the following is the output in Results.txt. 
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #256 for /boot/grub/stage2.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda7: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst /grub/grub.conf

sda8: _________________________________________________________________________

    File system:       lvm2pv
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type 'lvm2pv'

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197   6 FAT16
/dev/sda2    *         64,260   224,669,024   224,604,765   7 HPFS/NTFS
/dev/sda3         224,669,025   242,308,394    17,639,370   7 HPFS/NTFS
/dev/sda4         242,308,395   312,496,379    70,187,985   5 Extended
/dev/sda5         242,308,521   274,374,134    32,065,614  83 Linux
/dev/sda6         274,374,198   275,868,179     1,493,982  82 Linux swap / Solaris
/dev/sda7         275,868,243   276,077,024       208,782  83 Linux
/dev/sda8         276,077,088   312,496,379    36,419,292  8e Linux LVM


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0713" TYPE="vfat" 
/dev/sda2: UUID="127437F07437D4E7" TYPE="ntfs" 
/dev/sda3: UUID="7AECEBA7ECEB5BBF" LABEL="New Volume" TYPE="ntfs" 
/dev/sda5: UUID="21134c6a-2d65-455c-b180-4bbc30d955ab" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="8c4553eb-eb6c-468f-a063-084765a86a0e" TYPE="swap" 
/dev/sda7: LABEL="/boot" UUID="3cbebc3c-3b7a-4ea4-b766-48c13f425e2e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: UUID="KX8pf4-AEzG-6tD7-A225-s4lv-iZBT-4P9aXm" TYPE="lvm2pv" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)


================================ sda2/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Windows XP Media Center Edition" /noexecute=optin /fastdetect 

=========================== sda5/boot/grub/menu.lst: ===========================

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        10

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=21134c6a-2d65-455c-b180-4bbc30d955ab ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=21134c6a-2d65-455c-b180-4bbc30d955ab

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

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        21134c6a-2d65-455c-b180-4bbc30d955ab
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=21134c6a-2d65-455c-b180-4bbc30d955ab ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        21134c6a-2d65-455c-b180-4bbc30d955ab
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=21134c6a-2d65-455c-b180-4bbc30d955ab ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        21134c6a-2d65-455c-b180-4bbc30d955ab
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Dell Utility Partition
root        (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows XP Media Center Edition
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda7 during installation
UUID=21134c6a-2d65-455c-b180-4bbc30d955ab /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda8 during installation
UUID=8c4553eb-eb6c-468f-a063-084765a86a0e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 129.9GB: boot/grub/menu.lst
 129.9GB: boot/grub/stage2
 129.9GB: boot/initrd.img-2.6.28-11-generic
 129.9GB: boot/vmlinuz-2.6.28-11-generic
 129.9GB: initrd.img
 129.9GB: vmlinuz

============================= sda7/grub/grub.conf: =============================

# grub.conf generated by anaconda
#
# Note that you do not have to rerun grub after making changes to this file
# NOTICE:  You have a /boot partition.  This means that
#          all kernel and initrd paths are relative to /boot/, eg.
#          root (hd0,4)
#          kernel /vmlinuz-version ro root=/dev/VolGroup00/LogVol00
#          initrd /initrd-version.img
#boot=/dev/sda
default=2
timeout=10
splashimage=(hd0,4)/grub/splash.xpm.gz
hiddenmenu
title Fedora (2.6.23.1-10.fc7)
    root (hd0,4)
    kernel /vmlinuz-2.6.23.1-10.fc7 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
    initrd /initrd-2.6.23.1-10.fc7.img
title Fedora (2.6.21-1.3194.fc7)
    root (hd0,4)
    kernel /vmlinuz-2.6.21-1.3194.fc7 ro root=/dev/VolGroup00/LogVol00 rhgb quiet
    initrd /initrd-2.6.21-1.3194.fc7.img
title Other
    rootnoverify (hd0,1)
    chainloader +1

=================== sda7: Location of files loaded by Grub: ===================


 141.3GB: grub/grub.conf
 141.3GB: grub/menu.lst
 141.3GB: grub/stage2
 141.2GB: initrd-2.6.21-1.3194.fc7.img
 141.2GB: initrd-2.6.23.1-10.fc7.img
 141.2GB: vmlinuz-2.6.21-1.3194.fc7
 141.2GB: vmlinuz-2.6.23.1-10.fc7

```Referring to the Results.txt output, the problem started when I formatted /dev/sda3, which is D: drive in windows and size ~8GB. 

Is there a way to get out of this problem ?
thanks in advance for your time

---

### Post by unutbu on 2009-10-04
It looks like your root partition is /dev/sda5. In (legacy) GRUB-notation, that would by (hd0,4). So perhaps try booting from the LiveCD, and running```


sudo grub
grub> root (hd0,4)
grub> setup (hd0)

```

---

### Post by Romonov on 2009-10-04
That was a quick response! Go Ubuntu forums! 

I tried your suggestion, but the setup hasnt succeeded. Here is the output of running that:

```

grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 


```

---

### Post by presence1960 on 2009-10-04
> **Romonov said:**
> That was a quick response! Go Ubuntu forums! 

I tried your suggestion, but the setup hasnt succeeded. Here is the output of running that:

```

grub> root (hd0,4)

grub> setup (hd0)

Error 17: Cannot mount selected partition

grub> 


```

you have a boot partition at sda7. 

I forget how to restore & setup GRUB with a boot partition, but I think unutbu will know how.

I think it may be 

grub> root (hd0,6)
grub> setup (hd0)

**_But don't quote me on that!_**

---

### Post by Romonov on 2009-10-04
Thanks presence1960. 

Yea. Actually there is fedora in sda7. But after I installed ubuntu in sda5, it failed to come up in the boot menu. Im sorry if it was a mistake not to mention that previously.

---

### Post by Romonov on 2009-10-04
I am not sure in whether sda7 or sda8 has fedora as its been a long time since I installed it. how do i know this? 

I am just posting the output of using fdisk, if it might indicate more information. 

```

root@ubuntu:~# fdisk /dev/sda

The number of cylinders for this disk is set to 19452.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
omitting empty partition (5)

Command (m for help): p

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+   6  FAT16
/dev/sda2   *           5       13985   112302382+   7  HPFS/NTFS
/dev/sda3           13986       15083     8819685    7  HPFS/NTFS
/dev/sda4           15084       19452    35093992+   5  Extended
/dev/sda5           15084       17079    16032807   83  Linux
/dev/sda6           17080       17172      746991   82  Linux swap / Solaris
/dev/sda7           17173       17185      104391   83  Linux
/dev/sda8           17186       19452    18209646   8e  Linux LVM


```

---

### Post by presence1960 on 2009-10-04
> **Romonov said:**
> Thanks presence1960. 

Yea. Actually there is fedora in sda7. But after I installed ubuntu in sda5, it failed to come up in the boot menu. Im sorry if it was a mistake not to mention that previously.

that partition (sda7) is way too small to have an OS on it. and see this from the script in red:

```
blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0713" TYPE="vfat" 
/dev/sda2: UUID="127437F07437D4E7" TYPE="ntfs" 
/dev/sda3: UUID="7AECEBA7ECEB5BBF" LABEL="New Volume" TYPE="ntfs" 
/dev/sda5: UUID="21134c6a-2d65-455c-b180-4bbc30d955ab" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="8c4553eb-eb6c-468f-a063-084765a86a0e" TYPE="swap" 
[COLOR="Red"]/dev/sda7: LABEL="/boot" UUID="3cbebc3c-3b7a-4ea4-b766-48c13f425e2e" SEC_TYPE="ext2" TYPE="ext3" [/COLOR]
/dev/sda8: UUID="KX8pf4-AEzG-6tD7-A225-s4lv-iZBT-4P9aXm" TYPE="lvm2pv" 

```

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe686f016

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        64,259        64,197   6 FAT16
/dev/sda2    *         64,260   224,669,024   224,604,765   7 HPFS/NTFS
/dev/sda3         224,669,025   242,308,394    17,639,370   7 HPFS/NTFS
/dev/sda4         242,308,395   312,496,379    70,187,985   5 Extended
/dev/sda5         242,308,521   274,374,134    32,065,614  83 Linux
/dev/sda6         274,374,198   275,868,179     1,493,982  82 Linux swap / Solaris
[COLOR="Red"]/dev/sda7         275,868,243   276,077,024       208,782  83 Linux[/COLOR]
/dev/sda8         276,077,088   312,496,379    36,419,292  8e Linux LVM



there is no fedora there although it is a /boot partition with GRUB 2 on it. Something got messed up somehow!

---

### Post by presence1960 on 2009-10-04
> **Romonov said:**
> I am not sure in whether sda7 or sda8 has fedora as its been a long time since I installed it. how do i know this? 

I am just posting the output of using fdisk, if it might indicate more information. 

```

root@ubuntu:~# fdisk /dev/sda
[COLOR="Blue"]
The number of cylinders for this disk is set to 19452.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
omitting empty partition (5)[/COLOR]

Command (m for help): p

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           4       32098+   6  FAT16
/dev/sda2   *           5       13985   112302382+   7  HPFS/NTFS
/dev/sda3           13986       15083     8819685    7  HPFS/NTFS
/dev/sda4           15084       19452    35093992+   5  Extended
/dev/sda5           15084       17079    16032807   83  Linux
/dev/sda6           17080       17172      746991   82  Linux swap / Solaris
/dev/sda7           17173       17185      104391   83  Linux
/dev/sda8           17186       19452    18209646   8e  Linux LVM


```

No need to run that command it is in the script output. You must have fedora on sda8 which you installed with LVM (Logical Volume Manager)

Note the blue above. Your Ubuntu is probably outside that boundary and that may be why you can not mount it.

---

### Post by Romonov on 2009-10-04
You might be right. I think it might be in sda8. 


I initially thought ubuntu's installation would recognize fedora. But ubuntu did not list fedora option in boot menu. before i could look into that problem, I ran into this current problem with ubuntu's grub.

---

### Post by presence1960 on 2009-10-04
> **Romonov said:**
> You might be right. I think it might be in sda8. 


I initially thought ubuntu's installation would recognize fedora.[COLOR="Red"] But ubuntu did not list fedora option in boot menu[/COLOR]. before i could look into that problem, I ran into this current problem with ubuntu's grub.

If Ubuntu's boot menu came up then GRUB was working. What did you do to your machine at that point? Did you have a RAID setup with another disk at one point? Because your GRUB was pointing to partition # 256. I saw that same thing the other day on an ubuntu server install. After some back & forth it was discovered the person had RAID. You only have one hard disk now, but did you have 2 with a RAID setup?

---

### Post by Romonov on 2009-10-04
I deleted, re-created and formatted my D: drive in windows which is sda3. Once I restarted the machine, I was getting 
grub error 17

It is described in more detail post #25 here:
[http://ubuntuforums.org/showthread.php?t=1123109&page=3](http://ubuntuforums.org/showthread.php?t=1123109&page=3)

---

### Post by presence1960 on 2009-10-04
```
=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
[COLOR="Red"]# / was on /dev/sda7 during installation
UUID=21134c6a-2d65-455c-b180-4bbc30d955ab /               ext3    relatime,errors=remount-ro 0       1[/COLOR]
# swap was on /dev/sda8 during installation
UUID=8c4553eb-eb6c-468f-a063-084765a86a0e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

here is the problem, your fstab says / is on sda7!
and it says swap is on sda8!

---

### Post by unutbu on 2009-10-04
presence1960, although the comments are wrong, the UUIDs are correct.

Romonov, I'm not quite sure what's wrong, nor what the correct fix is. However, the following should not hurt and may help:

Boot from the LiveCD
```

cd ~/Desktop
wget http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2
tar xvjf testdisk*.tar.bz2
```

This will download the latest version of testdisk. The testdisk program can check your partition table for errors, and may be able to correct any errors it finds.
```

sudo testdisk-6.11.3/linux/testdisk_static
```

This runs testdisk_static.

Select "No Log", "Proceed", "Intel", "Analyse", "Quick Search", "Deeper Search"
The Deeper Search may take some time.
Use the up/down arrows to move among your partitions.
Press 'p' to try to list files inside the partitions.

Can you see the files in /dev/sda5 ?

If you can see the files in sda1, sda2, sda3, sda5, sda7 and sda8(*) then write the partition table to disk and exit testdisk.  

(*) I'm not sure if testdisk can read LVM partitions. If not, don't worry about sda8.

After using testdisk to write a new partition table, try 
```

sudo mount /dev/sda5 /mnt
ls -l /mnt
```

This is just a sanity check to make sure you can mount your root partition.
If you can, then try:

```

sudo umount /mnt
sudo grub
grub> root (hd0,4)
grub> setup (hd0)

```
again. Hopefully you won't get the same error.

Please post back with what happens. Terminal output would be most helpful.

---

### Post by Romonov on 2009-10-04
Thanks Unutbu. Here is the output of the Deeper Search in the Windows 107GB (sda2) drive:
```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19453 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     3 254 63      64197 [DellUtility]
P HPFS - NTFS              4   0  1 13984 254 63  224604765
D HPFS - NTFS          13985   0  1 15082 254 63   17639370 [New Volume]
D HPFS - NTFS          13985   0  1 15769 254 63   28676025 [New Volume]
D HPFS - NTFS          13985   0  1 17171 254 63   51199155 [New Volume]
D HPFS - NTFS          13985   0  1 18845 254 63   78091965 [New Volume]
D Linux                15083   2  1 17078 254 57   32065608
D Linux Swap           17079   1  1 17171 254 41    1493960
D Linux                17172   1  1 17184 254 57     208776 [/boot]
D Linux                17172   1  1 19190 254 59   32435168 [/]
D HPFS - NTFS          17172   1  1 19451 254 63   36628137
D Linux LVM            17185   1  1 19451 254 63   36419292
Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 32 MB / 31 MiB

```I am still doing the deeper search for the remaining partitions. Once done, I selected "Write". It said "You will have to reboot for the change to take effect". After this should I quit the software or should I select 
[MBR Code] Write TestDisk MBR code to first sector? 

Also after I quit, should I reboot and then run the commands on testing mount and root (hd0,4)...  or should I do that before rebooting?

---

### Post by Romonov on 2009-10-05
I just realized the deeper search is the same no matter which partition is highlighted and searches all disks. pls correct me if I am wrong.

---

### Post by Romonov on 2009-10-05
Also, I can view the contents of /dev/sda5.

---

### Post by Romonov on 2009-10-05
I tried typing the following both before and after rebooting. 

Before rebooting:
```

sudo mount /dev/sda5 mnt

```
worked and I could see the contents of the folder
I did an umount and entered into grub and got the following output:
```

sudo grub
grub> root (hd0,4)
Error 22: No such partition

```

After rebooting, the mount did not work:
```

sudo mount /dev/sda5 mnt
mount: special device /dev/sda5 does not exist

```

The result of grub commands is the same as before rebooting.

---

### Post by Romonov on 2009-10-05
Right now the find command is not successful either. 

```

sudo grub
grub> find /boot/grub/stage1
Error 15: File not found

```

---

### Post by unutbu on 2009-10-05
Romanov, notice the D's in the first column on the left:
```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19453 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1     3 254 63      64197 [DellUtility]
P HPFS - NTFS              4   0  1 13984 254 63  224604765
D HPFS - NTFS          13985   0  1 15082 254 63   17639370 [New Volume]
D HPFS - NTFS          13985   0  1 15769 254 63   28676025 [New Volume]
D HPFS - NTFS          13985   0  1 17171 254 63   51199155 [New Volume]
D HPFS - NTFS          13985   0  1 18845 254 63   78091965 [New Volume]
D Linux                15083   2  1 17078 254 57   32065608
D Linux Swap           17079   1  1 17171 254 41    1493960
D Linux                17172   1  1 17184 254 57     208776 [/boot]
D Linux                17172   1  1 19190 254 59   32435168 [/]
D HPFS - NTFS          17172   1  1 19451 254 63   36628137
D Linux LVM            17185   1  1 19451 254 63   36419292
```

"D" stands for deleted. They indicate partitions that existed at one point but are not listed in the current partition table. Using the left/right arrow keys you can change the "D" into a "P" for primary partition, or "L" for logical partition, or "*" for primary bootable. I believe you should change the partitions to look like this:

```
Disk /dev/sda - 160 GB / 149 GiB - CHS 19453 255 63
     Partition               Start        End    Size in sectors
**P** FAT16 >32M               0   1  1     3 254 63      64197 [DellUtility]
***** HPFS - NTFS              4   0  1 13984 254 63  224604765
**P** HPFS - NTFS          13985   0  1 15082 254 63   17639370 [New Volume]
D HPFS - NTFS          13985   0  1 15769 254 63   28676025 [New Volume]
D HPFS - NTFS          13985   0  1 17171 254 63   51199155 [New Volume]
D HPFS - NTFS          13985   0  1 18845 254 63   78091965 [New Volume]
**L** Linux                15083   2  1 17078 254 57   32065608
**L** Linux Swap           17079   1  1 17171 254 41    1493960
**L** Linux                17172   1  1 17184 254 57     208776 [/boot]
D Linux                17172   1  1 19190 254 59   32435168 [/]
D HPFS - NTFS          17172   1  1 19451 254 63   36628137
**L** Linux LVM            17185   1  1 19451 254 63   36419292

```
For each line that begins with a "P","L",or "*", press 'p' to check that you can see the files inside the partitions. If you can, then select "Write" to write the new partition table to disk.

---

### Post by presence1960 on 2009-10-05
> **unutbu said:**
> presence1960, although the comments are wrong, the UUIDs are correct.


I noticed that last night, but I was too tired to continue. My eyes were like lead weights so I went to bed. My daughter had a sleepover the previous night, although I survived they drained me. :)

---

### Post by unutbu on 2009-10-05
LOL :)  Thank you for working on this with me. Two eyes are always better than one, and are often required to spot GRUB problems.

---

### Post by presence1960 on 2009-10-05
> **unutbu said:**
> LOL :)  Thank you for working on this with me. Two eyes are always better than one, and are often required to spot GRUB problems.

No problem. Yeah my daughter had 6 of her friends over for a sleepover, I was really burnt out from the previous night. But they had fun so that is all that matters!

---

### Post by Romonov on 2009-10-05
Thanks a lot unutbu and presence1960. i am on live CD and running testdisk once again. I will make the modifications suggested and post here soon.

---

### Post by Romonov on 2009-10-05
Posted in next reply.

---

### Post by Romonov on 2009-10-05
I just realized there are more entries below in the partition table. I am just copy-pasting here the complete list:
```

Disk /dev/sda - 160 GB / 149 GiB - CHS 19453 255 63
     Partition               Start        End    Size in sectors
P FAT16 >32M               0   1  1     3 254 63      64197 [DellUtility]
* HPFS - NTFS              4   0  1 13984 254 63  224604765
P HPFS - NTFS          13985   0  1 15082 254 63   17639370 [New Volume]
D HPFS - NTFS          13985   0  1 15769 254 63   28676025 [New Volume]
D HPFS - NTFS          13985   0  1 17171 254 63   51199155 [New Volume]
D HPFS - NTFS          13985   0  1 18845 254 63   78091965 [New Volume]
L Linux                15083   2  1 17078 254 57   32065608
L Linux Swap           17079   1  1 17171 254 41    1493960
L Linux                17172   1  1 17184 254 57     208776 [/boot]
D Linux                17172   1  1 19190 254 59   32435168 [/]
D HPFS - NTFS          17172   1  1 19451 254 63   36628137
L Linux LVM            17185   1  1 19451 254 63   36419292
D Linux                17187   2 32 19194  22 28   32243712
D Linux                17187 230  4 19194 249 63   32243712
D Linux                17188 170  7 19195 190  3   32243712
D Linux                17188 235  8 19196   0  4   32243712
D Linux                17189 207 43 19196 227 39   32243712
D Linux                17191 217 51 19198 237 47   32243712
D Linux                17193 130 26 19200 150 22   32243712
D Linux                17198  58 13 19205  78  9   32243712
D Linux                17199 225 51 19206 245 47   32243712
D Linux                17202 110 61 19209 130 57   32243712
D Linux                17202 143 30 19209 163 26   32243712
D FAT32 LBA            18846   0  1 19451 254 63    9735390 [DellRestore]
D Linux Swap           19191   1  1 19451 254 41    4192880


```

I changed the entried till Linux LVM as suggested. Should I leave the remaining ones below that as D?

---

### Post by unutbu on 2009-10-05
Romonov, I think the "P"s, "*", and "L"s that you've selected are correct. 
I'm basing it off the size in sectors that the "Deeper search" is reporting, compared to
the output of "sudo fdisk -lu" in the RESULTS.txt file created by bootinfoscript.

(And yes, leave the remaining ones marked "D".)

---

### Post by Romonov on 2009-10-05
It worked! :) I am now logged into Ubuntu. Thanks a lot Unutbu and presence1960! 

I am trying to learn modifying grub while installing multiple OSs and stuff. I would be really thankful if you can spare some advice or suggest some pointers where I can get more info:

Firstly, I want the grub to recognise the fedora installation. Then I want to erase everything related to Fedora and install another operating system, like Gentoo, which someone advised will teach me a lot. 


Or if you suggest its too messy to find Fedora, I want to erase everything on the /dev/sda7 and /dev/sda8 if that won't harm my current setup and they are only related to Fedora. And go ahead installing Gentoo.

---

### Post by unutbu on 2009-10-05
I'm very relieved to read that it worked! :)

There are a couple of steps needed to boot Fedora:

[list]
[*] modify your /boot/grub/menu.lst on /dev/sda5 (Ubuntu) by adding a boot stanza like this to the end of the file:
```

title      	Fedora
root       	(hd0,6)
chainloader +1
```

This will add an option to your GRUB menu called "Fedora". When you select it, GRUB will look for a bootloader in the first few sectors of /dev/sda7. This is the Fedora boot partition.
[*] install the GRUB 2 bootloader to the first few sectors of /dev/sda7. I am not certain of how to do that, but if you ask here [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275), you may be able to get the answer. 
[*] On /dev/sda7 you have a file called /grub/grub.conf. I believe this is GRUB 2's equivalent of legacy GRUB's menu.lst. There I think you'll need to change all occurrences of (hd0,4) to (hd0,6) because (hd0,4) is GRUB-notation for /dev/sda5 and (hd0,6) is /dev/sda7. 
[/list]

Once you make those changes, I think there is a fair chance you'll be able to boot Fedora. I'm not sure mainly because I don't have much experience with GRUB 2. I hope this helps.

Also, for more details on how to multi-boot, see [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817).

---

### Post by presence1960 on 2009-10-05
> **unutbu said:**
> I'm very relieved to read that it worked! :)

There are a couple of steps needed to boot Fedora:

[list]
[*] modify your /boot/grub/menu.lst on /dev/sda5 (Ubuntu) by adding a boot stanza like this to the end of the file:
```

title      	Fedora
root       	(hd0,6)
chainloader +1
```

This will add an option to your GRUB menu called "Fedora". When you select it, GRUB will look for a bootloader in the first few sectors of /dev/sda7. This is the Fedora boot partition.
[*] install the GRUB 2 bootloader to the first few sectors of /dev/sda7. I am not certain of how to do that, but if you ask here [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275), you may be able to get the answer. 
[*] On /dev/sda7 you have a file called /grub/grub.conf. I believe this is GRUB 2's equivalent of legacy GRUB's menu.lst. There I think you'll need to change all occurrences of (hd0,4) to (hd0,6) because (hd0,4) is GRUB-notation for /dev/sda5 and (hd0,6) is /dev/sda7. 
[/list]

Once you make those changes, I think there is a fair chance you'll be able to boot Fedora. I'm not sure mainly because I don't have much experience with GRUB 2. I hope this helps.

Also, for more details on how to multi-boot, see [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817).

Great advice there! When I was running multiple OSs such as Ubuntu, Mint, Sabayon (GRUB2), & Masonux 9.04 along with Windows chainloading from Ubuntu's GRUB on MBR was the way to go. I installed GRUB from the other distros to that distro's partition rather than MBR and chainloaded it from the GRUB already on MBR (Ubuntu's). It worked even with sabayon which uses GRUB 2.

P.S. another decided advantage is when you update kernels only the menu.lst of that distro is updated with the new kernel. If you are not chainloading then you must edit each entry for that distro to include the updated kernels in the menu.lst that is taking over when you boot. With chainloading there is no need for that because when you choose the chainloaded entry in GRUB menu it passes off to that distro's menu.lst/grub.conf which already has the updated kernels. No messy editing every kernel update!

---

### Post by Romonov on 2009-10-06
Thanks for the advice. 

I am having problems following those steps. But instead of posting those problems, I just want erase whatever is there on fedora related partitions (sda 7 and sda 8 , combine them into a single partition and install Gentoo on it. That way, I dont have to deal with any other things that are messed up with Fedora (since it may not have the information about the partitions I modified for installing Ubuntu)

could you please let me know what I need to do to make ready and combine sda7 and sda8 for installing gentoo. Thanks a lot for your time and sharing your knowledge.

---

### Post by Romonov on 2009-10-06
Also, if I make those modifications for sda 7 and sda 8, should I do something more so that Windows will not have problems, since it may not see the changes in partitions that I do in Ubuntu.

---

### Post by unutbu on 2009-10-06
While booted into Ubuntu, click System>Admin>"Partition Editor". This will launch GParted.
Use this partition editor to delete sda7 and sda8 and create a new ext3 partition or partitions in its place. Click the "Apply" button to tell GParted to go forward with the changes.

Then you should be all set to install Gentoo. None of this should affect Windows or Ubuntu.

Good luck :)

---

### Post by Romonov on 2009-10-07
I tried gparted but it did not show any of the partitions. It showed the complete disk as unallocated. There are few discussions with this problem, but I thought it would be better to just reinstall everything from the beginning afresh. So I installed Ubuntu 9.0.4. One interesting/weird observation was, when installing with the CD, it didnt recognize any other operating systems installed. Yea! It said there are no operating systems installed on this system. 
I went on to select manual partitioning and used the complete disk for ubuntu. (I have backuped the data. So didnt have a problem with that). 

Just wanted to keep the forum informed of these observations in case they might help any future updates.

---

### Post by unutbu on 2009-10-07
The only time I've found GParted showing a disk with existing partitions as being labeled "unallocated" is when the disk has an invalid partition table.

GRUB and GParted appear to have a certain idea of what constitutes a valid partition table, and start throwing up GRUB errors and acting weird (unallocated space) when the partition table does not conform to its expectations. I do not have concrete proof, but my guess is that other partition editors (such as Windows partition editors) do not conform to the same standards and can, on occasion, produce a partition table that GRUB/GParted think is invalid. 

The workaround is to use testdisk to fix the partition table.

If GParted was showing unallocated space while "sudo fdisk -l" showed existing partitions and after having run testdisk, then I would be at a loss to know what was wrong.

Anyway, congratulations on having the forethought to make good backups, and happy Ubuntu'ing!

---

### Post by govedarov on 2009-10-20
HI,
I have same problem with Error 12, after I tried installing windows XP.
I have Vista and Ubuntu install. 
As expected the XP instalation removed the grub, so I had to install it again.
I removed the XP partition. But I still cannot access the Vista partition (nor the other NTFS partion I have on the drive).

I tried the testdisk, and it seems to be OK there. I can access the directories with the List command, still I cannot boot the Vista.
Can anyone help me?

Here is the output from the boot script recorder:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb636fb14

Partition  Boot         Start           End          Size  Id System

/dev/sda1           3,074,048    90,098,152    87,024,105   7 HPFS/NTFS
/dev/sda3         105,466,725   198,418,814    92,952,090   5 Extended
/dev/sda5         105,466,788   198,081,449    92,614,662  83 Linux
/dev/sda6         198,081,513   198,418,814       337,302  82 Linux swap / Solaris
/dev/sda4         198,434,816   390,721,535   192,286,720   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="D836545C36543DA6" LABEL="Vista" TYPE="ntfs" 
/dev/sda4: UUID="32164C28164BEC03" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="a141225e-bf7c-4d3d-9927-a0aa4e313a30" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="032062ae-4629-445f-abf2-00599a0b7bb8" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ivan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ivan)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect


=========================== sda5/boot/grub/menu.lst: ===========================

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
# kopt=root=UUID=a141225e-bf7c-4d3d-9927-a0aa4e313a30 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a141225e-bf7c-4d3d-9927-a0aa4e313a30

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

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		a141225e-bf7c-4d3d-9927-a0aa4e313a30
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=a141225e-bf7c-4d3d-9927-a0aa4e313a30 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		a141225e-bf7c-4d3d-9927-a0aa4e313a30
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=a141225e-bf7c-4d3d-9927-a0aa4e313a30 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		a141225e-bf7c-4d3d-9927-a0aa4e313a30
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a141225e-bf7c-4d3d-9927-a0aa4e313a30 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a141225e-bf7c-4d3d-9927-a0aa4e313a30
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a141225e-bf7c-4d3d-9927-a0aa4e313a30 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a141225e-bf7c-4d3d-9927-a0aa4e313a30
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=a141225e-bf7c-4d3d-9927-a0aa4e313a30 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=032062ae-4629-445f-abf2-00599a0b7bb8 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  56.3GB: boot/grub/menu.lst
  55.9GB: boot/grub/stage2
  55.5GB: boot/initrd.img-2.6.28-11-generic
  55.4GB: boot/initrd.img-2.6.28-15-generic
  55.9GB: boot/vmlinuz-2.6.28-11-generic
  55.7GB: boot/vmlinuz-2.6.28-15-generic
  55.4GB: initrd.img
  55.5GB: initrd.img.old
  55.7GB: vmlinuz
  55.9GB: vmlinuz.old
```

It is very strange, that my sda1 drive is described as XP boot sector, altrough the XP was never installed there. 

Any suggestions how to fix that mess?

---

### Post by presence1960 on 2009-10-20
look at this from your script:

```
================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition[COLOR="Red"](2)[/COLOR]\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

You have an XP boot loader on your Vista partition. Also the partition in boot.ini should be 1, not 2. (see red above)

You can try editing boot.ini from Ubuntu and change that 2 to a 1. But I am still confuses as to how a Vista install has XP boot files. Please explain.

---

### Post by oldfred on 2009-10-20
Herman has this:
Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing]("http://members.iinet.net/%7Eherman546/p15.html#BOOTMGR_is_missing")
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

restore boot loaders Ubuntu Win xp Vista
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

by meierfra
**How to fix Windows when the boot files are missing **
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

---

### Post by magnus07 on 2009-10-31
Just want to share...
A friend brought in a vista+Ubu 9.04 system with an error 12 as he selected to start vista... similar to previous posts...

After some wrangling I found that somehow grub needed to refer to the sda disk not with hd(0,x) but with hd(1,x) because grub itself was in the second hdd.
just canging hd(0,1) in the menu.lst to hd(1,1) solved the problem.

Thanks to all the others that posted because their toughts made me realize it could had been that the problem.
:popcorn:

PS: UNRELATED COMMENT: grub2 looks very different... it will take time to get used...

---

### Post by presence1960 on 2009-10-31
> **magnus07 said:**
> Just want to share...
A friend brought in a vista+Ubu 9.04 system with an error 12 as he selected to start vista... similar to previous posts...

After some wrangling I found that somehow grub needed to refer to the sda disk not with hd(0,x) but with hd(1,x) because grub itself was in the second hdd.
just canging hd(0,1) in the menu.lst to hd(1,1) solved the problem.

Thanks to all the others that posted because their toughts made me realize it could had been that the problem.
:popcorn:

PS: UNRELATED COMMENT: grub2 looks very different... it will take time to get used...

For future reference with GRUB 0.97: in (hdx,y) in menu.lst x = device and y = partition. Numbering for both start at 0.

But the x designation is not determined by fdisk or Ubuntu. It is determined by hard disk boot order in BIOS, because that is the actual order your disks are loaded when you boot the machine. Since GRUB is on sdb and it comes up when you boot that machine, that device is actually (hd0) even though fdisk & Ubuntu report it as sdb (hd1). Since the sda disk actually boots second it becomes (hd1). If you go into the BIOS and check the hard disk boot order you will see that sdb boots before sda.

---

### Post by denis6902 on 2009-11-19
i have no idea whats going on with this grub or grub2, just being a PITA!!!

I Even manage to loose everything today, not even linux was booting anymore, thanks god **SUPERGRUB DISK** helped to get the linux working at least!

As soon as the pc is booting i get GRUB saying press ESC to options:
linux
linux recovery
win7
memtest

From there linux, and recovery run fine. But if i choose win7 i get:
**ERROR 12 - Invalid Device Requested&#8206;**

I am afraid that if i use Gpated live cd to delete swap and linux partition and install it again it wont solve my problem. It seems that there is something wrong with the lines for the Windows initialization. [B]

What do i do?[/B]
[B]Can someone Help me out Please!?
Should i just format everything?

***no peeps for this silly grub2, very confusing and difficult to use! [-X
[/B]previous versions of ubuntu were way easier to use with the old simple grub
its way to complicated for beginners like myself. ](*,)


Terminal:
$ **sudo fdisk -l:**
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00001e6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         261     2096451   82  Linux swap / Solaris
/dev/sda2             262        3133    23069340   83  Linux
/dev/sda3            3134       16187   104856255    7  HPFS/NTFS
/dev/sda4           16188      121601   846737955    5  Extended
/dev/sda5           16188      121601   846737923+   7  HPFS/NTFS

```Terminal:
**$ gksu gedit /boot/grub/menu.lst**

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        8

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=3379f60d-7a05-4747-865d-fb55be2ca6ad ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3379f60d-7a05-4747-865d-fb55be2ca6ad

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

title        Ubuntu 9.10
uuid        3379f60d-7a05-4747-865d-fb55be2ca6ad
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3379f60d-7a05-4747-865d-fb55be2ca6ad ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, (recovery mode)
uuid        3379f60d-7a05-4747-865d-fb55be2ca6ad
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3379f60d-7a05-4747-865d-fb55be2ca6ad ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Windows 7 Ultimate Loader
rootnoverify    (hd0,3)
makeactive
chainloader        +1
boot

title        Ubuntu 9.10, memtest86+
uuid        3379f60d-7a05-4747-865d-fb55be2ca6ad
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```



Please see my thread here: [http://ubuntuforums.org/showthread.php?t=1329839](http://ubuntuforums.org/showthread.php?t=1329839)

---

### Post by presence1960 on 2009-11-19
> **denis6902 said:**
> i have no idea whats going on with this grub or grub2, just being a PITA!!!

I Even manage to loose everything today, not even linux was booting anymore, thanks god **SUPERGRUB DISK** helped to get the linux working at least!

As soon as the pc is booting i get GRUB saying press ESC to options:
linux
linux recovery
win7
memtest

From there linux, and recovery run fine. But if i choose win7 i get:
**ERROR 12 - Invalid Device Requested&#8206;**

I am afraid that if i use Gpated live cd to delete swap and linux partition and install it again it wont solve my problem. It seems that there is something wrong with the lines for the Windows initialization. [B]

What do i do?[/B]
[B]Can someone Help me out Please!?
Should i just format everything?

***no peeps for this silly grub2, very confusing and difficult to use! [-X
[/B]previous versions of ubuntu were way easier to use with the old simple grub
its way to complicated for beginners like myself. ](*,)


Terminal:
$ **sudo fdisk -l:**
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00001e6e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         261     2096451   82  Linux swap / Solaris
/dev/sda2             262        3133    23069340   83  Linux
/dev/sda3            3134       16187   104856255    7  HPFS/NTFS
/dev/sda4           16188      121601   846737955    5  Extended
/dev/sda5           16188      121601   846737923+   7  HPFS/NTFS

```Terminal:
**$ gksu gedit /boot/grub/menu.lst**

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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        8

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
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
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
# kopt=root=UUID=3379f60d-7a05-4747-865d-fb55be2ca6ad ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3379f60d-7a05-4747-865d-fb55be2ca6ad

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

title        Ubuntu 9.10
uuid        3379f60d-7a05-4747-865d-fb55be2ca6ad
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3379f60d-7a05-4747-865d-fb55be2ca6ad ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, (recovery mode)
uuid        3379f60d-7a05-4747-865d-fb55be2ca6ad
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=3379f60d-7a05-4747-865d-fb55be2ca6ad ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Windows 7 Ultimate Loader
rootnoverify    (hd0,3)
makeactive
chainloader        +1
boot

title        Ubuntu 9.10, memtest86+
uuid        3379f60d-7a05-4747-865d-fb55be2ca6ad
kernel        /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```



Please see my thread here: [http://ubuntuforums.org/showthread.php?t=1329839](http://ubuntuforums.org/showthread.php?t=1329839)

It does not look like you have GRUB2 installed because you have a menu.lst which GRUB 2 does not have. We need more detailes info about your setup. Do this please:

Let's get a better look at your setup & boot process. Boot into Ubuntu. Come back here and use the link in my signature to download the Boot Info Script 0.34 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by denis6902 on 2009-11-19
i tried using this command but it gave me a invalid command message! :(

dont have linux anymore, i restored the mbr with win7 dvd

check my thread for more details: [http://ubuntuforums.org/showthread.php?t=1329839](http://ubuntuforums.org/showthread.php?t=1329839)

---

### Post by presence1960 on 2009-11-19
> **denis6902 said:**
> i tried using this command but it gave me a invalid command message! :(

dont have linux anymore, i restored the mbr with win7 dvd

check my thread for more details: [http://ubuntuforums.org/showthread.php?t=1329839](http://ubuntuforums.org/showthread.php?t=1329839)

Now I am confused!! If you do not have Linux any longer why did you post the output of sudo fdisk -l and display your menu.lst file when asking for help?

Maybe you can be more specific about what you are trying to accomplish and what exactly you have done to your machine.

---

### Post by presence1960 on 2009-11-19
if you want GRUB back see [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

After reading the other link I see that you restored Windows to MBR and you now want GRUB back there so you can boot both OSs. Follow that link for reinstalling GRUB from Live CD/USB

---

### Post by denis6902 on 2009-11-19
> **presence1960 said:**
> if you want GRUB back see [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD").

After reading the other link I see that you restored Windows to MBR and you now want GRUB back there so you can boot both OSs. Follow that link for reinstalling GRUB from Live CD/USB


will that restore grub2 or just the old good grub?

---

### Post by presence1960 on 2009-11-19
> **denis6902 said:**
> will that restore grub2 or just the old good grub?

that will install GRUB 2. GRUB 2 is good just different than GRUB Legacy

---

### Post by denis6902 on 2009-11-19
THATS RIGHT!

I want to have both WIN7 and karmic dual booting, but if i can i want to stay far away from grub2, far too complicated.

---

### Post by presence1960 on 2009-11-20
> **denis6902 said:**
> THATS RIGHT!

I want to have both WIN7 and karmic dual booting, but if i can i want to stay far away from grub2, far too complicated.

[http://ubuntuforums.org/showpost.php?p=8071880&postcount=18](http://ubuntuforums.org/showpost.php?p=8071880&postcount=18)

To remove GRUB 2 and install Legacy GRUB follow this

---

