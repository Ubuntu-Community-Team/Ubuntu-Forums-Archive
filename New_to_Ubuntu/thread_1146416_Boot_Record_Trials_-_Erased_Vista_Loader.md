---
title: "Boot Record Trials - Erased Vista Loader"
date: 2009-05-02
forum: New to Ubuntu
---

### Post by ashwat on 2009-05-02
Here is a short story. 

I had Two NTFS partitions. One with Vista( the one with the boot-loader ) and the other with Windows 7. I decided to install Jaunty. But the mistake I did was install it over the Vista NTFS by making it into ext4. The Win7 partition still exists, but doesn't show up in GRUB for obvious reasons. What I request here is a clear set of instructions so that I am able to add Win7 to Grub or something like that so that I can dual boot Jaunty and Win7.

More details: 

Tried using this [guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_Windows_entry_into_GRUB_menu"). These are some of the results. 
1) > cat /boot/grub/device.map
(hd0)	/dev/sda
(hd1)	/dev/sdb
 

2) > sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4863    39062016   83  Linux
/dev/sda2           13996       14593     4803435    5  Extended
/dev/sda3            4864       13995    73352790    7  HPFS/NTFS
/dev/sda5           13996       14593     4803403+  82  Linux swap / Solaris

Partition table entries are not in disk order





3)    >  e.g. Assumed that /dev/hda1 is the location of Windows partition 

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
gksudo gedit /boot/grub/menu.lst


Clearly from the above description my windows partition is sda3. 

So first I pasted > title		Microsoft Windows
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1
 as is, without any changes. When I restarted the GRUB menu did show the new entry but when chosen did nothing, ie, > ERROR 21: Selected disk not found. So this time, on a hunch, I changed  the parameter to (hd0,2), which ended up being correct in the sense that the error now was > BOOTMGR IS MISSING. Press CTRL+ALT+DEL to restart. So I just needed a confirmation as to whether I am headed in the right direction ( which I think I am ) and what needs to be done to get to see the light at the end of the tunnel. 

Also, I have the ISO of the Windows 7, which instead of burning, I extracted it onto my external USB drive and installed it from there( using Vista ) aka I do not have a bootable DVD. Is there any solution tenable without needing to write a bootable DVD or is it the only choice? Even somehow getting  to install Windows 7 from the dump, is a solution enough for me.

---

### Post by ashwat on 2009-05-02
More info added.

---

### Post by caljohnsmith on 2009-05-02
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by ashwat on 2009-05-02
> **caljohnsmith said:**
> I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

Thanks John. Here are the contents of the RESULTS.txt
```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xe8000000

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63    78,124,094    78,124,032  83 Linux
/dev/sda2         224,829,675   234,436,544     9,606,870   5 Extended
/dev/sda5         224,829,738   234,436,544     9,606,807  82 Linux swap / Solaris
/dev/sda3    *     78,124,095   224,829,674   146,705,580   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="a9ba77ed-a8d9-4308-a4e3-f7c33212a4b5" TYPE="ext4" 
/dev/sda3: UUID="C0F8C570F8C564EE" LABEL="Win7" TYPE="ntfs" 
/dev/sda5: UUID="8e7af825-a790-4218-9f11-d10cd664a487" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/rahul/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=rahul)


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
timeout		5

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
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=a9ba77ed-a8d9-4308-a4e3-f7c33212a4b5 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=a9ba77ed-a8d9-4308-a4e3-f7c33212a4b5

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
uuid		a9ba77ed-a8d9-4308-a4e3-f7c33212a4b5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a9ba77ed-a8d9-4308-a4e3-f7c33212a4b5 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		a9ba77ed-a8d9-4308-a4e3-f7c33212a4b5
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=a9ba77ed-a8d9-4308-a4e3-f7c33212a4b5 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		a9ba77ed-a8d9-4308-a4e3-f7c33212a4b5
kernel		/boot/memtest86+.bin
quiet

title		Microsoft Windows
rootnoverify	(hd0,2)
savedefault
makeactive
chainloader	+1


### END DEBIAN AUTOMAGIC KERNELS LIST

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
UUID=a9ba77ed-a8d9-4308-a4e3-f7c33212a4b5 /               ext4    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=8e7af825-a790-4218-9f11-d10cd664a487 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


   2.0GB: boot/grub/menu.lst
   1.8GB: boot/grub/stage2
   1.7GB: boot/initrd.img-2.6.28-11-generic
   1.8GB: boot/vmlinuz-2.6.28-11-generic
   1.7GB: initrd.img
   1.8GB: vmlinuz
```

---

### Post by caljohnsmith on 2009-05-02
It looks like what happened is when you installed Windows 7, it put its boot files in the Vista partition and then took over the booting process for both of them (which is totally normal). So when you deleted the Vista partition, you also unintentionally deleted Windows 7's boot files. To replace your Windows 7's boot files to its partition, I would suggest following [meierfra's tutorial for replacing Vista's boot files if they are missing]("http://ubuntuforums.org/showpost.php?p=5726832") (the tutorial applies to Win 7 too since it is the same as Vista about its booting process); just follow step 2 to restore your Windows 7 boot files (you can skip step 1 and 3), and also you don't need to run the "bootsect" command at the end of step 2 since your Windows 7 boot sector is fine. Let me know how that goes or if you run into problems.

John

---

### Post by ashwat on 2009-05-02
Thanks John. Just wrote down everything in that tutorial. Will try to update the results in about 15mins from now.

---

### Post by ashwat on 2009-05-02
I went ahead using the Dell Reinstallation disk and did as instructed in step 2 without any errors. But upon restart in GRUB, the error description was in relation to the winload32.exe as > The selected entry could not be loaded because the application is missing or corrupt

