---
title: "grub restoration error"
date: 2009-01-04
forum: New to Ubuntu
---

### Post by koffeinöverdos on 2009-01-04
Hi, I recently installed vista for dual boot since i couldn't get what i wanted from virtual machine performance, and i have broken grub a few times before and fixed it, but now its different. I keep getting Error 15: File not found when i try to do find /boot/grub/stage1

I found tutorials that said if you get Error 15, try find /boot/grub/stage2 or find /grub/stage1, but these also return error 15. Can anyone help?

---

### Post by Miljet on 2009-01-04
I'm assuming that you are working from a Live CD? Have you tried mounting your Ubuntu partition and browsing it to make sure it wasn't overwritten by the Windows installation?

---

### Post by koffeinöverdos on 2009-01-09
Sorry about seemingly abandoning my thread, I had a personal emergency.

> **Miljet said:**
> I'm assuming that you are working from a Live CD? Have you tried mounting your Ubuntu partition and browsing it to make sure it wasn't overwritten by the Windows installation?

Sorry but I'm a linux noob. How would I mount that? Anyway I know Windows overwrote my MBR, its just this time I can't seem to fix it the way i did last time.

[edit] Okay I took a look at my drive with gparted, and it displays my ubuntu partition as unallocated. Is that what you were talking about Miljet?

---

### Post by Nerdriot on 2009-01-09
I had a similar problem, and resolved it here:

[http://ubuntuforums.org/showthread.php?t=754760]("http://ubuntuforums.org/showthread.php?t=754760")

Hope this helps some. :)

---

### Post by koffeinöverdos on 2009-01-09
> **Nerdriot said:**
> I had a similar problem, and resolved it here:

[http://ubuntuforums.org/showthread.php?t=754760]("http://ubuntuforums.org/showthread.php?t=754760")

Hope this helps some. :)

I followed the thread and did that. When I restarted my system, nothing. Just the blinking underscore. I have a feeling Vista kicked the crap out of my ubuntu partition... Unless someone can give me hope.

I dont understand.. I thought maybe Vista formatted my entire hard drive before installing on its 30 gb partition (like that even makes sense in the first place) but my linux-swap is still there.

All windows has ever done is screw up my computer, I never should have installed it so I could play that computer game and use Flash...

---

### Post by Nerdriot on 2009-01-09
Could you do me a favor and post your Grub here for me?

---

### Post by koffeinöverdos on 2009-01-09
> **Nerdriot said:**
> Could you do me a favor and post your Grub here for me?

Pardon my ignorance but what do you mean exactly? The specific command? I'm still a new linux user.

---

### Post by Nerdriot on 2009-01-09
No problem :)

Open terminal, and type in:

```
sudo gedit /boot/grub/menu.lst
```

When the text editor comes up, just paste what's in it here :)

---

### Post by koffeinöverdos on 2009-01-09
> **Nerdriot said:**
> No problem :)

Open terminal, and type in:

```
sudo gedit /boot/grub/menu.lst
```

When the text editor comes up, just paste what's in it here :)

Thank you for being patient with me.

The file had absolutely nothing in it. Not one character, I made sure it loaded. My partition was owned, wasn't it? I need a beer or three...

---

### Post by Nerdriot on 2009-01-09
Hmm, that's kind of odd... if you could, run this for me, and paste the output here:

```
ls -a /boot/grub/
```

If there's no menu.lst there, we'll try something else.

---

### Post by koffeinöverdos on 2009-01-09
> **Nerdriot said:**
> Hmm, that's kind of odd... if you could, run this for me, and paste the output here:

```
ls -a /boot/grub/
```

If there's no menu.lst there, we'll try something else.

```
ubuntu@ubuntu:~$ ls -a /boot/grub/
ls: cannot access /boot/grub/: No such file or directory
```

my linux-swap is still there, how is that perfectly fine yet ubuntu is totally gone?

---

### Post by Nerdriot on 2009-01-09
Well, that's certainly not good, lol...

Here, try this, to start, so we can at least generate a menu.lst:

```
sudo update-grub
```

That should check for installed kernels and such, and update your grub accordingly.

