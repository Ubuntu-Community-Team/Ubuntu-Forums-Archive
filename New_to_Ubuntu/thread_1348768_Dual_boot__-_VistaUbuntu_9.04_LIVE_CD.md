---
title: "Dual boot  - Vista/Ubuntu 9.04 LIVE CD"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by altkon on 2009-12-07
Hi guys,
I have a laptop with Vista OS and I have installed Ubuntu 9.04 from a Live CD.
All worked fine but when I select VISTA (Loader), Vista begins to load, crashes and restarts the PC.
Cannot load in safe Mode, only option is to turn off PC.
How can I recover VISTA ???
To load Ubuntu I had resized my DATA partition and while booting I chose Automatic option.
Can someone guide me how to work around this problem.
Ubuntu works fine..
Thanks a lot

---

### Post by mörgæs on 2009-12-07
Is there enough empty space on the Windows partition?

---

### Post by u.b.u.n.t.u on 2009-12-07
So Ubuntu 9.04 starts fine but Vista has been corrupted, so that it will not boot, is that correct?

If so, then checking the boot loader in Ubuntu 9.04 would be the next step to see if if Vista is correctly there.

---

### Post by altkon on 2009-12-07
How can I**[B]**[/B] check the boot loader on Ubuntu 9.04 ??

As far space is concerned I had 3 partitions on my hard drive .
On the first one 54 GB Vista was installed and then I resized the second
data partition into one of 10GB and another of appx 44 GB.
Know I dont know what really happened because I chose the automatic option for the installation.

---

### Post by u.b.u.n.t.u on 2009-12-07
> **altkon said:**
> How can I**[B]**[/B] check the boot loader on Ubuntu 9.04 ??

I skipped that version and can only relate 9.10 to you. In Ubuntu 9.10 one needs to install this via synaptic, look for startupmanager, and install.

---

### Post by putu.sundika on 2009-12-07
> **u.b.u.n.t.u said:**
> So Ubuntu 9.04 starts fine but Vista has been corrupted, so that it will not boot, is that correct?

If so, then checking the boot loader in Ubuntu 9.04 would be the next step to see if if Vista is correctly there.

if VISTA was corrupt,why dont re-install VISTA ?

---

### Post by synapsys on 2009-12-07
If you have a Vista OS disc, I would recommend booting to that, run startup recovery, make sure that you can boot Vista. Then re-install grub from an Ubuntu live cd. There are countless tutorials on how to do this.

---

### Post by u.b.u.n.t.u on 2009-12-07
> **putu.sundika said:**
> if VISTA was corrupt,why dont re-install VISTA ?

There may be a less dramatic resolution to the problem.

---

### Post by altkon on 2009-12-08
> **u.b.u.n.t.u said:**
> I skipped that version and can only relate 9.10 to you. In Ubuntu 9.10 one needs to install this via synaptic, look for start up manager, and install.

Did it as instructed...the problem persists...I guess booting Vista from my Toshiba Product recovery disk becomes unavoidable.

If booting Vista is successful I don't know if I will take the risk for a Dual booting again from my LIVE CD. Because I am afraid something goes wrong with my partitions... although from what I saw Ubuntu now seats on the right partition of 44 GB which I had created leaving 36.4 GB free space.Vista seats on 54 GB leaving 12 GB free space and my DATA partition  seats on 10 GB leaving 4.6 GB free space.

I still cannot understand why my VISTA OS was corrupted...during the dual
boot execution..??:o

'

---

### Post by PRC09 on 2009-12-08
Before using the recovery disks backup everything on the drive as the restore disks return it to factory freshness......

---

### Post by candtalan on 2009-12-08
> **altkon said:**
> Did it as instructed...the problem persists...I guess booting Vista from my Toshiba Product recovery disk becomes unavoidable.

If booting Vista is successful I don't know if I will take the risk for a Dual booting again from my LIVE CD. Because I am afraid something goes wrong with my partitions... although from what I saw Ubuntu now seats on the right partition of 44 GB which I had created leaving 36.4 GB free space.Vista seats on 54 GB leaving 12 GB free space and my DATA partition  seats on 10 GB leaving 4.6 GB free space.

I still cannot understand why my VISTA OS was corrupted...during the dual
boot execution..??:o

'


Did you test running vista after your resize and before installing Ubuntu?

Did you defragment vista before changing partition size?

Did you get the live CD to do a self test for errors in the target PC CD drive before you installed?

When leaving some target space for Ubuntu to install (automatically) into, I trust that you left *unpartitioned* space for ubuntu on the drive? If you created a partiton, even an unformatted one, you may not have got ubuntu to go into it. Choose the install option to install into the 'largest unused (unpartitioned) space' on the drive.

