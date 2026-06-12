---
title: "Help Configuring GRUB"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Tsurugi13 on 2009-04-28
I need some help with GRUB. For a while I was tinkering with the Windows 7 beta on a dual-boot with XP, but realized I wasn't really using it and removed it with GParted. Since then, the windows bootloader pops up and tries to boot into 7, even though it isn't there. This bootloader was configured by 7, so XP can't seem to do anything about it, short of using the recovery console, which I've already lost a hard drive to.

Getting to the point, when I installed Jaunty the other day, GRUB picked up on the windows bootloader, so now I have an entry called Windows Vista (boot), that pops up NTLDR, exactly like I don't want it to. Is there a way to configure GRUB's menu.lst file or something so that it boots straight to XP, and not just another bootloader?

---

### Post by drs305 on 2009-04-28
If things are being controlled by grub, it's a simple matter of editing /boot/grub/menu.lst

You can install StartUp-Manager to do the editing for you via a gui app.
Install:
```

sudo apt-get install startupmanager

```

To Start:
System, Administration, StartUp-Manager
or
```
gksudo startupmanager
```

Under the first tab, Boot Options, you can select the default OS.

StartUp-Manager has lots of other tweaks. You can read about them via the link in my signature line.

If you would prefer to manually edit menu.lst and get rid of the windows entries permanently, please post the contents in this thread.
```

cat /boot/grub/menu.lst

```

---

### Post by Tsurugi13 on 2009-04-28
The GUI is nice, but my problem is that I need to boot straight to XP, without touching the windows bootloader in the process.

---

### Post by Jimmynemo2 on 2009-04-28
I use KgrubEditor.

even though its KDE, it works fine in gnome, and gives a nice GUI program for editing the grub boot options. 

Worked like a charm for me, with similar problems.

You'll find it in the default repositories, even if you just type in grub.

Hope this helps.

---

### Post by Tsurugi13 on 2009-04-28
After a bit of prowling around with Kgrubeditor and gparted, I've found out a couple things. First is that I should have mentioned I'm using two different drives. The first, sda, contains nothing but Jaunty. The second, sdb, contains nothing but XP and this stupid bootloader. The entry for the windows bootloader is (hd1,0), so what I really need to do is get around that bootloader some way or another.

---

### Post by pastalavista on 2009-04-28
Try downloading, burning and booting with a [SuperGrub]("http://www.supergrubdisk.org") disk. It is very good at what it does. I've used it a couple of times and it is amazing at fixing things like this.

---

### Post by louieb on 2009-04-28
> **Tsurugi13 said:**
> Is there a way to configure GRUB's menu.lst file or something so that it boots straight to XP, and not just another bootloader?

The short answer is no. GRUB boots windows by chainloading to its boot loader. Afraid you have to fix XP's boot loader. This might help. [How to fix XP when the boot files are missing - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=813628")  or  [UF - How to fix XP when the boot files are missing]("http://ubuntuforums.org/showpost.php?p=5082723")

---

### Post by Tsurugi13 on 2009-04-30
> **louieb said:**
> The short answer is no. GRUB boots windows by chainloading to its boot loader. Afraid you have to fix XP's boot loader. This might help. [How to fix XP when the boot files are missing - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=813628")  or  [UF - How to fix XP when the boot files are missing]("http://ubuntuforums.org/showpost.php?p=5082723")

I tried this, and it didn't help. I think my real problem is a residual bootloader from my 7 install that no longer exists. Not really sure if that makes sense, as I formatted the 7 partition to death. :confused: Might reinstalling XP fix this? I'm about out of ideas.

---

### Post by NightwishFan on 2009-04-30
I think you can use "msconfig" to edit the windows boot loader.

In Xp go to the "run.." dialog and type: msconfig

---

### Post by caljohnsmith on 2009-04-30
I think it would help to first get a clearer picture of your setup related to your booting problem, so how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

John

---

