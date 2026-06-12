---
title: "missing vista from boot menu"
date: 2009-09-10
forum: New to Ubuntu
---

### Post by geek_overlord on 2009-09-10
After installing vista I was unable to boot into Ubuntu. I tried wubi but there's some sort of compatibility problem with Vista 64 so I used Super Grub. It did the job but now I don't have access to vista. I can see the drive in the places menu but I need to boot into it. Can someone tell me how to fix this please? Thank you.

---

### Post by PukingPenguin on 2009-09-10
Please open a terminal and give us the output of ```
sudo fdisk -l
```

---

### Post by geek_overlord on 2009-09-10
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0000112b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38158   306504103+  83  Linux
/dev/sda2           38159       38913     6064537+   5  Extended
/dev/sda5           38159       38913     6064506   82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       25841   195357928+   7  HPFS/NTFS

I hope this helps.

---

### Post by oldfred on 2009-09-10
We normally like to see your menu.lst so we can see why Vista does not work. If you just do not have the Vista boot stanza add this to the end of your menu.lst

First copy menu.lst just in case we edit it wrong. Then edit menu.lst:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup

gksudo gedit /boot/grub/menu.lst

```Add this stanza at the end (or edit what you have to be like this), I am also not sure if Vista requires the map commands since it is the only Windows on your machine usually windows wants to be on the first drive:

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title        Microsoft Windows Vista
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by geek_overlord on 2009-09-10
Ok sorry I don't quite understand everything you just gave me there. So is this one command or two? And thanks again for your help with this. I

---

### Post by bumanie on 2009-09-10
Do this command first> sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backupIt backs up your /boot/grub/menu.lst in case something goes wrong you can copy this back to the original list. Do this next>  gksudo gedit /boot/grub/menu.lstIt opens up the /boot/grub/menu.lst for editing.
Lastly add this to the bottom of the /boot/grub/menu.lst 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows Vista
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

Save the edited version and reboot and hopefully everything will work. Windows prefers to be on the first partition of the first hard drive, that is why the map commands are added to 'trick' windows into thinking it is on the first hard drive.

---

### Post by geek_overlord on 2009-09-10
I did as requested and got the error message "Invalid or unsupported executable". Just a little background, after I ran super grub I noticed Windows xp in the list of operating systems I could boot into. It must have picked that up from the xp disk I had in my drive at the time. I didn't actually have XP installed. I intended to install it since wubi didn't work with vista 64 but I was unsuccessful. So now it looks like I'm in a big mess. Does anyone have any suggestions? Thanks

---

### Post by oldfred on 2009-09-11
With two drives and just a few partitions it seemed like the Vista stanza entry should work. If it is more complicated we need you to download a program that will completely list your configuration. 

Download this program to a directory and run it. It will create a file called results.txt. Copy that file and post it here.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by geek_overlord on 2009-09-11
How do I run this? Sorry I'm still trying to figure out how to run programs in Linux.

---

### Post by oldfred on 2009-09-11
I find the easiest way to use Nautilus (the file manager) and right click, properties, tab for permissions and check the executable box. Then you can doubleclick and run.

Otherwise I alway have to lookup the terminal command that everyone else uses.

Adding commands that I looked up

sudo chmod 755 boot_info_script032.sh

 sudo ./boot_info_script032.sh

---

### Post by geek_overlord on 2009-09-11
I was able to check the executable box in Nautilus however when I double click the file I get nothing. I see a slight flicker on the icon and then nothing. I right clicked on the file for other options and I get more of the same when I select run. I tried run in terminal and terminal flickers on the status bar for a minute then goes away. The only thing I can do is display. Will that give you the information you need?

---

### Post by oldfred on 2009-09-11
It may have run. Is results.txt in the directory the script is in?  If not open a terminal (not run in terminal) and execute the script with the command given before. Then you should see it run the script or give an error message.

---

### Post by geek_overlord on 2009-09-11
I did as you said up to the point where the file was to be created. When I selected run or run in terminal I was unable to find the file or get the program to populate in terminal. It seems like I'm defeated at ever turn. Do you have any other ideas?

---

### Post by geek_overlord on 2009-09-11
duh sorry missed your last post. working on it.

---

### Post by geek_overlord on 2009-09-11
Ok here is the rather massive output of the file.

============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in 
    partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 8.10
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
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0000112b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   613,008,269   613,008,207  83 Linux
/dev/sda2         613,008,270   625,137,344    12,129,075   5 Extended
/dev/sda5         613,008,333   625,137,344    12,129,012  82 Linux swap / Solaris


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
240 heads, 63 sectors/track, 25841 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000001

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63   390,715,919   390,715,857   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="c712888e-5f65-485e-90b6-dfe1b0dcac0b" TYPE="ext3" 
/dev/sda5: UUID="6d7e2f94-94b4-4ef8-96c1-2be1e66269ae" TYPE="swap" 
/dev/sdb1: UUID="644836E44836B520" TYPE="ntfs" 

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
lrm on /lib/modules/2.6.27-14-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/dylan/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=dylan)


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
# kopt=root=UUID=c712888e-5f65-485e-90b6-dfe1b0dcac0b ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=c712888e-5f65-485e-90b6-dfe1b0dcac0b

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

title		Ubuntu 8.10, kernel 2.6.27-14-generic
uuid		c712888e-5f65-485e-90b6-dfe1b0dcac0b
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c712888e-5f65-485e-90b6-dfe1b0dcac0b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-14-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-14-generic (recovery mode)
uuid		c712888e-5f65-485e-90b6-dfe1b0dcac0b
kernel		/boot/vmlinuz-2.6.27-14-generic root=UUID=c712888e-5f65-485e-90b6-dfe1b0dcac0b ro  single
initrd		/boot/initrd.img-2.6.27-14-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		c712888e-5f65-485e-90b6-dfe1b0dcac0b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c712888e-5f65-485e-90b6-dfe1b0dcac0b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		c712888e-5f65-485e-90b6-dfe1b0dcac0b
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=c712888e-5f65-485e-90b6-dfe1b0dcac0b ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		c712888e-5f65-485e-90b6-dfe1b0dcac0b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c712888e-5f65-485e-90b6-dfe1b0dcac0b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		c712888e-5f65-485e-90b6-dfe1b0dcac0b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=c712888e-5f65-485e-90b6-dfe1b0dcac0b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		c712888e-5f65-485e-90b6-dfe1b0dcac0b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root



# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows Vista
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 


=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c712888e-5f65-485e-90b6-dfe1b0dcac0b /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6d7e2f94-94b4-4ef8-96c1-2be1e66269ae none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 216.7GB: boot/grub/menu.lst
 216.7GB: boot/grub/stage2
 216.7GB: boot/initrd.img-2.6.27-11-generic
 216.6GB: boot/initrd.img-2.6.27-14-generic
 216.6GB: boot/initrd.img-2.6.27-7-generic
 216.7GB: boot/vmlinuz-2.6.27-11-generic
 216.7GB: boot/vmlinuz-2.6.27-14-generic
 216.6GB: boot/vmlinuz-2.6.27-7-generic
 216.6GB: initrd.img
 216.7GB: initrd.img.old
 216.7GB: vmlinuz
 216.7GB: vmlinuz.old

---

### Post by oldfred on 2009-09-11
In my review of your system nothing stands out as wrong. You do have GRUB on sdb (the 200GB drive) which will not work since it points to a windows partition not a grub. But the GRUB on sda (320GB) should be correct and points to a menu.lst that looks ok. If Vista does not boot, try commenting out the two map lines with # signs and try again. 

Only if you wanted to directly boot the 200GB drive should you need to have windows boot in the MBR.

I see nothing about XP so where are you getting XP messages?

Just noticed the start and end of your Vista partition are almost the same. That cannot be good, but I am not sure of cure. I would suggest trying to repair the partition with gparted live disk unless someone else has a better suggestion.

Use testdisk to repair not gparted.

---

### Post by geek_overlord on 2009-09-12
yeah I fixed the xp issue. I'm going to work on the rest of this tomorrow afternoon as I've spent half the night playing Wii Sports and I'm pretty well beat. Thanks again Oldfred for helping me with all of this mess.

---

### Post by r.osmanov on 2009-09-12
There are two options at least:
[B]A. CLI way
B. GUI way
[/B]
**A. CLI way.**

1. Look for your Windows partition:
```
sudo df
```

2. Compare it with corresponding device:
```
sudo cat /boot/grub/device.map
```

3. Add lines like the following lines:
```
title        Windows Vista # or whatever
root        (hd0,0)       # or whatever    
makeactive
chainloader    +1
```
to apropriate place in /boot/grub/menu.lst (look at the file contents first)

**B. GUI way**
1. Install webmin:

```
sudo wget http://prdownloads.sourceforge.net/webadmin/webmin_1.480_all.deb
sudo dpkg -i webmin_1.480_all.deb
sudo apt- get install -f