Edit : 

My bad. I hit winload32.exe instead of winload.exe in setting the path. I corrected the mistake, only to get the error message that the digital signature could not be verified.

---

### Post by caljohnsmith on 2009-05-02
> **ashwat said:**
> I went ahead using the Dell Reinstallation disk and did as instructed in step 2 without any errors. But upon restart in GRUB, the error description was in relation to the winload32.exe as 

Edit : 

My bad. I hit winload32.exe instead of winload.exe in setting the path. I corrected the mistake, only to get the error message that the digital signature could not be verified.
Did you make sure you ran all the bcdedit commands exactly as meierfra gave them in step 2 of the tutorial? Even the smallest typo can lead to problems like you are experiencing. Also, are you getting the error about the digital signature on start up, and is it for the winload32.exe program? 

John

---

### Post by meierfra. on 2009-05-02
I justed added a "automatic repair"  method to  Step 2 of my tutorial. Give that a try.

---

### Post by ashwat on 2009-05-02
The first error was due to a typo. That was corrected. The digital signature one came up, after the correction when I selected Windows from GRUB. It comes up immediately. From what I am seeing from other forums, they are asking me to press F8 at start up to "disable drive signature enforcement". But since the error comes up immediately after selecting Windows from GRUB, F8 options do not come up. 

Honestly speaking this post has become a Windoze post and if I were a moderator I would trash this post :P.

---

### Post by ashwat on 2009-05-02
> **meierfra. said:**
> I justed added a "automatic repair"  method to  Step 2 of my tutorial. Give that a try.

I tried the automatic one as well. Did not work. Tried it again, and the install was showing the current install as Windows 7 Recovered and when i tried to re-repair it, the Send Error Report contained Version Mismatch. So what I get from this is that I WILL need to burn a Windows 7 disc which is something I want to avoid but cannot. Is there another way out? Is it possible for me to recover/install Win7 from Jaunty using a Dump/Mount?

---

### Post by meierfra. on 2009-05-02
Are you still getting the "invalid digital signature" message immediately after selecting Windows 7 from the grub menu?


Just to make sure that the Win 7 boot loader is configured correctly:

Boot from the Windows DVD and go to the command line. Then 

```
bcdedit /store C:\boot\bcd > C:\bcd.txt
```
(where "C" needs to be replaced by the drive letter of your Windows 7 partition)

You can access "bcd.txt" from Ubuntu via 

```
sudo mount /dev/sda3 /mnt
cat /mnt/bcd.txt
```

Could you post the output of the last command?

---

### Post by ashwat on 2009-05-02
Yes I am still getting the digital signature error

Here is the output of bcd.txt
```
Windows Boot Manager
--------------------
identifier              {bootmgr}
device                  partition=C:
default                 {default}
displayorder            {default}
timeout                 30

Windows Boot Loader
-------------------
identifier              {default}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Windows 7 Ultimate (recovered) 
osdevice                partition=C:
systemroot              \Windows

```

---

### Post by meierfra. on 2009-05-02
According to bcd.txt the Win 7 bootloader seems to be configured correctly.

I just worked through my tutorial  using  a  Dell Vista Reinstallation DVD to replace  the boot loader of my Window 7 installation.   Win 7 booted just fine. So I don't think your  problem is caused by using the wrong kind of DVD.

Is this the error messages you are getting:


> 'A recent hardware or software change might have installed a file that is signed incorrectly or damaged, or that might be malicious software from an unknown source. If you have a Windows installation disc insert the disk and restart your computer. Click "repair your computer" and then choose a recovery tool. Otherwise, to start Windows so you can investigate further, press the ENTER key and display the boot menu, press F8 for Advanced Boot Options and select last Known Good. If you understand why the digital signature cannot be verified and want to start Windows without this file, temporarily disable driver signature enforcement.

File: \windows\system32\winload exe

Status: Oxc0000428

Info: Windows cannot verify the digital signature for this file'


Does you error message  also complain about "winload.exe" or  is it a different file?

---

### Post by ashwat on 2009-05-02
Exactly the same error.

---

### Post by meierfra. on 2009-05-02
> Exactly the same error.

Sorry,  this is the first time I'm encountering that error message and I have no clue what else  to do.  I'll do some more googling and I'll let you know if I come up with a new idea, 

Let us know if you find a solution.

---

### Post by meierfra. on 2009-05-03
Well, I found a couple of case which  are very similar to yours:

[http://dandar3.blogspot.com/2009/03/windows-vista-bootloader-repair.html](http://dandar3.blogspot.com/2009/03/windows-vista-bootloader-repair.html)

[http://neosmart.net/forums/showthread.php?p=35496](http://neosmart.net/forums/showthread.php?p=35496)

Unfortunately, the first case never was solved. But the link seems to indicate that this problem only occurs in  the very recent versions of Window 7. Which might explain why I didn't run into any problems: I have a very early version of Windows 7 beta. What version are you using?

The  second  case was solved using the Windows 7 DVD. 
So I'm withdrawing my earlier statements that your problem has nothing to do with the DVD you are using.  It seems there is a problem with  "winload.exe".  I know that the winload.exe used by Vista is different from the winload.exe used by Win 7. So it makes sense that your Vista DVD is not able to fix the Win 7 winload.exe

In other words, I now agree with your earlier assessment:  You need  to burn a Windows 7 DVD.

---

### Post by ashwat on 2009-05-04
Win7 RC. Burnt and it worked.

---

### Post by meierfra. on 2009-05-04
> Win7 RC. Burnt and it worked.
Great. Enjoy Win7 and Ubuntu.

---