You can verify the partitons on the PC by using the live CD again as live, and view using the partiton editor (gparted) in the system>administration menu, do not change anything, just investigate.

good luck

---

### Post by jsp21c on 2009-12-08
Hi, just joined this forum and wanted to share some info about restoring Vista.

The disk or recovery partition you have from the manufacturer is probably going to do a "factory reset", however Microsoft have released a bootable ISO which enables you to use the Windows Recovery Center ..... a feature which is standard on Vista Ultimate but not all of the other versions (possibly is on Pro but can't be certain)..... this isn't a Vista Installation disk, it's a recovery disk.

You'll have to read the article on neosmart.net [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and follow their instructions.

When you've burned the ISO, boot from it, select Language, Time & Currency and Keyboard layout, click "next" then select "Repair Your Computer". This should repair your Vista boot sequence however it will also probably mess up your Grub boot loader.

Personally I'm running Ubuntu 9.10 off a usb thumbdrive, dual booting seems to be just too messy. I'm planning on buying a PC just to run Linux next year because having one OS on one machine seems to be the safest option.

Hope this helps.

jsp21c.

---

### Post by altkon on 2009-12-11
> **u.b.u.n.t.u said:**
> There may be a less dramatic resolution to the problem.

andre@andre-laptop:~$ sudo fdisk -l
[sudo] password for andre: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb636fb14

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         192     1536000   27  Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2   *         192        7162    55990272    7  HPFS/NTFS
/dev/sda3            7488        8794    10485756    7  HPFS/NTFS
/dev/sda4            8795       14593    46580467+   5  Extended
/dev/sda5            8795       14350    44628538+  83  Linux
/dev/sda6           14351       14593     1951866   82  Linux swap / Solaris
andre@andre-laptop:~$ andre@andre-laptop:~$ sudo fdisk -l
andre@andre-laptop:~$: command not found
andre@andre-laptop:~$ [sudo] password for andre: 
[sudo]: command not found
andre@andre-laptop:~$ 
andre@andre-laptop:~$ Disk /dev/sda: 120.0 GB, 120034123776 bytes
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
andre@andre-laptop:~$ 255 heads, 63 sectors/track, 14593 cylinders
255: command not found
andre@andre-laptop:~$ Units = cylinders of 16065 * 512 = 8225280 bytes
No command 'Units' found, did you mean:
 Command 'units' from package 'units' (universe)
Units: command not found
andre@andre-laptop:~$ Disk identifier: 0xb636fb14
No command 'Disk' found, did you mean:
 Command 'risk' from package 'xfrisk' (universe)
Disk: command not found
andre@andre-laptop:~$ 
andre@andre-laptop:~$    Device Boot      Start         End      Blocks   Id  System
Device: command not found
andre@andre-laptop:~$ /dev/sda1               1         192     1536000   27  Unknown
bash: /dev/sda1: Permission denied
andre@andre-laptop:~$ Partition 1 does not end on cylinder boundary.
Partition: command not found
andre@andre-laptop:~$ /dev/sda2   *         192        7162    55990272    7  HPFS/NTFS
bash: /dev/sda2: Permission denied
andre@andre-laptop:~$ /dev/sda3            7488        8794    10485756    7  HPFS/NTFS
bash: /dev/sda3: Permission denied
andre@andre-laptop:~$ /dev/sda4            8795       14593    46580467+   5  Extended
bash: /dev/sda4: Permission denied
andre@andre-laptop:~$ /dev/sda5            8795       14350    44628538+  83  Linux
bash: /dev/sda5: Permission denied
andre@andre-laptop:~$ /dev/sda6           14351       14593     1951866   82  Linux swap / Solaris
bash: /dev/sda6: Permission denied
andre@andre-laptop:~$ andre@andre-laptop:~$ 
andre@andre-laptop:~$: command not found
andre@andre-laptop:~$ 

Could this information help to solve my problem??

---

### Post by mcdjork on 2009-12-11
If your bootloader is booting into the Vista partition all right (it sounds like you can at least get the Windows boot started because you chose to go into safe mode), there's not much you can do besides run the windows recovery. 

Vista and Windows 7 keep system files at some far-off random spot on the disk. It prevents you from resizing the partition to take advantage of space that you do actually have. Why? I don't know. Defragmenting with the windows software doesn't move them. You have to use another program like UltimateDefrag. I went throuh all kinds of steps to do this on my wife's computer. That's Windows for you. In your case, it's too late for that of course. If GParted resized your Vista partition, there's a very serious chance that your Windows drive has been corrupted. 

Run the Vista recovery, boot into Ubuntu Live and reinstall Grub. I think that's what you'll have to do.

---

### Post by altkon on 2009-12-12
> **candtalan said:**
> Did you test running vista after your resize and before installing Ubuntu?

Did you defragment vista before changing partition size?

Did you get the live CD to do a self test for errors in the target PC CD drive before you installed?

When leaving some target space for Ubuntu to install (automatically) into, I trust that you left *unpartitioned* space for ubuntu on the drive? If you created a partiton, even an unformatted one, you may not have got ubuntu to go into it. Choose the install option to install into the 'largest unused (unpartitioned) space' on the drive.

You can verify the partitons on the PC by using the live CD again as live, and view using the partiton editor (gparted) in the system>administration menu, do not change anything, just investigate.

good luck

Yes I test run Vista after resizing disk partitions, and it run OK.
No I did not a defragment except for the usual scan every first week of each month.i.e 3Dec 2009
No I did not do a self test  for errors before the installation.
There was plenty of empty space left.(Look at the "sudo fdisk -l"commend results that are shown on top of this reply.
Have tried to locate the partition editor fro system>administration menu but the only thing I foud was "Disk Utility" option.

---

### Post by candtalan on 2009-12-12
> 
There was plenty of empty space left.(Look at the "sudo fdisk -l"commend results that are shown on top of this reply. 
Space may not be the problem.

I note that sda1 and sda2 both seem to have the same start point
========
Device Boot Start End Blocks Id System
/dev/sda1 1 192 1536000 27 Unknown
Partition 1 does not end on cylinder boundary.
/dev/sda2 * 192 7162 55990272 7 HPFS/NTFS
/dev/sda3 7488 8794 10485756 7 HPFS/NTFS
/dev/sda4 8795 14593 46580467+ 5 Extended
/dev/sda5 8795 14350 44628538+ 83 Linux
/dev/sda6 14351 14593 1951866 82 Linux swap / Solaris
========
I am no expert, but I would first guess that this might screw up vista booting

> **altkon said:**
> Yes I test run Vista after resizing disk partitions, and it run OK.

good that suggests that the resize by itself did not cause a problem

>  No I did not a defragment except for the usual scan every first week of each month.i.e 3Dec 2009 
A defragment is useful to reduce chances of windows filesystem corruption when things get churned around, as in partition resize, although I have read it is not necessary. However, before I resize windows I do a defragment not once, but two times first. (Note that a scan is a different thing from a defragment).

>  No I did not do a self test for errors before the installation.
A CD self test in the problem PC can be done even now at this late stage, to indicate if both your CD is good and is being seen correctly by the target CD drive. Just boot from the live cd and choose 'Check CD for errors'. It checks two things - the CD itself and the CD drive.


>  Have tried to locate the partition editor fro system>administration menu but the only thing I foud was "Disk Utility" option.

gparted (or partition editor) is in the running live CD menu
System>administration menu, 
but you must be running the live CD. It is not found after the installation (unless you deliberately install it later)

hth

---

### Post by altkon on 2009-12-13
Hello candtalan

Can I boot on the Live CD by just hitting on the "autorun.inf" icon
figuring on the cdrom - file browser??? when I insert my Live CD while
I am logged into Ubuntu.!!! Or should I press onto "Install" icon.

All this because I dont want to configure by pressing the F2 setup after I hit on Windows Loader at start up.



/media/cdrom0/autorun.inf

---

### Post by altkon on 2009-12-13
A screen shot of my CD file browser

/home/andre/Desktop/Screenshot-1.png

---

### Post by macmaster on 2009-12-13
Mount the vista filesystem on ubuntu and backup any files and try reinstalling vista. To find out what ubuntu did with the partitions get an application called GParted.


Vista is the worst OS that ever existed.

---

### Post by altkon on 2009-12-13
> **macmaster said:**
> Mount the vista filesystem on ubuntu and backup any files and try reinstalling vista. To find out what ubuntu did with the partitions get an application called GParted.




Vista is the worst OS that ever existed.

I reckon there are plenty of GParted applications like (GParted Live Cd or GParted Vista or GParted Ubuntu) Which one is suitable for my case??

---

### Post by candtalan on 2009-12-13
> **altkon said:**
> Hello candtalan

Can I boot on the Live CD by just hitting on the "autorun.inf" icon
figuring on the cdrom - file browser??? when I insert my Live CD while
I am logged into Ubuntu.!!! Or should I press onto "Install" icon.

All this because I dont want to configure by pressing the F2 setup after I hit on Windows Loader at start up.
/media/cdrom0/autorun.inf

No. You boot from the live CD by putting the cd into the drive, then turning the PC off. Then starting the PC again. The PC will start to boot only from the CD. First you see a choice of language. Then you see a simple menu. 

If this does not seem to be happening then then other adjustments are needed first.
hth

---

### Post by presence1960 on 2009-12-13
Before you go reinstalling and changing things...

Did you use Vista's disk management utility to shrink Vista to create space for Ubuntu? If not that is why you are having a problem (see [here]("http://bugzilla.gnome.org/show_bug.cgi?id=379482")) coupled with the fact you did not defrag Windows at least once or twice prior to installing Ubuntu.

The fix for this should be easy but I want to be sure of exactly what you got on your setup & boot process first because of all the fiddling around you may have done. 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

Once I get this info I can most likely give you clear, precise instructions on how to get your machine working again without wiping or reinstalling anything.

---

### Post by altkon on 2009-12-14
> **candtalan said:**
> No. You boot from the live CD by putting the cd into the drive, then turning the PC off. Then starting the PC again. The PC will start to boot only from the CD. First you see a choice of language. Then you see a simple menu. 

If this does not seem to be happening then then other adjustments are needed first.
hth

Tried your method but PC does not boot from the Live/CD,but thru the boot loader as usual.
Please give me details for other adjustments.

---

### Post by presence1960 on 2009-12-14
> **altkon said:**
> Tried your method but PC does not boot from the Live/CD,but thru the boot loader as usual.
Please give me details for other adjustments.

You need to go into BIOS (referred to as Setup on some computers). You need to hit a key to get into it. That key will be specific to your make & model computer. Mine is the delete key. If you are not sure which key it is refer to your machine's documentation. If you do not have that then go to your manufacturer's website and download the manual for your model.

Once in BIOS you will need to set the CD/DVD drive as first in the boot order. This will allow you to boot from CD/DVDs.

If you have a Dell I believe you can hit F12 to access a menu to change the device boot order. This will be a one time change only. If you want to make it permanent you must go in BIOS.

---

### Post by altkon on 2009-12-14
Here is the text output of boot_info_script as requested by presence1960:

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
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
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda6: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xb636fb14

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048     3,074,047     3,072,000  27 Hidden HPFS/NTFS
/dev/sda2    *      3,074,048   115,054,591   111,980,544   7 HPFS/NTFS
/dev/sda3         120,293,376   141,264,887    20,971,512   7 HPFS/NTFS
/dev/sda4         141,275,610   234,436,544    93,160,935   5 Extended
/dev/sda5         141,275,673   230,532,749    89,257,077  83 Linux
/dev/sda6         230,532,813   234,436,544     3,903,732  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="6A8C441C8C43E0E5" LABEL="WinRE" TYPE="ntfs" 
/dev/sda2: UUID="4E10479310478147" LABEL="Vista" TYPE="ntfs" 
/dev/sda3: UUID="32164C28164BEC03" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="78504b60-b223-4d9f-babd-b1a96083a2c8" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="acd5aefe-74cb-4729-94eb-26a19d5cacd9" 

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
# kopt=root=UUID=78504b60-b223-4d9f-babd-b1a96083a2c8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=78504b60-b223-4d9f-babd-b1a96083a2c8

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

title		Ubuntu 9.10, kernel 2.6.31-16-generic
uuid		78504b60-b223-4d9f-babd-b1a96083a2c8
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=78504b60-b223-4d9f-babd-b1a96083a2c8 ro quiet splash 
initrd		/boot/initrd.img-2.6.31-16-generic
quiet

title		Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid		78504b60-b223-4d9f-babd-b1a96083a2c8
kernel		/boot/vmlinuz-2.6.31-16-generic root=UUID=78504b60-b223-4d9f-babd-b1a96083a2c8 ro  single
initrd		/boot/initrd.img-2.6.31-16-generic

title		Ubuntu 9.10, kernel 2.6.28-11-generic
uuid		78504b60-b223-4d9f-babd-b1a96083a2c8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=78504b60-b223-4d9f-babd-b1a96083a2c8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid		78504b60-b223-4d9f-babd-b1a96083a2c8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=78504b60-b223-4d9f-babd-b1a96083a2c8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.10, memtest86+
uuid		78504b60-b223-4d9f-babd-b1a96083a2c8
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
rootnoverify	(hd0,1)
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
UUID=78504b60-b223-4d9f-babd-b1a96083a2c8 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=acd5aefe-74cb-4729-94eb-26a19d5cacd9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 102.4GB: boot/grub/menu.lst
 102.4GB: boot/grub/stage2
 102.4GB: boot/initrd.img-2.6.28-11-generic
 102.4GB: boot/initrd.img-2.6.31-16-generic
 102.5GB: boot/vmlinuz-2.6.28-11-generic
 102.5GB: boot/vmlinuz-2.6.31-16-generic
 102.4GB: initrd.img
 102.5GB: vmlinuz
```

Hope this helps!!

---

### Post by presence1960 on 2009-12-14
The output from the script looks OK. The only thing I can think of is your Vista bootloader is borked. You can try restoring Vista's bootloader then restore GRUB.

You don't have a Vista install DVD so go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download the iso for your version of Vista (32 or 64 bit) Burn it to CD as an image and then boot from that CD. This will allow you to use Vista Recovery Console(sorry you can't install Vista with this CD).

Once you boot the CD follow the directions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista -scroll down to see them. When completed reboot & you should boot right to Vista.

Now boot the 9.04 Live CD. Do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

You should be good to go!

---

### Post by altkon on 2009-12-14
Hi Presence 1960

Thanks for your quick reply.
```
You can try restoring Vista's bootloader then restore GRUB.
```
How can I restore Vista's bootloader??

```
You don't have a Vista install DVD so go here and download the iso for your version of Vista (32 or 64 bit) Burn it to CD as an image and then boot from that CD. This will allow you to use Vista Recovery Console(sorry you can't install Vista with this CD).
```


I happen to have the Product Recovery Disk by Toshiba for Windows Vista 
Home Premium 32 bit.
Can I go ahead and use it iso downloading from Internet.
aa

---

### Post by presence1960 on 2009-12-14
> **altkon said:**
> 

I happen to have the Product Recovery Disk by Toshiba for Windows Vista 
Home Premium 32 bit.
Can I go ahead and use it iso downloading from Internet.
aa

I would use the CD you make from the  iso just in case your Recovery Disk does not include Recovery Console like a lot do not. This way there will be no mistakes and you won't lose any data by restoring your hard disk back to the factory image which is what Recovery Disks/partitions do.

This (from my previous post) is how you restore Vista bootloader:

> Once you boot the CD follow the directions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista -scroll down to see them. When completed reboot & you should boot right to Vista.

---

### Post by altkon on 2009-12-18
> **presence1960 said:**
> The output from the script looks OK. The only thing I can think of is your Vista bootloader is borked. You can try restoring Vista's bootloader then restore GRUB.

You don't have a Vista install DVD so go [here]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") and download the iso for your version of Vista (32 or 64 bit) Burn it to CD as an image and then boot from that CD. This will allow you to use Vista Recovery Console(sorry you can't install Vista with this CD).

Once you boot the CD follow the directions [here]("http://ubuntuforums.org/showthread.php?t=1014708") for Vista -scroll down to see them. When completed reboot & you should boot right to Vista.

Now boot the 9.04 Live CD. Do this:

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,4)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,4)"
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.
```

You should be good to go!

Hi, 

Unfortunately restoring the Vista bootloader was unsuccessful. Even after following the steps you described and fixing the Vista bootloader and MBR, the problem persists. Flash of BSOD and restart when loading Vista. Also, as before, starting in Safe Mode results in a failure with only an option to switch off computer.

I was however able to restore the GRUB bootloader as per your steps above and I'm back using the Ubuntu, which is nice. Thank you for your suggestions.

Do you think there is any reason to attempt this with my Toshiba product Vista recovery CD ? Also, can you think of any other reason (given the output of the boot script above) that this problem has arisen? Is it possible that the Vista installation has become corrupted beyond repair?

Thanks for your steps above, though and any other assistance with this fault is very very much appreciated.

---

### Post by presence1960 on 2009-12-18
> **altkon said:**
> Hi, 

Unfortunately restoring the Vista bootloader was unsuccessful. Even after following the steps you described and fixing the Vista bootloader and MBR, the problem persists. Flash of BSOD and restart when loading Vista. Also, as before, starting in Safe Mode results in a failure with only an option to switch off computer.

I was however able to restore the GRUB bootloader as per your steps above and I'm back using the Ubuntu, which is nice. Thank you for your suggestions.

Do you think there is any reason to attempt this with my Toshiba product Vista recovery CD ? Also, can you think of any other reason (given the output of the boot script above) that this problem has arisen? Is it possible that the Vista installation has become corrupted beyond repair?

Thanks for your steps above, though and any other assistance with this fault is very very much appreciated.
If you use the recovery partition/CD it will most likely restore your hard disk to the factory image wiping everything off in the process. If Windows is that important to you then you will have no other choice. Make sure your data is backed up first.

---

### Post by altkon on 2009-12-18
```
If you use the recovery partition/CD it will most likely restore your hard disk to the factory image wiping everything off in the process. 

```

By the recovery partition/CD dou you mean my Toshiba Product Recovery disk??
or something else !!! please clarify !!!
What about my partitions should I resize and how??? 
I don't mind loosing all my files as long as I can recover Vista on Dual boot with Ubuntu.
Thanks a lot for your guidance.

---

### Post by JayKay3000 on 2009-12-18
If you use the recovery cd (toshiba) that came with your pc then in theory it should restore it to the factory settings.

In other words. It will restore it to the original vista instalation you had when you first used the computer out of the box.

Thus wiping everything off the disk that is on there currently.

If you have the Vista disk I would re-install vista and wipe the computer.

Then re-install ubuntu as a duel boot.

---

### Post by altkon on 2009-12-18
> **JayKay3000 said:**
> If you use the recovery cd (toshiba) that came with your pc then in theory it should restore it to the factory settings.

In other words. It will restore it to the original vista instalation you had when you first used the computer out of the box.

Thus wiping everything off the disk that is on there currently.

If you have the Vista disk I would re-install vista and wipe the computer.

Then re-install ubuntu as a duel boot.

```
Then re-install ubuntu as a dual boot.

```
To do that I will have to resize my partitions first.
Last time I did this prior to booting With the Ubuntu live Cd without using gdpart option but the Windows resizing feature.
Now I am afraid to repeat the same mistake after which I had my VISTA OS corrupted.
Would you prefer that I resize my partitions now from within Ubuntu Live CD gdpart option and not the Windows Vista resize feature??
Please comment....

---

### Post by oldfred on 2009-12-18
I would suggest trying this:

meierfra. was one of the major contributors to the script and is very knowledgable.
[http://ubuntuforums.org/showthread.php?t=1350824](http://ubuntuforums.org/showthread.php?t=1350824)   meierfra. post 10 on repair of Vista
I agree. But I recommend to use testdisk to fix your boot sector. (Vista's "fixboot" usually only repairs the boot code in the boot sector, but not the boot parameters)

Also microsoft's version has more commands to try:
How to restore the Windows Vista bootloader
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

If you used gparted and did not unchecked the box it can cause problems:
starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)

---

### Post by joes7 on 2009-12-18
There should be no problem at all, if your PC is decent.

---

### Post by altkon on 2009-12-20
> **candtalan said:**
> Did you test running vista after your resize and before installing Ubuntu?

Did you defragment vista before changing partition size?

Did you get the live CD to do a self test for errors in the target PC CD drive before you installed?

When leaving some target space for Ubuntu to install (automatically) into, I trust that you left *unpartitioned* space for ubuntu on the drive? If you created a partiton, even an unformatted one, you may not have got ubuntu to go into it. Choose the install option to install into the 'largest unused (unpartitioned) space' on the drive.

You can verify the partitons on the PC by using the live CD again as live, and view using the partiton editor (gparted) in the system>administration menu, do not change anything, just investigate.

good luck


```
You can verify the partitons on the PC by using the live CD again as live, and view using the partiton editor (gparted) in the system>administration menu, do not change anything, just investigate.
```

My investigation revealed that there are now 9 partitions on my HDD
dev/sda 111.79 GIB as follows 1.unallocated 1 mib 2.dev/sda1 ntfs winre
1.46 Gib 3. dev/sda2 ntfs Vista 53.40 GIB (boot) 4.Unallocated 2.50 GIB
5.dev/sda3 ntfs data 10 GIB 6.unullocated 5.24 MIB 7.dev/sda4 extended 
44.42 GIB 8.dev/sda5 ext3 42.56 GIB 9.dev/sda6 linux/swap 1.86 GIB

I have a screen print for all these but unfortunately I cannot copy
or attach even as a private message to you.

As you know all my efforts to restore the Vista boot loader were
unsuccessful.

Based on my above findings please come up with some bright proposal.

Thanks

---

### Post by presence1960 on 2009-12-20
> **altkon said:**
> ```
You can verify the partitons on the PC by using the live CD again as live, and view using the partiton editor (gparted) in the system>administration menu, do not change anything, just investigate.
```

My investigation revealed that there are now 9 partitions on my HDD
dev/sda 111.79 GIB as follows 1.unallocated 1 mib 2.dev/sda1 ntfs winre
1.46 Gib 3. dev/sda2 ntfs Vista 53.40 GIB (boot) 4.Unallocated 2.50 GIB
5.dev/sda3 ntfs data 10 GIB 6.unullocated 5.24 MIB 7.dev/sda4 extended 
44.42 GIB 8.dev/sda5 ext3 42.56 GIB 9.dev/sda6 linux/swap 1.86 GIB

I have a screen print for all these but unfortunately I cannot copy
or attach even as a private message to you.

As you know all my efforts to restore the Vista boot loader were
unsuccessful.

**_Based on my above findings please come up with some bright proposal._**

Thanks

You really have a mess there! At this point I would restore my machine back to the factory image using your restore disk(s). Next time prior to installing Ubuntu I would do some reading on installing Ubuntu as a dual boot & partitioning. Here are some links:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

In reference to the above bold & underlined: The brightest thing I can come up with is use Windows, then spend some time to increase your knowledge about installing OSs, partitioning & give it another go when you are ready. That is as bright as it can get.:rolleyes:

---

### Post by meierfra. on 2009-12-20
Before a "factory reinstalling"  I suggest to run a file system check  and  start up repair on your Vista partition.

Boot from the Visa CD and go the command prompt as before. 

(If you have problems getting to the command prompt:
At the first screen select your favorite language.
At the second screen, select "Install Now"
At the third screen, press  "Shift F10".)

Type 
```
 diskpart
``` and then at the  'diskpart' prompt:

```
 list volume
```

This will list the drive letters for all  the 'NTFS' and 'Fat' partitions on your computer.  Determine the drive letter for your Vista partition. 
Type

```
 exit
``` to exit the "diskpart" prompt.


Type 

```
chkdsk C: /r

```
but replace "C:" by the drive letter of your Vista partition.


Run chkdsk several times, until no more errors are detected.

If you still cannot boot into Vista, run a "Start up Repair":

Boot from you Vista Recovery CD.
At the first screen select your favorite language.
At the second screen choose your operating system.
At the third screen choose "Repair your Computer".
If a pop windows appears, offering  to repair a problem with the "Startup options",   click on "Repair and restart".
Otherwise  choose "Startup Repair" at the next screen.

"Startup Repair" tends to fix one problem at the time. So you might have to run "Startup Repair" several times.

---

### Post by altkon on 2009-12-20
meierfra.
```
Before a "factory reinstalling" I suggest to run a file system check and start up repair on your Vista partition.

Boot from the Visa CD and go the command prompt as before. 

(If you have problems getting to the command prompt:
At the first screen select your favorite language.
At the second screen, select "Install Now"
At the third screen, press "Shift F10".)
```

By Visa CD do you mean the Toshiba product Recovery Disk
that I have or the Windows Vista Recovery disk I downloaded
and burned on a Live CD from Neo Smart site.

---

### Post by meierfra. on 2009-12-20
Windows Vista Recovery disk you downloaded.

---

### Post by altkon on 2009-12-21
> **meierfra. said:**
> Before a "factory reinstalling"  I suggest to run a file system check  and  start up repair on your Vista partition.

Boot from the Visa CD and go the command prompt as before. 

(If you have problems getting to the command prompt:
At the first screen select your favorite language.
At the second screen, select "Install Now"
At the third screen, press  "Shift F10".)

Type 
```
 diskpart
``` and then at the  'diskpart' prompt:

```
 list volume
```

This will list the drive letters for all  the 'NTFS' and 'Fat' partitions on your computer.  Determine the drive letter for your Vista partition. 
Type

```
 exit
``` to exit the "diskpart" prompt.


Type 

```
chkdsk C: /r

```
but replace "C:" by the drive letter of your Vista partition.


Run chkdsk several times, until no more errors are detected.

If you still cannot boot into Vista, run a "Start up Repair":

Boot from you Vista Recovery CD.
At the first screen select your favorite language.
At the second screen choose your operating system.
At the third screen choose "Repair your Computer".
If a pop windows appears, offering  to repair a problem with the "Startup options",   click on "Repair and restart".
Otherwise  choose "Startup Repair" at the next screen.

"Startup Repair" tends to fix one problem at the time. So you might have to run "Startup Repair" several times.

Hi meierfra.
Just now finished running twice my file system check and
my Vista partition up and running again.
So back to business as usual now as both systems Vista/Ubuntu
healthy and running.
Only that I lost my Wireless connection on Vista, but I will
work on it to restore everything to normal.

I owe you a lot for guiding me thru this messed up situation.
Similarly I would like to thank all the other Community Members
who gave a helping hand to resolve this issue.

A million of thanks to all...:)

Best regards,

Andre

---

### Post by meierfra. on 2009-12-21
> Just now finished running twice my file system check and
my Vista partition up and running again.
Great. Have fun with Vista and Ubuntu

---

### Post by altkon on 2009-12-23
> **presence1960 said:**
> You really have a mess there! At this point I would restore my machine back to the factory image using your restore disk(s). Next time prior to installing Ubuntu I would do some reading on installing Ubuntu as a dual boot & partitioning. Here are some links:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)

In reference to the above bold & underlined: The brightest thing I can come up with is use Windows, then spend some time to increase your knowledge about installing OSs, partitioning & give it another go when you are ready. That is as bright as it can get.:rolleyes:

```
In reference to the above bold & underlined: The brightest thing I can come up with is use Windows, then spend some time to increase your knowledge about installing OSs, partitioning & give it another go when you are ready. That is as bright as it can get.:rolleyes
```

Hi!! presence1960.
I followed your advice and I spend all this time trying to educate myself reading the tutorials you have suggested.
Nevertheless I failed to spot my wrong doings so as to find my mistakes.
As a novice I followed step by step the instructions contained in the following link.
[http://www.addictivetips.com/windows-tips/extend-or-expand-volume-of-windows-partition-in-vista/](http://www.addictivetips.com/windows-tips/extend-or-expand-volume-of-windows-partition-in-vista/)

And I succeeded to create some healthy partitions and after a "fdisk check for errors" to restore my Vista System which is now up and running without having lost any files and data.
The reason I bring back this issue is in order to spot my wrong doings and mistakes, which as a novice I cannot visualize.
Please bear with me for this and don't misunderstand me.
As I owe you a lot for the happy solution we have reached and accomplished.:)

---

### Post by presence1960 on 2009-12-23
> **altkon said:**
> ```
In reference to the above bold & underlined: The brightest thing I can come up with is use Windows, then spend some time to increase your knowledge about installing OSs, partitioning & give it another go when you are ready. That is as bright as it can get.:rolleyes
```

Hi!! presence1960.
I followed your advice and I spend all this time trying to educate myself reading the tutorials you have suggested.
Nevertheless I failed to spot my wrong doings so as to find my mistakes.
As a novice I followed step by step the instructions contained in the following link.
[http://www.addictivetips.com/windows-tips/extend-or-expand-volume-of-windows-partition-in-vista/](http://www.addictivetips.com/windows-tips/extend-or-expand-volume-of-windows-partition-in-vista/)

And I succeeded to create some healthy partitions and after a "fdisk check for errors" to restore my Vista System which is now up and running without having lost any files and data.
The reason I bring back this issue is in order to spot my wrong doings and mistakes, which as a novice I cannot visualize.
Please bear with me for this and don't misunderstand me.
As I owe you a lot for the happy solution we have reached and accomplished.:)

You are not misunderstood. Glad you got Vista up & running. BTW meierfra is very knowledgeable and is one of a few people I look to in their posts to help me in gaining more knowledge. He and caljohnsmith were instrumental in my learning a little about boot process. The boot info script (courtesy of meierfra) I believe is one of the best tools we have to troubleshoot most boot issues. Sometimes we need to take a breather and step back and do some brushing up or maybe even some learning before proceeding again. I know that is how it went for me. My first attempt at installing Ubuntu was a disaster and I lost everything on my hard disk. Good thing I do incremental backups each week, so I had still had a copy of all my data on an external disk. But needless to say installing windows again is a major chore unlike linux and I was mad! I blamed Ubuntu (lol). But I continued to come back to the forum from Windows and I got some links and info to read. I took the next two or so weeks reading and absorbing all that. When I next tried to install a dual boot I for the most part understood and was familiar with a lot of what was necessary to do because I had done the prep work prior. I wasn't trying to be a wise guy by suggesting reading some material. In my opinion that was what I thought you needed to do before proceeding again.

---

### Post by altkon on 2010-03-30
> **meierfra. said:**
> Before a "factory reinstalling"  I suggest to run a file system check  and  start up repair on your Vista partition.

Boot from the Visa CD and go the command prompt as before. 

(If you have problems getting to the command prompt:
At the first screen select your favorite language.
At the second screen, select "Install Now"
At the third screen, press  "Shift F10".)

Type 
```
 diskpart
``` and then at the  'diskpart' prompt:

```
 list volume
```

This will list the drive letters for all  the 'NTFS' and 'Fat' partitions on your computer.  Determine the drive letter for your Vista partition. 
Type

```
 exit
``` to exit the "diskpart" prompt.


Type 

```
chkdsk C: /r

```
but replace "C:" by the drive letter of your Vista partition.


Run chkdsk several times, until no more errors are detected.

If you still cannot boot into Vista, run a "Start up Repair":

Boot from you Vista Recovery CD.
At the first screen select your favorite language.
At the second screen choose your operating system.
At the third screen choose "Repair your Computer".
If a pop windows appears, offering  to repair a problem with the "Startup options",   click on "Repair and restart".
Otherwise  choose "Startup Repair" at the next screen.

"Startup Repair" tends to fix one problem at the time. So you might have to run "Startup Repair" several times.

hI!!meierfra
It is me again...
Unfortunately my dual  booting system this time lost the Windows Vista
Loader and when I try to looad from another system Except Ubuntu it fails
to do so indicating an error.
Can I apply the same procedure as you had suggested  abovein order to recover my Windows Vista Loader again.
Thanks a lot.
Regards,
Andre

---

### Post by altkon on 2010-03-30
To be more specific when I try to boot from other operating system
it shows error 11 Unrecognized device string

---

### Post by altkon on 2010-03-30
Please disregard my query as at second atempt when I scrolled down the the existing options the Windows Vista Loader showed up.
Therefore no problem any more.
Please consider the case as not existing.
Thanks a lot.
Regards,
Andre

---