```
Then follow post installation instructions(few lines) to launch webmin.
2. Go to [https://localhost:10000/](https://localhost:10000/) (or whatever it will be for you) and enter root login & password
3. Go to Hardware->GRUB Boot Loader 

And you have a handy tool to edit you grub ;)

---

### Post by r.osmanov on 2009-09-12
I'm sorry, I didn't notice much of the posts. However, I still think you should try webmin. 
Sometimes GUI applications having less performance help make configuration tasks (like this and e.g. partitioning) less painful. 

Regards.

---

### Post by oldfred on 2009-09-12
See also this thread even though it is Window7 the issues are the same with Vista.
[http://ubuntuforums.org/showthread.php?t=1261173](http://ubuntuforums.org/showthread.php?t=1261173)

Did you resize your Vista partition? If you had an old version of gparted or did not uncheck the box to have the round to cylinder unchecked it can cause partition issues with Windows.

One suggestion is testdisk, buckeyball has this suggestion  and Vista should be the same:
I'm not sure if 7 is the same but with XP you could stick the installation disk in and go to 'Repair'. In there you can run help I think and there is a command containing 'chkdisk'. Run that. Then 'fixboot' and 'fixmbr'.

If you do windows repairs, it may take over the MBR and you will have to use supergrub to fix the MBR.

---

### Post by geek_overlord on 2009-09-12
Alright so I have a few options here and while I can usually muddle my way through partitioning I can't back up my data. I have stuff on there like pictures of my daughter that I can't lose. Is there a way to move any of that data over to the Ubuntu drive and just wipe vista( which I can't utter enough obscenities to describe). I intended to wipe that drive and install XP anyway so as long as I get my data everything should be cool.

---

### Post by r.osmanov on 2009-09-12
> **oldfred said:**
> If you do windows repairs, it may take over the MBR and you will have to use supergrub to fix the MBR.

Virtually, Live CD can be used instead of supergrub. Once I had lost my grub also. 
I issued something like the following:
```
sudo -i
grub
find /boot/grub/stage1
# it outputs something like (hd0,0)
setup (hd0,0)  # or whatever
```and all woked.
Or update-grub should do the job. Once you booted on Ubuntu, webmin could be very handy for such simple grub management also. Webmin has a feature to backup all configuration files to one place. So you can restore alll the settings with a click.

---

### Post by r.osmanov on 2009-09-12
> **geek_overlord said:**
> Is there a way to move any of that data over to the Ubuntu drive and just wipe vista( which I can't utter enough obscenities to describe).
Normally, you should see your Windows partition from Ubuntu. It usually appears in Places menu.
Or you can use 
```
sudo fdisk -l
```
To know what is your partition and than mount it. (By choosing partition from "Places" you actually mount it before nautilus opens it in a new window)

---

### Post by presence1960 on 2009-09-12
```
============================= Boot Info Summary: ==============================

=> Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive
in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
=> [COLOR="Red"]Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #2 in
partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst[/COLOR].

```

sdb boots first in BIOS so the rootnoverify should be (hd0.0). It is the order of disk boot in BIOS that matters when using (hdx,y)  instead of UUID. Make sure sdb boots first in BIOS then make your windows entry in menu.lst this:

```
title          Windows <your version>
rootnoverify   (hd0,0)
chainloader    +1
```

since sdb boots first you do not need map lines. Map lines are only needed when windows is not on the first disk that boots in BIOS. In this case sdb boots first which is where windows is located and GRUB looks for menu.lst on boot drive #2 (sda)

---

### Post by presence1960 on 2009-09-12
> **r.osmanov said:**
> Virtually, Live CD can be used instead of supergrub. Once I had lost my grub also. 
I issued something like the following:
```
sudo -i
grub
find /boot/grub/stage1
# it outputs something like (hd0,0)
setup (hd0,0)  # or whatever
```and all woked.
Or update-grub should do the job. Once you booted on Ubuntu, webmin could be very handy for such simple grub management also. Webmin has a feature to backup all configuration files to one place. So you can restore alll the settings with a click.

here are those commands...telling someone whatever is not helpful.

```
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR, or "setup (hd0,1)" or 
   whatever your hard disk + partition # is, to install GRUB to a 
   partition.
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

