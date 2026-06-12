---
title: "Ubuntu 9.04 not booting help please!"
date: 2009-10-02
forum: New to Ubuntu
---

### Post by Captainslacko on 2009-10-02
I have been itching to try Linux for some time. :popcorn: I picked up a copy of **Ubuntu 9.04** on Disk and took the plunge and loaded it as a dual boot on my Toshiba Laptop beside Windows XP. 
It worked fine for about one week:guitar: but after a sessions of loading and unloading some of the programs in Ubuntu, it stopped booting.
The bootup Sequence begins, I get to a gray screen, and then it hangs.:confused:
Where do I start with Ubuntu to restore/repair the boot sequence?
:popcorn:

---

### Post by boblemur on 2009-10-02
ok so there are a few things you can try

so first press:

```
ctrl + alt + f1
```

do you get a text login screen?. if so, then you have probably broken Xorg.

if not, then you arnt getting that far, if thats the case try

1. power the system on.
2. At the grub menu use arrow keys to select the boot line you use,
press 'e' to edit it
3. Press 'e' again (I think) to edit the first line of it
4. Go to the end of the line and delete the part 'quiet splash'
5. Enter to finish editing, then 'b' to boot.

and try and see any error messages that come up or anymore information that looks bad just before it hangs, or even where it hangs.

---

### Post by Captainslacko on 2009-10-02
> **boblemur said:**
> ok so there are a few things you can try
 
so first press:
 
```
ctrl + alt + f1
```
 
do you get a text login screen?. if so, then you have probably broken Xorg.
 
if not, then you arnt getting that far, if thats the case try
 
1. power the system on.
2. At the grub menu use arrow keys to select the boot line you use,
press 'e' to edit it
3. Press 'e' again (I think) to edit the first line of it
4. Go to the end of the line and delete the part 'quiet splash'
5. Enter to finish editing, then 'b' to boot.
 
and try and see any error messages that come up or anymore information that looks bad just before it hangs, or even where it hangs.
 
 
Thanks for the quick reply. Tried both suggestions.
 
ctrl, alt, f1 didn't do anything.
 
"e" "e" couldn't find anything saying quiet splash
 
 
When booting up I get the Starting Up.....
then the Ubuntu logo and load line underneath
then a grey screen that flashes a couple of times to black screen and back to grey
 
Any further suggestions would be appreciated
 
Thanks again](*,)

---

### Post by boblemur on 2009-10-02
im guessing that you are not running ubuntu 9.10 so you shouldnt be using grub 2

so when you get your grub menu. press down to cancel the timeout then select the top entry (the one you normally boot from).

and press 'e' and it should look like..
uuid ....
kernel ....
initrd ....
quiet

- select quiet
- press 'd' 
- select kernel
- press 'e' 
- and now you should see ...... ro quiet splash so delete "quiet splash"
and you are left with ro on the end.
- press enter
- press b (to boot) 

you will get alot of white writing... dont worry if you cant read it all :P.

let me know if the screen still goes gray or whether it hangs with any messages or errors

good luck, sorry my first instructions wernt very clear

---

### Post by presence1960 on 2009-10-03
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Captainslacko on 2009-10-03
> **boblemur said:**
> im guessing that you are not running ubuntu 9.10 so you shouldnt be using grub 2

so when you get your grub menu. press down to cancel the timeout then select the top entry (the one you normally boot from).

and press 'e' and it should look like..
uuid ....
kernel ....
initrd ....
quiet

- select quiet
- press 'd' 
- select kernel
- press 'e' 
- and now you should see ...... ro quiet splash so delete "quiet splash"
and you are left with ro on the end.
- press enter
- press b (to boot) 

you will get alot of white writing... dont worry if you cant read it all :P.

let me know if the screen still goes gray or whether it hangs with any messages or errors

good luck, sorry my first instructions wernt very clear


OK successfully followed these instructions, no change to boot up though still hanging at the same place and in the same way...no error messages.:confused:

---

### Post by boblemur on 2009-10-03
ok try selecting the 2nd entry on the list. (in grub)

it should be recovery mode. you will be given a root shell once it boots (hopefully)

then try run:

```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
dpkg-reconfigure xserver-xorg
reboot

```

and see if it works after that, if not then let me know...

---

### Post by Captainslacko on 2009-10-03
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.


Ok thanks did all this. Opened terminal pasted the code in and hit enter, as I guess this causes it to run in the absence of any other command to do so.

bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 

......was the result

thanks and regards

---

### Post by Captainslacko on 2009-10-03
> **boblemur said:**
> ok try selecting the 2nd entry on the list. (in grub)

it should be recovery mode. you will be given a root shell once it boots (hopefully)

