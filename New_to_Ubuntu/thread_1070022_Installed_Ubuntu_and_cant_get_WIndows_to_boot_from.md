---
title: "Installed Ubuntu and cant get WIndows to boot from Grub boot loader menu"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by mystikal2k2a on 2009-02-14
Hi

Ok I'm stuck, please can anyone help me with this?

I have 2 sata hard drives - 1 with MS Windows XP Pro and the other with Linux Ubuntu. I have the grub boot loader menu appearing and I can see an entry for Windows. When I try and select the Windows option from the boot loader menu I get an error. I've received different errors each time I have tried configuring the boot/grub/menu.lst file. I can't get into Windows at present but can get into Ubuntu.

This is the contents of fdisk -l -

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x896a4361

Device Boot Start End Blocks Id System
/dev/sda1 * 1 498 4000153+ 82 Linux swap / Solaris
/dev/sda2 499 6334 46877670 5 Extended
/dev/sda5 499 6334 46877638+ 83 Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x457d457c

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 3916 31455238+ 7 HPFS/NTFS
/dev/sdb2 3917 19457 124833082+ 7 HPFS/NTFS

This is the contents of my menu.lst file in boot/grub -

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

I have tried various combinations to get this corrected. I even tried replacing the letters hd1 and hd0 to sd1 and sd0 where applicable because I read it maybe required for SATA discs?

Can anyone help please?

Thanks

---

### Post by kestrel1 on 2009-02-14
That should work, but normally Windows prefers to be on the first HD.
Mine works OK with```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```
I wonder if taking the map parts out would do it.
I know mine is on hd0, but I would imagine that hd1 would have worked.

---

### Post by mystikal2k2a on 2009-02-14
Hmm I might need to switch the boot device in the BIOS to the Ubuntu Sata disk.

Then change the root in the menu.lst entry to hd0,0 and see where that gets me. 

I will switch the sata cables round again to make Windows the first SATA disk running on SATA channel 1.

If anyone has any other ideas please suggest.

Thank you

---

### Post by kestrel1 on 2009-02-14
If Windows was installed on the second drive I doubt it will work by switching the cables.
Have you tried removing from your menu.lst file:> map (hd0) (hd1)
map (hd1) (hd0)

---

### Post by caljohnsmith on 2009-02-14
In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

---

### Post by mystikal2k2a on 2009-02-14
> **caljohnsmith said:**
> In order to get a clearer picture of your setup, how about downloading the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your Windows booting problem might be.

Hi

The results of the Boot Info Script are attached.

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x896a4361

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63     8,000,369     8,000,307  82 Linux swap / Solaris
/dev/sda2           8,000,370   101,755,709    93,755,340   5 Extended
/dev/sda5           8,000,433   101,755,709    93,755,277  83 Linux


Drive sdb: _____________________________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x457d457c

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    62,910,539    62,910,477   7 HPFS/NTFS
/dev/sdb2          62,910,540   312,576,704   249,666,165   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="245a7002-e951-496f-abb3-6dd16708da08" TYPE="swap" 
/dev/sda5: UUID="3361e22f-4975-4671-b356-2266937660b2" TYPE="ext3" 
/dev/sdb1: UUID="70801F19801EE57E" TYPE="ntfs" 
/dev/sdb2: UUID="1A8469008468E02D" LABEL="Local Disk" TYPE="ntfs" 

=============================== "mount" output: ===============================

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
gvfs-fuse-daemon on /home/nadim/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=nadim)

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
# kopt=root=UUID=3361e22f-4975-4671-b356-2266937660b2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3361e22f-4975-4671-b356-2266937660b2

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
uuid		3361e22f-4975-4671-b356-2266937660b2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3361e22f-4975-4671-b356-2266937660b2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		3361e22f-4975-4671-b356-2266937660b2
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=3361e22f-4975-4671-b356-2266937660b2 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		3361e22f-4975-4671-b356-2266937660b2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3361e22f-4975-4671-b356-2266937660b2 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		3361e22f-4975-4671-b356-2266937660b2
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=3361e22f-4975-4671-b356-2266937660b2 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		3361e22f-4975-4671-b356-2266937660b2
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


=============================== sda5/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb5
UUID=3361e22f-4975-4671-b356-2266937660b2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
UUID=245a7002-e951-496f-abb3-6dd16708da08 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


  16.5GB: boot/grub/menu.lst
  16.6GB: boot/grub/stage2
  16.5GB: boot/initrd.img-2.6.27-11-generic
  16.7GB: boot/initrd.img-2.6.27-7-generic
  16.6GB: boot/vmlinuz-2.6.27-11-generic
  16.6GB: boot/vmlinuz-2.6.27-7-generic
  16.5GB: initrd.img
  16.7GB: initrd.img.old
  16.6GB: vmlinuz
  16.6GB: vmlinuz.old

================================ sdb1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