Please note in # 6 setup (hdx) puts GRUB on MBR and setup (hdx,y) puts GRUB on the installation partition which is useful for chainloading off another GRUB that is already in MBR.


```

---

### Post by oldfred on 2009-09-12
Presence - I understand why changing the Bios boot order makes the entry for windows cleaner but the issue still is the Vista partition shows it starts in sector 63.

I misread the start end in my previous entry but from Herman's site in a link from the thread I provided before:
> Windows Vista and Windows 7 have departed from tradition and no longer have their partition starting in sector 63, after the first track of the hard disk. Instead, their first sectors start in number 2048, I don't know why.I do not know if gparted with the check box off will work but the comments in the other thread say testdisk should work to fix the partition start.

---

### Post by presence1960 on 2009-09-12
> **oldfred said:**
> Presence - I understand why changing the Bios boot order makes the entry for windows cleaner but the issue still is the Vista partition shows it starts in sector 63.

I misread the start end in my previous entry but from Herman's site in a link from the thread I provided before:
I do not know if gparted with the check box off will work but the comments in the other thread say testdisk should work to fix the partition start.

OP is getting invalid or unsupported executable file with this:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows Vista
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```

because sdb boots first. So (hd1,0) is actually on sda. I would try switching as I suggested, what is there to lose. The info on the boot info script output supports what I am saying. Vista appears to have all it's boot files intact.

If what I propose does not work I would then do a 2 part fix. I would restore Vista's bootloader to MBR of sdb by doing [this]("http://ubuntuforums.org/showthread.php?t=1014708"). After completion reboot and see if it boots right to Vista. if it does I would reboot and go into BIOS and make sda first in boot order. It already has GRUB installed to MBR then his entry in menu.lst will work as it is like this:
```
This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title Microsoft Windows Vista
rootnoverify (hd1,0)
savedefault
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1



```

The benefits would be that each disk would have the bootloader for the OS on it's disk on MBR. If one disk became unbootable you can switch boot order in BIOS and boot the other OS.

P.S. The check box off is still not guaranteed to work. here is a [link ]("http://bugzilla.gnome.org/show_bug.cgi?id=379482")to the as yet unresolved bug in resizing Vista's partition with gparted (or any outside partitioner). Until the bug is resolved it is still best to resize Vista by defragging at least once or twice & for good measure turn off system restore and then use Vista's disk management utility to shrink Vista. If done with gparted you are taking your chances. If Vista is rendered unbootable by resizing with gparted you just need to do [this]("http://ubuntuforums.org/showthread.php?t=1014708"). That will usually turn the trick.

---