then try run:

```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
dpkg-reconfigure xserver-xorg
reboot

```and see if it works after that, if not then let me know...


OK tried this, when the recovery mode booted I got the white writing flashing passed then to a menu, where the closest option seemed to be Drop to root shell prompt which I selected and got a message something about reboot not being a directory (I think)[-(

Thanks for sticking with this

---

### Post by Captainslacko on 2009-10-03
Let me also add that in the grub menu I seem to have 1- Ubuntu 9.04, 2- Ubuntu recovery, 3- Ubuntu 9.04, 4- Ubuntu recovery, Memtest and Windows XP. I have tried the changes in both Ubuntu 9.04 menus.

---

### Post by boblemur on 2009-10-03
> **Captainslacko said:**
> Ok thanks did all this. Opened terminal pasted the code in and hit enter, as I guess this causes it to run in the absence of any other command to do so.

bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 

......was the result

thanks and regards


1)i think you missed the link he was talking about: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

download that and then try it again :)

2) which I selected and got a message something about reboot not being a directory (I think).... are you able to try again and write down what it says. try get to the root console cause that would really help.. 

a quick question do you have /home on a separate partition? or is it all together?

---

### Post by presence1960 on 2009-10-03
> **Captainslacko said:**
> 

bash: /home/ubuntu/Desktop/boot_info_script*.sh: No such file or directory
ubuntu@ubuntu:~$ 

......was the result

thanks and regards

That means the boot info script you downloaded is not located on the desktop. Move it to the desktop and run the command.

---

### Post by pjforster on 2009-10-03
Hi there, looks like I am in the same boat. Very newbie.

I installed, dual boot thankfully, last week and I think I have installed a package I shouldnt have from the download / apps manager. I dont have my live cd or access to any bandwidth to download it.

I am going through about the same, will copy down and try your previous post but I get to the end of the load sequence and where my screen should come up it looks like the resolution resizes. It goes black (backlit) then the screen shuts off momentarily and then either stays lit but black or screen is off. This might repeat once or twice..

Tried the alt ctrl f1-f6, backspace and nothing.
Tried a few sudo dpkg commands to no avail also.

I get the screens ubuntu 9.04 kernal 2.6.28.15 and .11 normal boot and recovery.
I can get to a command promt and tried to reconfigure xserver-xorg. 

Any help greatly appreciated.

---

### Post by Captainslacko on 2009-10-05
> **boblemur said:**
> 1)i think you missed the link he was talking about: [http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

download that and then try it again :)

2) which I selected and got a message something about reboot not being a directory (I think).... are you able to try again and write down what it says. try get to the root console cause that would really help.. 

a quick question do you have /home on a separate partition? or is it all together?

to your quick question...I have XP on one partition and created a second partition with heaps of space, utilising the Ubuntu partitioning option when loading to my hard drive. Ubuntu is loaded entirely on the second partition. :guitar:

---

### Post by random turnip on 2009-10-05
Has it updated kernel?
When you get to the GRUB menu, does it give you more than one version of Ubuntu to boot into, each one being a different kernel.  If so then just boot into one lower down, updating kernels sometimes make Ubuntu not work on some machines.

---

### Post by Captainslacko on 2009-10-05
> **presence1960 said:**
> Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.


OK results.....
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #5 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

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

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9259b927

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   267,193,079   267,193,017   7 HPFS/NTFS
/dev/sda2         272,430,270   488,392,064   215,961,795   5 Extended
/dev/sda5         272,430,333   479,524,184   207,093,852  83 Linux
/dev/sda6         479,524,248   488,392,064     8,867,817  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="3CD0A989D0A94A4A" LABEL="S3A6758D002" TYPE="ntfs" 
/dev/sda5: UUID="3112c1e7-1ee0-4988-9a25-b602c6594e0e" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="14b806a6-8368-4618-9520-14db88106559" 

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


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 

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
# kopt=root=UUID=3112c1e7-1ee0-4988-9a25-b602c6594e0e ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=3112c1e7-1ee0-4988-9a25-b602c6594e0e

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
uuid        3112c1e7-1ee0-4988-9a25-b602c6594e0e
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3112c1e7-1ee0-4988-9a25-b602c6594e0e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        3112c1e7-1ee0-4988-9a25-b602c6594e0e
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=3112c1e7-1ee0-4988-9a25-b602c6594e0e ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        3112c1e7-1ee0-4988-9a25-b602c6594e0e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3112c1e7-1ee0-4988-9a25-b602c6594e0e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        3112c1e7-1ee0-4988-9a25-b602c6594e0e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=3112c1e7-1ee0-4988-9a25-b602c6594e0e ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        3112c1e7-1ee0-4988-9a25-b602c6594e0e
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
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
# / was on /dev/sda5 during installation
UUID=3112c1e7-1ee0-4988-9a25-b602c6594e0e /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=14b806a6-8368-4618-9520-14db88106559 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda5: Location of files loaded by Grub: ===================


 223.5GB: boot/grub/menu.lst
 223.5GB: boot/grub/stage2
 223.5GB: boot/initrd.img-2.6.28-11-generic
 223.6GB: boot/initrd.img-2.6.28-15-generic
 223.5GB: boot/vmlinuz-2.6.28-11-generic
 223.6GB: boot/vmlinuz-2.6.28-15-generic
 223.6GB: initrd.img
 223.5GB: initrd.img.old
 223.6GB: vmlinuz
 223.5GB: vmlinuz.old