After that, run "ls -a /boot/grub/" again and see if anything was added (particularly, if menu.lst was).

I'm actually a little confused myself, really. My guess is, you'll only have to reinstall Grub, which you can do by booting up Ubuntu through a live cd/install cd.

---

### Post by koffeinöverdos on 2009-01-09
> **Nerdriot said:**
> Well, that's certainly not good, lol...

Here, try this, to start, so we can at least generate a menu.lst:

```
sudo update-grub
```

That should check for installed kernels and such, and update your grub accordingly.

After that, run "ls -a /boot/grub/" again and see if anything was added (particularly, if menu.lst was).

I'm actually a little confused myself, really. My guess is, you'll only have to reinstall Grub, which you can do by booting up Ubuntu through a live cd/install cd.

When i tried to run sudo update grub, it told me I had to create /boot/grub first, so I did, and then here's what happened.

```

ubuntu@ubuntu:~$ sudo mkdir /boot/grub
ubuntu@ubuntu:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... Generating /boot/grub/default file and setting the default boot entry to 0
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.lst file ... 

Could not find /boot/grub/menu.lst file. Would you like /boot/grub/menu.lst generated for you? (y/N) y
Searching for splash image ... none found, skipping ...
Found kernel: /boot/memtest86+.bin
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

```

Look like a good sign or was that pointless?

---

### Post by koffeinöverdos on 2009-01-09
sorry here's the bit for ls -a /boot/grub/

```

ubuntu@ubuntu:~$ ls -a /boot/grub/
.  ..  default  menu.lst

```

---

### Post by Nerdriot on 2009-01-09
Good sign. :) Now, if you'll run "sudo gedit /boot/grub/menu.lst" and paste the contents here, we'll see if Vista was added (though I doubt it was).

Then, we'll go ahead and try to get Grub installed as the loader, so you'll be able to switch between the two.

---

### Post by koffeinöverdos on 2009-01-09
> **Nerdriot said:**
> Good sign. :) Now, if you'll run "sudo gedit /boot/grub/menu.lst" and paste the contents here, we'll see if Vista was added (though I doubt it was).

Then, we'll go ahead and try to get Grub installed as the loader, so you'll be able to switch between the two.

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
# kopt=root=/home/ubuntu/aufs ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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

title		Ubuntu 8.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST
```
Thank you for staying with me this long, you're being extremely helpful.

---

### Post by Nerdriot on 2009-01-09
It's not a problem at all :)

That... hmm. Yeah, Vista isn't too friendly apparently. My advice would be to reboot the machine with the Ubuntu CD in it, and follow the directions here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6")

If that doesn't help at all (which it should), then come back, and we'll figure it out from there. :)

---

### Post by koffeinöverdos on 2009-01-09
> **Nerdriot said:**
> It's not a problem at all :)

That... hmm. Yeah, Vista isn't too friendly apparently. My advice would be to reboot the machine with the Ubuntu CD in it, and follow the directions here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6]("http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm?page=6")

If that doesn't help at all (which it should), then come back, and we'll figure it out from there. :)

I got stopped in my tracks pretty quickly, but it might be an easy fix.

```

grub> root (hd0,0)

grub> setup (hd0)

