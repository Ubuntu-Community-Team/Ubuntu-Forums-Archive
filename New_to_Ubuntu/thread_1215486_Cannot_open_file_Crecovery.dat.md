---
title: "Cannot open file C:recovery.dat"
date: 2009-07-17
forum: New to Ubuntu
---

### Post by linlearn on 2009-07-17
Hi experts,
I CANNOT OPEN Vista. I have installed Ubuntu 9.04 from a CD.
I have Vista Home Premium version and use an ASUS laptop. After installation of Ubuntu, I got the dual boot menu (Grub) Vista and Ubuntu. Going into Vista , gives a Grub error 22.
So, I re-installed Vista using recovery CD and driver CD (Bios setting to CD drive) , it gives 'NTLDR is missing' and then gives 'Grub error 22' error.
Then I had to re-install Ubuntu with guided partitioning and go into Vista loader . It gives me an error 'CANNOT OPEN FILE C:\RECOVERY.DAT' with a big red ERROR. 
So I had to re-install Ubuntu. 
I had done searches on google for GRub error 22 and recovery.dat . I have edited menu.lst so that Vista loads first but still I get a 'recovery.dat' error. 

I have downloaded boot_info_script032.sh file and using the code got the results.txt. 

The output of results.txt is as follows.
-------------
```

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Vista: Fat 32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /BOOTMGR /boot/bcd /BOOT/bcd /Boot/bcd 
                       /boot/BCD /BOOT/BCD /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 2048.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xbbc58b91

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    16,386,047    16,384,000  1c Hidden W95 FAT32 (LBA)
/dev/sda2    *     16,386,048   235,751,422   219,365,375   7 HPFS/NTFS
/dev/sda3         235,753,936   390,719,487   154,965,552   f W95 Ext d (LBA)
/dev/sda5         240,990,208   390,719,487   149,729,280   7 HPFS/NTFS
/dev/sda6         235,753,938   240,637,634     4,883,697  83 Linux
/dev/sda7         240,637,698   240,974,999       337,302  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: LABEL="RECOVERY" UUID="1489-5F00" TYPE="vfat" 
/dev/sda2: UUID="24942DE7942DBC64" LABEL="VistaOS" TYPE="ntfs" 
/dev/sda5: UUID="789830C9983087A0" LABEL="DATA" TYPE="ntfs" 
/dev/sda6: UUID="44e13094-0e3b-4a1b-84d5-b1ca30389e75" TYPE="ext3" 
/dev/sda7: UUID="4c4b1c29-733b-4725-a694-eb536978cb02" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda6 on / type ext3 (rw,relatime,errors=remount-ro)
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
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/sonroy/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=sonroy)
/dev/sda2 on /media/VistaOS type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)


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
# kopt=root=UUID=44e13094-0e3b-4a1b-84d5-b1ca30389e75 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=44e13094-0e3b-4a1b-84d5-b1ca30389e75

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
uuid        44e13094-0e3b-4a1b-84d5-b1ca30389e75
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=44e13094-0e3b-4a1b-84d5-b1ca30389e75 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        44e13094-0e3b-4a1b-84d5-b1ca30389e75
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=44e13094-0e3b-4a1b-84d5-b1ca30389e75 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        44e13094-0e3b-4a1b-84d5-b1ca30389e75
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title        Windows Vista (loader)
rootnoverify    (hd0,1)
savedefault
makeactive
chainloader    +1


=============================== sda6/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda6 during installation
UUID=44e13094-0e3b-4a1b-84d5-b1ca30389e75 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=4c4b1c29-733b-4725-a694-eb536978cb02 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda6: Location of files loaded by Grub: ===================


 122.1GB: boot/grub/menu.lst
 122.1GB: boot/grub/stage2
 121.4GB: boot/initrd.img-2.6.28-11-generic
 121.4GB: boot/vmlinuz-2.6.28-11-generic
 121.4GB: initrd.img
 121.4GB: vmlinuz
----------------------------------

```
 I am a beginner to Ubuntu.
Vista Recovery CD (given by ASUS)does not have recovery console so cannot use command line to do 'fixmbr' or fixboot.  
I copied Vista recovery.iso to CD,but I get an error 'cannot mount file'. So CD cannot open in Ubuntu.  

Can anyone help. I want to get into Vista .

Regards,
Linlearn

---

### Post by linlearn on 2009-07-18
Hi experts,
I hope I have not confused people by the long message. I just cant get into Vista when clicking on the Grub menu. then I get cannot open file C:\Recovery.dat. My recovery cd does not have the repair option.
That is the gist of it.
PLEASE HELP

linlearn

---