```

I installed Ubuntu on the second Sata drive whilst my Windows HD was still plugged in on the mobo. When I rebooted I got the error - Grub Loading STAGE 1.5 Grub Loading, please wait Error 21

I couldn't get back into Ubuntu because of this so I switched my sata cables on the Sata drives to be able to edit the menu.lst file and thats where I'm up to now. I've tried many different combinations to edit the menu.lst file but no luck. 

Thank you for your help!

---

### Post by caljohnsmith on 2009-02-14
So without changing your HDDs' configuration, did you try the entry that kestrel1 gave in post #2? You may not realize it, but you could be booting the sdb drive on start up, and if that is true, kestrel1's Windows entry should work. If it doesn't, please be more specific in describing the exact error you get, or what exactly happens. Also it would help a lot if you could be specific about the error you got with your original Windows Grub entry from post #1.

---

### Post by mystikal2k2a on 2009-02-14
Hi

I've just tried what Kestrel1 suggested with the 2 mapping lines in the piece of code removed, this what the entry in menu.lst file looks like at the moment (still with present HD configuration as in my last post in the boot script code - 

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
chainloader +1

When I restarted the computer and selected Windows in the Grub menu I received this error - 

Error 21: Selected disk does not exist
Enter any key

This returns me back to the Grub menu and I am able to select Ubuntu from the list.

Sorry because I've tried so many combinations of trying to edit the menu.lst file I can't remember which specific error appeared with the entry from post 1 on this thread. I can re-edit the menu.lst file so it looks like the post 1 entry again? I can tell you the exact error that is produced as a result, shall I do this?

Thanks

---

### Post by caljohnsmith on 2009-02-14
How about doing this instead: on start up when you get the Grub menu, press "c" to get the Grub command line, and then do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
From what you have described so far, probably the first command will show two partitions of type "83" and "82", but let me know if instead the partitions are both type "7". Also, you will probably get an error with the second command, but please let me know exactly what the result is.

---

### Post by mcloser on 2009-02-14
where do these people go?

CalJohn, please accept my thanks on behalf of 'others'

I see how much you help all us noobs and I for one can say that it makes the conversion to U much easier.  it is getting very mature now and works very well but new users need a bit of spoon feeding to find out how to do some of those tricky things to make it perfect.

its too bad because i wanted to know what was causing buddy's problem, it sounds like something that might happen to me some day !

anyway - thx.    :)

---

### Post by mystikal2k2a on 2009-02-15
> **caljohnsmith said:**
> How about doing this instead: on start up when you get the Grub menu, press "c" to get the Grub command line, and then do:
```
grub> geometry (hd0)
grub> geometry (hd1)
```
From what you have described so far, probably the first command will show two partitions of type "83" and "82", but let me know if instead the partitions are both type "7". Also, you will probably get an error with the second command, but please let me know exactly what the result is.

Ok, I've followed your instructions and these are the results:

grub> geometry (hd0) output was - 

drive 0x80: C/H/S = 1023/255/63, The number of sectors = 625142448, LBA
 Partition num: 0, Filesystem type unknown, partition type 0x82
 Partition num: 4, Filesystem type is ext2fs, partition type 0x83

grub> geometry (hd1) output was - 

Error 21: Selected disk does not exist

Really thank you very much for all your help so far caljohnsmith.

---

### Post by caljohnsmith on 2009-02-15
The results you got from the geometry commands are unfortunately what I expected; currently you are booting the sda Ubuntu drive on start up which is good, but your sdb Windows drive is not even detected by Grub. And since Grub uses your BIOS to access your drives, that means most likely that your BIOS does not recognize the sdb drive on start up. How about when you are in Ubuntu do the following:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
That will restore a Windows MBR to your sdb Windows drive; after that, how about rebooting, but set your BIOS to boot the sdb Windows drive instead of the sda drive if you can. Let me know if that allows you to boot Windows or not. I'm thinking probably you will will have to change your BIOS settings so that your Windows drive is properly recognized on start up, but let me know how it goes or what problems you run into. We can work from there.
> **mcloser said:**
> 
CalJohn, please accept my thanks on behalf of 'others'

I see how much you help all us noobs and I for one can say that it makes the conversion to U much easier.  it is getting very mature now and works very well but new users need a bit of spoon feeding to find out how to do some of those tricky things to make it perfect.

its too bad because i wanted to know what was causing buddy's problem, it sounds like something that might happen to me some day !

anyway - thx.    :)
You're certainly welcome, mcloser; thanks for your encouragement, because I'm sometimes a little surprised at how few people even remember to say a simple "thanks" when someone voluntarily gives their free time to help them. I must admit that it sure is a lot more motivating to help someone when they are considerate enough to just say a simple "thanks" of some sort. :)

---

### Post by mcloser on 2009-02-15
yes caljohn, I hope to be able to help folks with stuff at some point myself, the only problem i face is now being at the age where i just want stuff to work and am not so inclined into ripping stuff apart.

I was wondering a few posts ago whether SuperGrub might do something helpful.

also hooking up the drives in the order so it hits the Windoze drive first.

I am almost thinking that the best arrangement is to have both OS on the same drive with the second just as a user file shared as NTFS.  I have good luck with this arrangement myself, where other configurations have failed.

I have hesitated to say anything because I'm not sure if this will help or not, please advise.

( also is the real command :   RM - R *     ?  )

---

### Post by mystikal2k2a on 2009-02-15
> **caljohnsmith said:**
> The results you got from the geometry commands are unfortunately what I expected; currently you are booting the sda Ubuntu drive on start up which is good, but your sdb Windows drive is not even detected by Grub. And since Grub uses your BIOS to access your drives, that means most likely that your BIOS does not recognize the sdb drive on start up. How about when you are in Ubuntu do the following:
```
sudo apt-get install lilo
sudo lilo -M /dev/sdb mbr
```
That will restore a Windows MBR to your sdb Windows drive; after that, how about rebooting, but set your BIOS to boot the sdb Windows drive instead of the sda drive if you can. Let me know if that allows you to boot Windows or not. I'm thinking probably you will will have to change your BIOS settings so that your Windows drive is properly recognized on start up, but let me know how it goes or what problems you run into. We can work from there.

Hi caljohnsmith

You were right that BIOS was detecting the sdb drive. I have to do some configuration in the BIOS so the drive would appear. Both drives now appear on booting up just before the Grub loader starts up which wasn't happening before. After the changes I made in the BIOS so it detected the sdb drive I tried selected Windows from the grub menu and I didn't receive the "error 21: selected disk does not exist". I received the message "starting up..." instead but it just hangs there. So I'm guessing the sdb drive is now being picked up.

I haven't yet done what you suggested in your last post just in case the problem can be rectified with the changes I made in the BIOS to detect the sdb drive. I can go ahead and do what you suggested in your last post if you wish? I thought I better check as making change after change of my own accord will slow down the progress of trying to fix this logically and primarily I don't want to waste your time.

Please let me know if I should do what you suggested in your last post (load the lilo program on mbr of sdb Windows drive and make the sdb drive bootable in BIOS).

Thank you very much once again... getting closer :)

---

### Post by caljohnsmith on 2009-02-15
Yes, please go ahead and run the lilo commands from my previous post. Also, you'll need the mapping lines for your Windows entry, so how about using the following entry:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, and let me know exactly what happens when you try XP from your Grub menu. We can work from there.

---

### Post by mystikal2k2a on 2009-02-15
> **caljohnsmith said:**
> Yes, please go ahead and run the lilo commands from my previous post. Also, you'll need the mapping lines for your Windows entry, so how about using the following entry:
```
title       Windows XP
rootnoverify     (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, and let me know exactly what happens when you try XP from your Grub menu. We can work from there.

caljohnsmith I'd like to say a very big thank you, it's all working now :)