### Post by Tsurugi13 on 2009-05-01
All right, here it is:

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ext3
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

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD /ntldr /NTLDR 
                       /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41ab2316

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   149,790,059   149,789,997  83 Linux
/dev/sda2         149,790,060   156,248,189     6,458,130   5 Extended
/dev/sda5         149,790,123   156,248,189     6,458,067  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x98699869

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   976,768,064   976,768,002   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="12bd1d29-f9bd-434f-94b6-e0aea3bcc50f" TYPE="ext3" 
/dev/sda5: UUID="c9e810e1-410c-4f6f-86d7-55f38766c70f" TYPE="swap" 
/dev/sdb1: UUID="B89C71669C712054" TYPE="ntfs" 

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
lrm on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/brennan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=brennan)


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
# kopt=root=UUID=12bd1d29-f9bd-434f-94b6-e0aea3bcc50f ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=12bd1d29-f9bd-434f-94b6-e0aea3bcc50f

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
uuid		12bd1d29-f9bd-434f-94b6-e0aea3bcc50f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=12bd1d29-f9bd-434f-94b6-e0aea3bcc50f ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		12bd1d29-f9bd-434f-94b6-e0aea3bcc50f
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=12bd1d29-f9bd-434f-94b6-e0aea3bcc50f ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		12bd1d29-f9bd-434f-94b6-e0aea3bcc50f
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Windows Vista (loader)
rootnoverify	(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1


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
UUID=12bd1d29-f9bd-434f-94b6-e0aea3bcc50f /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=c9e810e1-410c-4f6f-86d7-55f38766c70f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


  53.6GB: boot/grub/menu.lst
  53.2GB: boot/grub/stage2
  53.2GB: boot/initrd.img-2.6.28-11-generic
  53.2GB: boot/vmlinuz-2.6.28-11-generic
  53.2GB: initrd.img
  53.2GB: vmlinuz

================================ sdb1/boot.ini: ================================

[Boot Loader]

timeout=30

Default=multi(0)disk(0)rdisk(0)partition(1)\Windows

[Operating Systems]

multi(0)disk(0)rdisk(0)partition(1)\Windows="Windows XP" /fastdetect



```

Thanks for the help.

---

### Post by caljohnsmith on 2009-05-01
So is your sdb1 partition supposed to be Windows XP? Right now that partition still has a Vista/Win7 boot sector, and it also has all of Vista's/Win7's boot files. So I'm not sure at this point if you really have Windows XP successfully installed to that partition, but it might be that you do and all you need to do is fix the boot sector. To fix the boot sector, you could boot a Windows XP install CD, go to the recovery console, and run:
```
fixboot
```
And that should fix the sdb1 boot sector so that it is a Windows XP boot sector. Then try booting sdb1 using your existing Windows Vista entry in your Grub menu, and let me know exactly what happens. We can work from there if you want.

Cheers,
John

---

### Post by Tsurugi13 on 2009-05-03
> **caljohnsmith said:**
> So is your sdb1 partition supposed to be Windows XP? Right now that partition still has a Vista/Win7 boot sector, and it also has all of Vista's/Win7's boot files. So I'm not sure at this point if you really have Windows XP successfully installed to that partition, but it might be that you do and all you need to do is fix the boot sector. To fix the boot sector, you could boot a Windows XP install CD, go to the recovery console, and run:
```
fixboot
```
And that should fix the sdb1 boot sector so that it is a Windows XP boot sector. Then try booting sdb1 using your existing Windows Vista entry in your Grub menu, and let me know exactly what happens. We can work from there if you want.

Cheers,
John

Well, I ran through this, and the same thing happened. The recovery console claimed to be fixing a corrupted bootloader, but nothing changed.

---

### Post by caljohnsmith on 2009-05-03
So "fixboot" didn't return any errors? Please post the output of the following command:
```
sudo xxd -s128 -l2 -p /dev/sdb1
```

John

---

### Post by louieb on 2009-05-03
Believe you need to give fixboot a drive letter. Defaut is the current drive.  try
```
fixboot c:
```

---

### Post by Tsurugi13 on 2009-05-04
> **louieb said:**
> Believe you need to give fixboot a drive letter. Defaut is the current drive.  try
```
fixboot c:
```

Hurm. I didn't give it a drive letter, and I think it broke something. Ubuntu won't boot, it just drops into a shell. Starting to remind me of this: [http://xkcd.com/349/]("http://xkcd.com/349/")

---

### Post by xhaan on 2009-05-04
Not sure exactly what's going on, it's a little hard to follow...

But I gather that your Ubuntu drive has boot priotiy in your BIOS (GRUB boots first, if there isn't a CD in)

And then, on your Windows drive, your Windows loader is hosed, which you tried to repair, and it now broke GRUB.


I'm not sure exactly what to say (that hasn't already been said) but I'll warn that Windows installers and tools tend to be 'greedy' (I forgot this myself and wiped a whole partition just the other day while doing an XP install)

Basically I mean you have a danger of the installer/tool in question taking the first disk it comes across without even asking you. And it sounds to me like in this case, it happened to be your Ubuntu drive.

So, I recommend **physically disconnecting** any other drives except the one you want to work on, to avoid any further damage. This also helps you figure out problems in your bootloader without the confusion of chain loading. So disconnect your Ubuntu drive so you know FOR SURE that your Windows drive is the one getting priority, and any changes made will happen to that drive only. After that is fixed, it's a bit simpler to reconnect Ubuntu and fix GRUB last.

---

### Post by Tsurugi13 on 2009-05-05
Yaaaaaay! Disconnecting my ubuntu drive and using fixboot c: in the recovery console worked like a charm, although I did need to reinstall ubuntu to get it back to normal, just restoring GRUB didn't work. Not too much of a loss, about the only thing I'd done was install yakuake. Thanks for all the help!

---

### Post by Insanity01 on 2009-05-05
you can do any of the things mentioned above, but what i like is easyBCD under windows, allows you to configure w.e bootloader you are using, removing os's to boot, adding etc...

---