### Post by lisati on 2009-07-18
> **linlearn said:**
> Hi experts,
I hope I have not confused people by the long message. I just cant get into Vista when clicking on the Grub menu. then I get cannot open file C:\Recovery.dat. My recovery cd does not have the repair option.
That is the gist of it.
PLEASE HELP

linlearn

Possibly those who would have replied are stumped by the absence of a repair options....

You might find some ideas here: [http://asusg1s.wikidot.com/tips-and-tricks](http://asusg1s.wikidot.com/tips-and-tricks)

---

### Post by lkraemer on 2009-07-18
You probably need to start with a download of a Vista Recovery CD
for 32 bit or 64 Bit, depending on what is installed on your machine.
You MUST know this before you start.  It should be in your documentation.

[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

Guide:
[http://www.techhandbook.com/windows/3080-How-create-Vista-recovery-disk-and-rescue-Vista.html](http://www.techhandbook.com/windows/3080-How-create-Vista-recovery-disk-and-rescue-Vista.html)

You shouldn't need to continually install Ubuntu, just run it from the
LiveCD for the downloads, and with K3B installed you can burn the CDR's
needed.  

Next boot the proper (32 Bit vs 64 Bit) Vista Recovery CDR and let it do
it's thing.

Then boot the LiveCD of Ubuntu and use Gparted to check the Partitions,
making sure the Ubuntu partition still exists.  If it does, just
reinstall Grub.

If the Ubuntu partition is wiped, install Ubuntu.

Please refer to the Dual Boot site at:
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

And refer to Supergrub at:
[http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html](http://members.iinet.net.au/~herman546/SuperGrubDiskPage.html)

And refer to Testdisk at:
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)

It it were me I'd figure out exactly WHY I needed Vista, and if it
wasn't a real need, I'd stick in the LiveCD of Ubuntu, CrunchBang 9.04.1,
PCLinuxOS 2009.2, or sidux 2009.2, wipe the partitions, and start a fresh
install of my selected Distro and never look back.

You can always install VirtualBox (PUEL version) and then install
XP or Windows xx in VirtualBox, assuming you have enough RAM to
allow you to run the HOST and GUEST OS.  (I use 2 Gig with 693 for XP) 

Good Luck!

lkraemer

---

### Post by LewRockwell on 2009-07-18
SuperGrubDisk

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

.

---

### Post by linlearn on 2009-07-21
Hi guys ,
Thanks for the replies.
Lisati,
I have tried some of the Asus options. I have spoken to Asus yesterday and they are asking me to send it for repairs. That will take 10 working days. Thanks for the link. I will go through it fully.

Lkraemer,
[Windows Vista 32-Bit (x86) Recovery Disc Torrent]("http://neosmart.net:6969/torrent.html?info_hash=c7411cffb5b0c27b28d0ec080af55ea0016f7b7b")
[LEFT]I have tried that too. I have burned CD and somehow it does not boot with that after setting Bios to CD/DVD. Nothing happens. I have burned Supergru_[U]b _on to disc but all I get is a gru[/U]___b black screen interface._
__[/LEFT]
[U][U]If one knows how to use Ubuntu it is fine, I am having problems with 
1. Wireless . At present using ethernet cable to connect
2. Cant mount CD for burning
3. Not enough space.
 4. Setting printer.
It will take me time to understand Linux. I am reading a lot of forums.

I will do the test disk and try the virtual box.

[/U][/U][LewRockwell]("http://ubuntuforums.org/member.php?u=847166")

I have burned Superdisk and I dont get any fancy interface but a black command line interface with grub>


Thanks,
Linlearn

---

### Post by lkraemer on 2009-07-21
linlearn,
If you insert the Ubuntu LiveCD in the CD/DVD Drive, and boot you
should be able to get to a working system.  If this doesn't work,
try rebooting, and running Memtest from the LiveCD.

It sounds as if you either aren't making a valid CD when you burn,
or your system has other problems.  Try booting the CDR's you have
burned on another machine.  If they don't work then you will need to
burn them again, as it was defective.

FROM a UBUNTU LIVECD:
I suggest installing K3B, using SYSTEM -> ADMINISTRATION -> SYNAPTICS
from the pulldown menu.  Burn the ISO's as Disk at Once (DA0), at the
slowest speed displayed.  I always use CDRW's for the first burns/trials.
Be sure to VERIFY the MD5SUM's of the ISO's you download.  K3B will
recalculate the MD5SUMS and there is a file showing the MD5SUM's for
you to download when you downloaded the ISO.  And, you can try the
CDRW's you burned on several machines to make sure they boot.

SuperGrub, and the Windows Boot CDR's should boot fine, if not you
probably have a bad burn.

Until you get this figured out, don't mess with your Vista's partitions
for fear of making it worse.

lkraemer

---

### Post by linlearn on 2009-07-21
lkraeme,
I am going to do just that. I remember that the Brasero Burner stopped at checksum and did not do a thing. 
I will re-burn Vista and supergrub.

Linlearn

---

### Post by linlearn on 2009-07-22
Hi,
I have been having problems with 'not enough space' so cannot burn CD and 'cannot mount volume' errors. I was trying to mount manually and I abandoned it after resizing and moving.
I just managed to burn Vista recovery CD successfully. I ran it and got the language options. I could not get in. Still gives an error. I will read the forums. I will try from the command prompt and keep you posted.

linlearn

---

### Post by linlearn on 2009-07-22
I cannot get Vista working. I had burnt the CD from [http://neosmart.net/bslog/2008/window...disc-download/]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/"). I had used Bootrec.exe /FixMbr and Bootrec.exe /FixBoot in the command line.
This removed the Grub menu. I re-installed the recovery CD from ASUS and again did 'Repair the computer' but does not work. I think some file is corrupt. The error I get is Vista has to be re-installed.
The supergrub disc only shows a black  screen with 'grub>'

So now I will re-burn Supergrub and see what happens.

Linlearn

---

### Post by lkraemer on 2009-07-22
linlearn,
WOW, you have been having FUN....for the past several days......just to
get Vista running so you can get a Virus or two......and do it all over
again! Think of all the experience you are getting........

I'd much rather wipe the Hard Drive's Partition, insert the Ubuntu LiveCD,
install Ubuntu 9.04.1, or 8.04.3 LTS, and be up and running in less than
40 minutes.

Enough Already....you're killing me....!  WHEW!!!!

lkraemer

---

### Post by linlearn on 2009-07-24
lkraemer,
Thanks for helping me with this.:o
It is fun . yes. I just got the Supergrub CD done and it shows all the fancy options but still Windows does not boot. Like you said, I burnt the CD on the slowest speed. So now I doing the Vista recovery CD all over again. I really cant get into Vista.
Yes I learnt a lot from the forums. Too much of Ubuntu for me really.
I have learnt that Linux has a lot of programs ready for use unlike Windows. 
I have to learn how to make space. I cant get my head around Gparted. Wanted to create a root / but will do it later.
I will have to sort out the wireless on my Netgear router WPN824 as well. 
These two are for later.
Right now , reading about md5sum check for ISO and for the CD as well.
I am in ubuntu and with a wired internet connection.:)

Thanks,
Linlearn

---

### Post by linlearn on 2009-07-24
Hi Lkraemer, Lisati and LewRockwell,

I have given up.
lisati,lkraemer,lewrockwell thanks for your efforts.

I just cannot get into Vista.
I will get onto making wireless work on Netgear WPN824.
I guess I will open a new thread.

Cheers,
linlearnt

---

### Post by linlearn on 2009-08-07
Hi Guys,
I have SOLVED this issue finally the day before yesterday.
I followed the isntructions in the link [http://asusg1s.wikidot.com/tips-and-tricks](http://asusg1s.wikidot.com/tips-and-tricks) as given by lisati and it worked.
I have burned a lot of discs . Windows Vista Recovery Disc but it wont install as it comes up with an error 'Cannot find E:\Sources\\Install.wim'. This disc can only repair or maybe it was a bad burn. I have burned slowly many times at 4x,DAO using K3B and Brasero.
Super Grub does not help.

In case people want to know , follow the instructions . only insert ASUS RECOVERY disc first . Recover it to the first disc. DO NOT INSERT the asus DRIVER CD. Let it reboot, It does it 2 or 3 times. then you get a base Vista install. After that install the Driver CD.

Thanks to everyone for the help. 
I will come back to Linux (Ubuntu or Opensuse)after I read dual boot thoroughly. I have to understand what the GRUB menu does on clicking Vista loader. I got a GRUB error 22 and it kickstarted all the issues in Windows. I have lost all data as I tried to do recovery to both the discs. And the back up did not work in Vista anyway. XP was far better.

Thanks a lot,
Linlearn.

---

### Post by lexthoonen on 2010-07-02
Of course it's fun to blame microsoft for this, but it happens when you ask to install ubuntu next to vista. I, for example, need windows for Adobe Lightroom, and wasn't pleased to be presented with a huge red "ERROR" and a message saying Can not open file c:\recovery.dat after choosing vista from the grub menu for the first time since installing the new ubuntu.

I'm not panicking, it's all backed up, but it's still nasty. 

p.s. asus machine too.

---

### Post by linlearn on 2010-07-03
I wrote this thread in Aug 09.Vista has been a  real problem. even now it is. I cannot transfer data to an external drive , too as it says 'Semaphore timed out. It is not the case with XP
I am not using Ubuntu now a days , I am using Opensuse

---