I followed your instructions from post#12 and the last post. Then I rebooted the computer at which point I made the Windows sdb drive the first boot device. The result of this was me entering Windows as normal (no grub menu).

Next I rebooted the computer and went into the BIOS to switch the first boot device to sda. The result of this was the grub menu appearing I selected Windows from the grub menu and I went straight into Windows. I rebooted the computer to see if I could still select Ubuntu from the grub loader and yes I can :)

So thank you very much, I owe you a drink if your ever in the UK, Manchester area!

One last question please if I ever come to formatting my Windows partition on the sdb drive, will I need to mess around with any of this again?

Also I know partly why it wasn't working now after installing Ubuntu which was the BIOS wasn't picking up the sdb drive but it seems like by reloading the lilo boot loader on the sdb drive fixed the overall problem?

Cheers :)

---

### Post by caljohnsmith on 2009-02-15
> **mystikal2k2a said:**
> 
One last question please if I ever come to formatting my Windows partition on the sdb drive, will I need to mess around with any of this again?

If you format the Windows partition, you should be fine regarding booting Ubuntu. If you actually reinstall Windows, you will have to reinstall Grub afterwards since Windows always overwrites the MBR with its own boot loader.
> **mystikal2k2a said:**
> 
Also I know partly why it wasn't working now after installing Ubuntu which was the BIOS wasn't picking up the sdb drive but it seems like by reloading the lilo boot loader on the sdb drive fixed the overall problem?

Cheers :)
I think what fixed the problem was making sure you were booting the sdb drive, and also making sure your Windows Grub entry was correct. Reinstalling a Windows MBR to the Windows drive helped remove the ambiguity of which drive you were booting on start up, because you had Grub installed to the MBR of both drives originally. Anyway, cheers and enjoy Ubuntu and Windows. :)

---

### Post by mystikal2k2a on 2009-02-17
> **caljohnsmith said:**
> If you format the Windows partition, you should be fine regarding booting Ubuntu. If you actually reinstall Windows, you will have to reinstall Grub afterwards since Windows always overwrites the MBR with its own boot loader.

I think what fixed the problem was making sure you were booting the sdb drive, and also making sure your Windows Grub entry was correct. Reinstalling a Windows MBR to the Windows drive helped remove the ambiguity of which drive you were booting on start up, because you had Grub installed to the MBR of both drives originally. Anyway, cheers and enjoy Ubuntu and Windows. :)

Thanks for all your help once again Caljohnsmith!

---