Error 17: Cannot mount selected partition
```

The thing is that if i try  find /boot/grub/stage1 is still says file not found.

---

### Post by caljohnsmith on 2009-01-09
It looks like those commands you ran to create a menu.lst won't help because you ran them from the Live CD without having your Ubuntu partition mounted. I think there might be other issues though, so how about doing the following:
```
cd ~/Desktop && wget 'http://internap.dl.sourceforge.net/sourceforge/bootinfoscript/boot_info_script.sh' && sudo bash boot_info_script.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by koffeinöverdos on 2009-01-09
```
============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot /boot /boot/grub

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sda3: _________________________________________________________________________

    File system:       Extended Partition

sda5: _________________________________________________________________________

    File system:       swap

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x49494948

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    61448191    30723072    7  HPFS/NTFS
/dev/sda2        61448625    61930574      240975    b  W95 FAT32
/dev/sda3   *    61930575   312576704   125323065    5  Extended
/dev/sda5       306568458   312576704     3004123+  82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: partition 1 does not end at a cylinder boundary

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xa4b57300

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001    7  HPFS/NTFS

sfdisk -V /dev/sdb:

Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
/dev/sdb: OK

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="9AC07FE8C07FC951" TYPE="ntfs" 
/dev/sda2: SEC_TYPE="msdos" UUID="490C-B3FA" TYPE="vfat" 
/dev/sda5: UUID="458962b2-2243-43fe-b51d-2269ad5e3ce9" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: UUID="C8663EAB663E99E0" LABEL="FreeAgent Drive" TYPE="ntfs" 

=============================== "mount" output: ===============================

/proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.27-7-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
/dev/scd0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sdb1 on /media/FreeAgent Drive type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)

================================== sda1/Boot: ==================================

total 504
drwxrwxrwx 1 root root   4096 2009-01-04 23:38 .
drwxrwxrwx 1 root root   8192 2009-01-09 22:12 ..
-rwxrwxrwx 1 root root  24576 2009-01-09 23:10 BCD
-rwxrwxrwx 1 root root  21504 2009-01-09 21:57 BCD.LOG
-rwxrwxrwx 2 root root      0 2009-01-04 23:38 BCD.LOG1
-rwxrwxrwx 2 root root      0 2009-01-04 23:38 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2009-01-04 23:38 bootstat.dat
drwxrwxrwx 1 root root      0 2009-01-04 23:38 cs-CZ
drwxrwxrwx 1 root root      0 2009-01-04 23:38 da-DK
drwxrwxrwx 1 root root      0 2009-01-04 23:38 de-DE
drwxrwxrwx 1 root root      0 2009-01-04 23:38 el-GR
drwxrwxrwx 1 root root      0 2009-01-04 23:38 en-US
drwxrwxrwx 1 root root      0 2009-01-04 23:38 es-ES
drwxrwxrwx 1 root root      0 2009-01-04 23:38 fi-FI
drwxrwxrwx 1 root root      0 2009-01-04 23:38 Fonts
drwxrwxrwx 1 root root      0 2009-01-04 23:38 fr-FR
drwxrwxrwx 1 root root      0 2009-01-04 23:38 hu-HU
drwxrwxrwx 1 root root      0 2009-01-04 23:38 it-IT
drwxrwxrwx 1 root root      0 2009-01-04 23:38 ja-JP
drwxrwxrwx 1 root root      0 2009-01-04 23:38 ko-KR
-rwxrwxrwx 1 root root 386664 2006-11-02 09:51 memtest.exe
drwxrwxrwx 1 root root      0 2009-01-04 23:38 nb-NO
drwxrwxrwx 1 root root      0 2009-01-04 23:38 nl-NL
drwxrwxrwx 1 root root      0 2009-01-04 23:38 pl-PL
drwxrwxrwx 1 root root      0 2009-01-04 23:38 pt-BR
drwxrwxrwx 1 root root      0 2009-01-04 23:38 pt-PT
drwxrwxrwx 1 root root      0 2009-01-04 23:38 ru-RU
drwxrwxrwx 1 root root      0 2009-01-04 23:38 sv-SE
drwxrwxrwx 1 root root      0 2009-01-04 23:38 tr-TR
drwxrwxrwx 1 root root      0 2009-01-04 23:38 zh-CN
drwxrwxrwx 1 root root      0 2009-01-04 23:38 zh-HK
drwxrwxrwx 1 root root      0 2009-01-04 23:38 zh-TW

================================== sda1/boot: ==================================

total 8
drwxrwxrwx 1 root root    0 2009-01-05 03:21 .
drwxrwxrwx 1 root root 8192 2009-01-09 22:12 ..
drwxrwxrwx 1 root root    0 2009-01-05 03:21 grub

=============================== sda1/boot/grub: ===============================

total 1
drwxrwxrwx 1 root root  0 2009-01-05 03:21 .
drwxrwxrwx 1 root root  0 2009-01-05 03:21 ..
-rwxrwxrwx 1 root root 45 2009-01-05 03:21 device.map

=============================== StdErr Messages: ===============================

No errors were reported.
```