=======Devices which don't seem to have a corresponding hard drive==============

sdb    :guitar::P:popcorn:

---

### Post by Captainslacko on 2009-10-05
> **random turnip said:**
> Has it updated kernel?
When you get to the GRUB menu, does it give you more than one version of Ubuntu to boot into, each one being a different kernel.  If so then just boot into one lower down, updating kernels sometimes make Ubuntu not work on some machines.


No both versions are identical  :popcorn::confused:

---

### Post by presence1960 on 2009-10-05
your boot info output looks good. i would say something you installed messed up your graphics. Boot into recovery mode. When the gui comes up scroll down to xfix and run that. Reboot and see what happens.

---

### Post by Captainslacko on 2009-10-05
> **presence1960 said:**
> your boot info output looks good. i would say something you installed messed up your graphics. Boot into recovery mode. When the gui comes up scroll down to xfix and run that. Reboot and see what happens.


thanks, tried that twice but still no improvement  :-k  [-o<

---

### Post by itsbrad212 on 2009-10-06
i would just use your ubuntu cd and boot into it. then, check out this thread for info:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by boblemur on 2009-10-07
> **itsbrad212 said:**
> i would just use your ubuntu cd and boot into it. then, check out this thread for info:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Sorry itsbrad212 but i fail to share you opinion. what exactly were you trying to get him to achieve, there is nothing wrong with his grub, so it would seem stupid to restore it.

Please provide more information about what you are trying to achieve, by directing him to that post?

Captainslacko:

i suggest you wait to see what itsbrads's point is before trying to restore grub...

its getting to the point where its probably worth your while concidering reinstalling. how much data do you have in your /home folder? and do you have an external hard disk large enough to hold that data?

---

### Post by Captainslacko on 2009-10-08
> **boblemur said:**
> Sorry itsbrad212 but i fail to share you opinion. what exactly were you trying to get him to achieve, there is nothing wrong with his grub, so it would seem stupid to restore it.

Please provide more information about what you are trying to achieve, by directing him to that post?

Captainslacko:

i suggest you wait to see what itsbrads's point is before trying to restore grub...

its getting to the point where its probably worth your while concidering reinstalling. how much data do you have in your /home folder? and do you have an external hard disk large enough to hold that data?


I think I am agreeing with you, it's a new install so backup is not necessary.
How do I do a reinstall? I have been looking but still stuck in Windows mindset and probably not seeing the obvious.:guitar::P:popcorn::KS

---

### Post by boblemur on 2009-10-08
First you will need the LiveCD, for the version you want to install i recommend 9.04 for now.

Boot into the live cd, and then double click install and follow the prompts. Be vary careful when installing as this will destory all of your / including /home. what you could try is, backup your /home (as that way all the programs you have will keep there settings and your personal files.

/home is a much smarter alternative to window's My Documents, /home stores folders such as .mozilla which firefox stores all its settings in, so if you backup /home then restore it, your computer will be exactly the same as before you reinstalled except without your programs.

When you are reinstalling make sure you know exactly what you are doing during the partitioning step. As im sure you know this step has fatal consequences for your data if done wrong. 

once again, make sure you do not format any ntfs or fat filesystems during install make sure the only filesystems you format are / and /home

which is /dev/sda5.

The ubuntu installer should make it easy for you to overwrite your existing ubuntu with a new one.

good luck if you find anything unclear please don't hesitate to ask :)

---

### Post by Captainslacko on 2009-10-10
> **boblemur said:**
> First you will need the LiveCD, for the version you want to install i recommend 9.04 for now.

Boot into the live cd, and then double click install and follow the prompts. Be vary careful when installing as this will destory all of your / including /home. what you could try is, backup your /home (as that way all the programs you have will keep there settings and your personal files.

/home is a much smarter alternative to window's My Documents, /home stores folders such as .mozilla which firefox stores all its settings in, so if you backup /home then restore it, your computer will be exactly the same as before you reinstalled except without your programs.

When you are reinstalling make sure you know exactly what you are doing during the partitioning step. As im sure you know this step has fatal consequences for your data if done wrong. 

once again, make sure you do not format any ntfs or fat filesystems during install make sure the only filesystems you format are / and /home

which is /dev/sda5.

The ubuntu installer should make it easy for you to overwrite your existing ubuntu with a new one.

good luck if you find anything unclear please don't hesitate to ask :)


Ok I get to step 4, the partitioning section, I highlight the Ubuntu partition and click forward and get a message saying something like No Root directory....go back. No matter what I do I can't seem to get past this. What do I need to do?

Thanks and regards:guitar::confused::confused::guitar:

---

### Post by boblemur on 2009-10-10
if you are doing auto install im unsure :S

you should click manual:

select dev/sda5 (your ext3 partition) and select edit, then make it ext3 tick the format box, and where it says "use for" select /

then select sda6 (your swap partition) and select edit then make it "swap area"

and then click ok, you should now have, 

/dev/sda5    <tick>     /     size
/dev/sda6    something  swap

make sure that the format box is not ticked for sda1

then click next :)

---

### Post by Captainslacko on 2009-10-11
> **boblemur said:**
> if you are doing auto install im unsure :S

you should click manual:

select dev/sda5 (your ext3 partition) and select edit, then make it ext3 tick the format box, and where it says "use for" select /

then select sda6 (your swap partition) and select edit then make it "swap area"

and then click ok, you should now have, 

/dev/sda5    <tick>     /     size
/dev/sda6    something  swap

make sure that the format box is not ticked for sda1

then click next :)

:confused::confused: There's something I'm not getting. I wrote down and followed the instructions.
When in the edit window there was no sda6 option, I ticked the format box, dropped down to the swap area option and it unticked the format box and deactivated it so i could not tick it. OK then yeilded the same message I was getting before....No root file system is defined. Please correct from the partitioning menu. :confused::(:confused::guitar:
Where am I going wrong??

---

### Post by Captainslacko on 2009-10-11
> **boblemur said:**
> if you are doing auto install im unsure :S

you should click manual:

select dev/sda5 (your ext3 partition) and select edit, then make it ext3 tick the format box, and where it says "use for" select /

then select sda6 (your swap partition) and select edit then make it "swap area"

and then click ok, you should now have, 

/dev/sda5    <tick>     /     size
/dev/sda6    something  swap

make sure that the format box is not ticked for sda1

then click next :)

:confused::confused: There's something I'm not getting. I wrote down and followed the instructions.
When in the edit window there was no sda6 option, I ticked the format box, dropped down to the swap area option and it unticked the format box and deactivated it so i could not tick it. OK then yeilded the same message I was getting before....No root file system is defined. Please correct from the partitioning menu. :confused::(:confused::guitar:
Where am I going wrong??

---

### Post by boblemur on 2009-10-12
you need to select:

/dev/sda5 and then goto edit, and select ext3 and tick format and then select under "use for"  just the / that is your root directory.

---

### Post by presence1960 on 2009-10-12
> **boblemur said:**
> you need to select:

/dev/sda5 and then goto edit, and select ext3 and tick format and then select under **"use for"  just the / that is your root directory**.

actually that is under mount point that you select /. "Use as" is where you select the filesystem you wish to use, i.e. ext2, ext3, ext4, etc.

---

### Post by Captainslacko on 2009-10-12
:popcorn::KS:guitar::guitar: Thanks Thanks and Thanks for all your help. This reply is from the Ubuntu OS on my laptop, freshly reinstalled. Great learning experience.

When operating in Broken Windows  I use a small password storage program passprom. It won't run in Ubuntu. It is password protected and stores all my login site URL's and login details. Is there a similar program for Ubuntu?

Anyhow thanks again for all your help.:popcorn::guitar::popcorn::guitar:

---

### Post by boblemur on 2009-10-13
The only one that i cant think of is just the default keyring which is under:

```
application > accessories > passwords and encryption keys
```

but other than that i think google would be a better way of finding something like that if the one in ubuntu isnt good enough

---

### Post by bigfootnmd on 2009-11-29
I have a similar problem with 9.10

I installed 9.04 and then upgraded to 9.10 (see my earlier post in Install forum).
After the upgrade to 9.10 finished I installed all updates.  Now my PC boots to the shell script login prompt.  I have tried fixing the xorg conf file as discussed in this thread.I am STUCK.

Problem Solved.  I copied my xorg.failsafe.conf to my xorg.conf.

---

