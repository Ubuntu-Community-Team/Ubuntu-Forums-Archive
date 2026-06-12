---
title: "GRUB not loading XP after install"
date: 2009-10-06
forum: New to Ubuntu
---

### Post by jimhoff on 2009-10-06
I've read many forum posts and web pages about restoring the grub menu after installing XP, but my lack of knowledge is giving me problems when trying to apply the general steps to my specific problem. I you, the experts, could help me.

I installed XP on a partition on my ubuntu laptop. XP ran fine, and then I restored the GRUB menu and now cannot boot XP.

After booting from a flash drive, I was able to configure GRUB and I typed

 root (hd0,0) 
 setup (hd0) 
 quit 
 exit 

Then I edited menu.lst to add 

title Windows XP 
root (hd0,1) 
makeactive 
chainloader +1 

Right before the end line (### END DEBIAN AUTOMAGIC KERNELS LIST)

When I reboot the computer XP is on the GRUB list, but if I choose it nothing happens. 

I think the problem lies in the (hd0,1) part, but I'm not sure what exactly those characters refer to or how to find out what they should be.

Could anyone help me with this?

Thanks

---

### Post by keygiwawah on 2009-10-06
I don't know much about that, but just had a thought... It might be something wrong with your Master Boot Record. You might be able to try and repair it with super grub... I don't think you can hurt anything if it's not in the MBR.

---

### Post by oldos2er on 2009-10-06
Can you boot to Ubuntu, and post the output of this command here?
```
sudo fdisk -l
```

---

### Post by jimhoff on 2009-10-06
Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2020    16225618+  83  Linux
/dev/sda2   *        2021        6992    39937590    7  HPFS/NTFS
/dev/sda3            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris

Disk /dev/mmcblk0: 1017 MB, 1017643008 bytes
29 heads, 60 sectors/track, 1142 cylinders
Units = cylinders of 1740 * 512 = 890880 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1        1143      993667+   6  FAT16

---

### Post by rbc on 2009-10-06
I do not have an answer to your problem, but since you (sort of) asked for an explanation….

hd(x,y)

x=hard drive number (starting with zero)
y=partition number (starting with zero)

---

### Post by jimhoff on 2009-10-06
Okay, so my windows partition is /dev/sda2 then. So then do I edit /grub/menu.lst to read 

title Windows XP 
root (hd0,2) 
makeactive 
chainloader +1 

to get it to boot xp?

Edit:  I tried that and when I tried to boot XP I got the message: Error 12: invalid device requested

---

### Post by arrange on 2009-10-06
Could you post the output of [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/") here?

Also - did you have XP on *sda2* before you made the changes (when it worked)?

---

### Post by jimhoff on 2009-10-06
I've downloaded that script, how would I go about running it?

And yes, I think I had it on sda2.

---

### Post by arrange on 2009-10-06
see
[http://sourceforge.net/docman/display_doc.php?docid=137292&group_id=250055](http://sourceforge.net/docman/display_doc.php?docid=137292&group_id=250055)

---

### Post by halitech on 2009-10-06
if windows was on partition sda2 then you would enter it as (0,1) in grub as the first partition would be (0,0) as grub starts from 0 (as noted above by rbc)

---

### Post by lindsay7 on 2009-10-06
In order to get a clearer picture of your setup, how about booting your Ubuntu Live CD (the Ubuntu install CD), download the Boot Info Script to the Live CD desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:

Code:
sudo bash ~/Desktop/boot_info_script*.sh
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup.

---

### Post by lindsay7 on 2009-10-06
> **jimhoff said:**
> I've read many forum posts and web pages about restoring the grub menu after installing XP, but my lack of knowledge is giving me problems when trying to apply the general steps to my specific problem. I you, the experts, could help me.

I installed XP on a partition on my ubuntu laptop. XP ran fine, and then I restored the GRUB menu and now cannot boot XP.

After booting from a flash drive, I was able to configure GRUB and I typed

 root (hd0,0) 
 setup (hd0) 
 quit 
 exit 

Then I edited menu.lst to add 

title Windows XP 
root (hd0,1) 
makeactive 
chainloader +1 

Right before the end line (### END DEBIAN AUTOMAGIC KERNELS LIST)

When I reboot the computer XP is on the GRUB list, but if I choose it nothing happens. 

I think the problem lies in the (hd0,1) part, but I'm not sure what exactly those characters refer to or how to find out what they should be.

Could anyone help me with this?

Thanks


You said "Right before the end line (### END DEBIAN AUTOMAGIC KERNELS LIST)"


The lines setting up Windows needs to be after "##End Debian....." in your grub menu.

---

### Post by jimhoff on 2009-10-06
Here's the results.txt

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    32,451,299    32,451,237  83 Linux
/dev/sda2    *     32,451,300   112,326,479    79,875,180   7 HPFS/NTFS
/dev/sda3         112,326,480   117,210,239     4,883,760   5 Extended
/dev/sda5         112,326,543   117,210,239     4,883,697  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="eb31226b-8486-4929-a6fa-113cf503415a" TYPE="ext3" 
/dev/sda2: UUID="FCD800A7D800626E" TYPE="ntfs" 
/dev/sda5: UUID="a48e917d-1ad2-41bb-acbc-3404db4d3c3b" TYPE="swap" 
/dev/mmcblk1p1: SEC_TYPE="msdos" UUID="FC30-3DA9" TYPE="vfat" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
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
/home/jimhoff/.Private on /home/jimhoff type ecryptfs (ecryptfs_sig=8e803568c482f037,ecryptfs_fnek_sig=f57647ea21723016,ecryptfs_cipher=aes,ecryptfs_key_bytes=16)
gvfs-fuse-daemon on /home/jimhoff/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=jimhoff)
/dev/mmcblk1p1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)


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
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
# hiddenmenu

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
# kopt=root=UUID=eb31226b-8486-4929-a6fa-113cf503415a ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=eb31226b-8486-4929-a6fa-113cf503415a

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

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        eb31226b-8486-4929-a6fa-113cf503415a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=eb31226b-8486-4929-a6fa-113cf503415a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        eb31226b-8486-4929-a6fa-113cf503415a
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=eb31226b-8486-4929-a6fa-113cf503415a ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        eb31226b-8486-4929-a6fa-113cf503415a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=eb31226b-8486-4929-a6fa-113cf503415a ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        eb31226b-8486-4929-a6fa-113cf503415a
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=eb31226b-8486-4929-a6fa-113cf503415a ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        eb31226b-8486-4929-a6fa-113cf503415a
kernel        /boot/memtest86+.bin
quiet


### END DEBIAN AUTOMAGIC KERNELS LIST

title        Windows XP
root         (hd0,2)
makeactive
chalnloader +1

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=eb31226b-8486-4929-a6fa-113cf503415a /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a48e917d-1ad2-41bb-acbc-3404db4d3c3b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


    .4GB: boot/grub/menu.lst
   1.5GB: boot/grub/stage2
   1.5GB: boot/initrd.img-2.6.28-11-generic
  13.5GB: boot/initrd.img-2.6.28-15-generic
   1.5GB: boot/vmlinuz-2.6.28-11-generic
  13.1GB: boot/vmlinuz-2.6.28-15-generic
  13.5GB: initrd.img
   1.5GB: initrd.img.old
  13.1GB: vmlinuz
   1.5GB: vmlinuz.old

================================ sda2/boot.ini: ================================

[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

---

### Post by Anarci on 2009-10-06
If you can try grabbing a copy of the supergrub livecd (or usb) - It a useful tool to have and I recommend it for anyone running linux - [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) 

It will pick up all installed os's and can write the changes to the mbr.

---

### Post by jimhoff on 2009-10-06
> **lindsay7 said:**
> You said "Right before the end line (### END DEBIAN AUTOMAGIC KERNELS LIST)"


The lines setting up Windows needs to be after "##End Debian....." in your grub menu.



Oh, yup. I just misspoke there in the first post. As seen from the results.txt I posted, it is after the END DEBIAN KERNELS bit. 

I appreciate all the help everyone has given me so far, but still can't get it to boot. I tried installing the supergrubdisk on a usb drive. I think I did everything right but there wasn't a boot option to boot from USB drive, so I guess I messed up somewhere. The instructions were pretty complicated for me.

---

### Post by lindsay7 on 2009-10-06
This is what I see, your windows partition is sda 2 which equates to hd0,1 so change your Grub menu to the following,

title        Windows XP
root         (hd0,1)
savedefault
makeactive
chalnloader +1

You do this by typing the following into the terminal

sudo gedit /grub/boot/menu.lst  (that is the lower case letter L)

Make the change and save the file, then reboot.

If this does not work, SuperGrub may help you fix things. Does your computer have a cd drive?  If so download the Supergrub program and save it to the cd and run the program from there.


You might also try this and see if it helps any,

sudo update-grub

---

### Post by arrange on 2009-10-06
2 mistakes, should be```
title        Windows XP
root         (hd0,1)
makeactive
chainloader +1

```

NOT ```
title        Windows XP
root         (hd0,2)
makeactive
chalnloader +1

``` (cha**l**nloader - spelling + root - partition number)

---

### Post by jimhoff on 2009-10-06
lindsay7,

if i open up grub/boot/menu.lst, it is empty. I have been editing boot/grub/menu.lst  and that contains the information. Did you have them switched around, or do I?

Thanks

---

### Post by oldfred on 2009-10-06
Your original entry was correct. Windows is on sda2 which in grub is (hd0,1) Your results.txt still has (hd0,2)

Your original entry:
title Windows XP 
root (hd0,1) 
makeactive 
chainloader +1 

lindsay7 beat me to it.

What was the original problem from your first post that had the correct entry.

---

### Post by lindsay7 on 2009-10-06
Yes, I made a mistake. You are correct.

Arrange, is correct too with the typos that he picked up on.

---

### Post by jimhoff on 2009-10-06
Oh hey, problem solved. Looks like I didn't proof read what I typed into the menu.lst. I chainloader was misspelt.  

Thanks for your expert proof reading skills. :)

---

### Post by QIII on 2009-10-06
Good catch on the spelling of chainloader.

But since GRUB is zero-based, I believe he should attempt (hd0,1) since he is looking for sda2.

---

### Post by lindsay7 on 2009-10-06
I am happy that _we all_ found the problem and you are back in business.  More then one set of eyes always helps.

---