See I believe it should be sda3, but it shows it as blank.

---

### Post by caljohnsmith on 2009-01-09
sda3 is your extended partition, meaning that it is just a container for the logical partitions; thus that wouldn't be your Ubuntu install. I hate to break the bad news, but unfortunately it looks like your Ubuntu install was overwritten; I think that sda2 might have been Ubuntu, but that's a FAT partition now. The bottom line is you don't have any linux partitions, so unfortunately I think you lost your Ubuntu install.

---

### Post by koffeinöverdos on 2009-01-09
> **caljohnsmith said:**
> sda3 is your extended partition, meaning that it is just a container for the logical partitions; thus that wouldn't be your Ubuntu install. I hate to break the bad news, but unfortunately it looks like your Ubuntu install was overwritten; I think that sda2 might have been Ubuntu, but that's a FAT partition now. The bottom line is you don't have any linux partitions, so unfortunately I think you lost your Ubuntu install. Thats pretty much the feeling I had from the beginning. Thanks anyway everyone...

---

### Post by Nerdriot on 2009-01-09
> **caljohnsmith said:**
> It looks like those commands you ran to create a menu.lst won't help because you ran them from the Live CD without having your Ubuntu partition mounted. I think there might be other issues though, so how about doing the following:
```
cd ~/Desktop && wget 'http://internap.dl.sourceforge.net/sourceforge/bootinfoscript/boot_info_script.sh' && sudo bash boot_info_script.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

Yeah, I didn't think about that. You're exactly right.

---

### Post by Nerdriot on 2009-01-09
> **caljohnsmith said:**
> sda3 is your extended partition, meaning that it is just a container for the logical partitions; thus that wouldn't be your Ubuntu install. I hate to break the bad news, but unfortunately it looks like your Ubuntu install was overwritten; I think that sda2 might have been Ubuntu, but that's a FAT partition now. The bottom line is you don't have any linux partitions, so unfortunately I think you lost your Ubuntu install.

And that was my fear... I was hoping for something else, but that's exactly how it seems...

Is there any chance that all of the data was left in-tact? Like the home folder and such? I'd hate for them to lose everything (been there).

---

### Post by koffeinöverdos on 2009-01-09
> **Nerdriot said:**
> And that was my fear... I was hoping for something else, but that's exactly how it seems...

Is there any chance that all of the data was left in-tact? Like the home folder and such? I'd hate for them to lose everything (been there).

Where am I supposed to look? There's no linux partition to mount.

I was braced for this, i wasn't even getting errors, just a bunch of "x Not Found" for everything i tried, there is suddenly no trace of my ubuntu install on my hard drive. What the heck happened?

Anyway thanks so much for donating your time to help me out. Greatly appreciated.

This really really sucks because not only did i have a lot of important things that I didnt back up, but I also spent forever pimping out gnome and stuff.

---

### Post by caljohnsmith on 2009-01-09
> **Nerdriot said:**
> And that was my fear... I was hoping for something else, but that's exactly how it seems...

Is there any chance that all of the data was left in-tact? Like the home folder and such? I'd hate for them to lose everything (been there).
If koffeinöverdos wants to, he could use a tool like "photorec" to recover whatever files he can from the sda2 partition. As you allude to, when you format a partition, the entire partition doesn't actually get overwritten. It's just that sorting through all the recovered files is a big chore, because they usually end up with generic names, and usually there's thousands of them. I can really feel for him too because I know what it is like.

---

### Post by Nerdriot on 2009-01-09
Sorry I'm not more help, by the way. I'm still a noob myself, heh...

---

### Post by koffeinöverdos on 2009-01-09
> **Nerdriot said:**
> Well, I'm thinking since there's not a mountable linux partition, it's probably all gone, sadly.

I wish I could help more. Sorry we weren't able to make it "work" again.Thank you very much for all of your help though, I learned some commands from it at least.

---

### Post by Nerdriot on 2009-01-09
Speaking of commands, does anyone remember the command to show all the mountable partitions/disks? I've been digging for it, but I can't find it. (That was really vague, sorry)

---

