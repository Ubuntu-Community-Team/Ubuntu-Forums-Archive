---
title: "linux-image-2.6.27-7-generic update problem"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by dan1973 on 2009-04-17
When trying to install updates, system has problems with above mentioned update. Its response is as follows:

E: /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb: unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version

What do I do?

---

### Post by unutbu on 2009-04-17
Please post the output of 
```

ls -l /boot/vmlinuz-2.6.27-7-generic
df -T /boot/vmlinuz-2.6.27-7-generic
```

---

### Post by dan1973 on 2009-04-17
~$ ls -l /boot/vmlinuz-2.6.27-generic
ls: cannot access /boot/vmlinuz-2.6.27-generic: No such file or directory

~$ df -T /boot/vmlinuz-2.6.27-generic
df: `/boot/vmlinuz-2.6.27-generic': No such file or directory
df: no file systems processed

does this help?

---

### Post by unutbu on 2009-04-17
Yes, that is very helpful. The reason why you were getting the error message "unable to make backup link" is because the file it was trying to link to does not exist.

Your system seems to think that you have the linux-image-2.6.27-7-generic package installed, when in fact, at least one file is missing. 

Let's try to trick the system into thinking you have the missing file:
Type
```

sudo touch /boot/vmlinuz-2.6.27-7-generic
```

This will create an empty dummy file.
Then try installing the updates again.

---

### Post by dan1973 on 2009-04-17
No luck yet.:(
P.S. was there supposed to be a message returned after i entered the command?

---

### Post by dan1973 on 2009-04-17
i have also just noticed on the update description this message:

You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed. 

Should i be paying attention to this and if so where will i find this upgrade, and will it stop prompting me to install the linux-image-2.6.27-7?

---

### Post by unutbu on 2009-04-17
You probably already have the linux-generic package installed, since it is installed by default on Ubuntu.

After entering the "sudo touch" command, and trying to install updates, what is the error message you are now receiving? Is it the same as before, or is it a new error message?

Are you running
```

sudo apt-get update
sudo apt-get upgrade
```

or some other command?

PS. To answer your other question, the "sudo touch" command gives no output.

---

### Post by dan1973 on 2009-04-17
The error message was exactly the same as before.
I haven't been usin the terminal commands for the update, have been following the annoying red exclamation mark on the top right of my task bar. It takes me straight to the update manager where the offending package stares out at me. 

Should i update with command?

---

### Post by unutbu on 2009-04-17
Please run 
```

sudo apt-get update
sudo apt-get upgrade
```
and post all the output.

Since the output could be long, please use [URL="http://ubuntuforums.org/showpost.php?p=5490091&postcount=43 "][noparse]```
...
```[/noparse][/URL] tags.

---

### Post by dan1973 on 2009-04-17
```
dan@ubuntu:~$ sudo apt-get update
[sudo] password for dan: 
Hit http://gb.archive.ubuntu.com intrepid Release.gpg
Hit http://gb.archive.ubuntu.com intrepid/main Translation-en_GB               
Hit http://archive.canonical.com intrepid Release.gpg                          
Ign http://archive.canonical.com intrepid/partner Translation-en_GB            
Hit http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB         
Hit http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB           
Hit http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB         
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg                  
Hit http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB       
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB 
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB   
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB 
Hit http://archive.ubuntu.com intrepid Release.gpg                             
Hit http://archive.canonical.com intrepid Release                              
Hit http://gb.archive.ubuntu.com intrepid Release                              
Hit http://archive.ubuntu.com intrepid Release                                 
Hit http://gb.archive.ubuntu.com intrepid-updates Release                      
Ign http://archive.canonical.com intrepid/partner Packages                     
Hit http://gb.archive.ubuntu.com intrepid/main Packages                        
Ign http://archive.canonical.com intrepid/partner Sources                      
Hit http://archive.ubuntu.com intrepid/main Sources                            
Hit http://archive.canonical.com intrepid/partner Packages                     
Hit http://gb.archive.ubuntu.com intrepid/restricted Packages                  
Hit http://gb.archive.ubuntu.com intrepid/restricted Sources                   
Hit http://gb.archive.ubuntu.com intrepid/main Sources                         
Hit http://gb.archive.ubuntu.com intrepid/multiverse Sources                   
Hit http://gb.archive.ubuntu.com intrepid/universe Sources                     
Hit http://archive.ubuntu.com intrepid/restricted Sources                      
Hit http://archive.canonical.com intrepid/partner Sources                      
Hit http://gb.archive.ubuntu.com intrepid/universe Packages                    
Hit http://gb.archive.ubuntu.com intrepid/multiverse Packages               
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources              
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources        
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB
Hit http://security.ubuntu.com intrepid-security Release
Hit http://security.ubuntu.com intrepid-security/main Packages
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Reading package lists... Done
dan@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.27-7-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.0MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get: 1 http://gb.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-7-generic 2.6.27-7.16 [23.0MB]
21% [1 linux-image-2.6.27-7-generic 5031185/23.0MB 21%]         120kB/s 2min29s^22% [1 linux-image-2.6.27-7-generic 5211761/23.0MB 22%]        93.0kB/s 3min11s^22% [1 linux-image-2.6.27-7-generic 5273321/23.0MB 22%]        93.0kB/s 3min10s^23% [1 linux-image-2.6.27-7-generic 5333513/23.0MB 23%]        93.0kB/s 3min10s^Fetched 23.0MB in 3min13s (119kB/s)                                            
(Reading database ... 134923 files and directories currently installed.)
Preparing to replace linux-image-2.6.27-7-generic 2.6.27-7.14 (using .../linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.27-7-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb (--unpack):
 unable to make backup link of `./boot/vmlinuz-2.6.27-7-generic' before installing new version: Operation not permitted
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-generic
Found kernel: /boot/vmlinuz-2.6.27-11-generic
Found kernel: /boot/vmlinuz-2.6.27-7-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-7-generic_2.6.27-7.16_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
dan@ubuntu:~$ 
```


It was looking good right up to the end - too soon to hope.

---

### Post by unutbu on 2009-04-17
Are you, perchance, using Wubi?
Also, please post the output of these commands:
```

df -T /boot/vmlinuz-2.6.27-7-generic
lsattr /boot/vmlinuz-2.6.27-7-generic

```
(It should be different, now that you've run the "sudo touch" command.)

---

### Post by dan1973 on 2009-04-18
How did you guess? 
Does this mean that yet again, windows is the source of my troubles?

```
dan@ubuntu:~$ df -T /boot/vmlinuz-2.6.27-generic
Filesystem    Type   1K-blocks      Used Available Use% Mounted on
/dev/sda3     vfat    56294048  46844192   9449856  84% /host
dan@ubuntu:~$ lsattr /boot/vmlinuz-2.6.27-generic
lsattr: Inappropriate ioctl for device While reading flags on /boot/vmlinuz-2.6.27-generic
dan@ubuntu:~$ 

```

hope this helps.

---

### Post by unutbu on 2009-04-18
I've seen this problem before. It is discussed on this bugs.launchpad page: [https://bugs.launchpad.net/wubi/+bug/252900](https://bugs.launchpad.net/wubi/+bug/252900).

The problem is that your /boot is located on a FAT (probably FAT32) partition. 
Indeed, your Windows OS is on a FAT partition.

The installer script for the upgraded version of linux-image-2.6.27-7-generic
wants to make a symlink in the /boot directory, but this operation fails because
the VFAT filesystem format does not have a notion of symlinks.

The bugs.launchpad page discusses a number of solutions to the problem.

The first one, suggested by magowiz, seem complicated to me, and has the disadvantage that you would have to go through that process every time you wanted to upgrade the kernel. Let's pass on this solution.

The second option is to convert your entire FAT partition to NTFS.
Here are instructions on how to do that:
[https://bugs.launchpad.net/wubi/+bug/252900/comments/9](https://bugs.launchpad.net/wubi/+bug/252900/comments/9)

The third option is to transfer Ubuntu into a partition of its own.
Instruction on how to do that are here: [http://lubi.sourceforge.net/lvpm.html](http://lubi.sourceforge.net/lvpm.html)

A fourth solution is to backup your data on Ubuntu (such as your home directory),
then delete your Wubi installation, and use the LiveCD to do a normal installation of Ubuntu into a partition of its own.

A fifth option is to "pin" your kernel version to the current version. Then the update manager will stop bothering you about an upgrade for the kernel being available.

---

### Post by dan1973 on 2009-04-18
First things first, thank you so much for your kind advice and patience. I haven't yet tried and of the solutions as what follows ma affect my decision. 

I'm not sure what to do.

When my computer tries to boot into ubuntu I am now receiving an error message as follows: well almost as follows, had to write it manually first!

booting 'ubuntu 8.10, kernel 2.6.27-generic'
filesystem is fat,partition type 0X0C
The current working directory (i.e., the relative path) is ubuntu/disks
kernel   /boot/vmlinuz-2.6.27-generic  root=UUID=01D0-39CA   loop =/ubuntu/disks/root.disk ro ROOTFLAGS = sync quiet splash

Error 13: invalid or unsupported executable format
press key to continue.

When offered the boot selection, i chose Ubuntu 8.10 kernel 2.6.27-11-generic. System booted up fine, seems to be no visible differences, and also the update icon doesn't warn me about the 2.6.27 update.

What does this all mean? Is it ok to boot up into the 2.6.27-11 version and if so how do i get the system to do this from the start without showing the Error 13 message?

Will i still get the 'update' problem when booting into this version?

Must go offline for a while until tonight - families huh!

---

### Post by unutbu on 2009-04-18
I think when you point GRUB (the bootloader) to boot a kernel (e.g. /boot/vmlinuz-2.6.27-generic) which is missing, you get Error 13. I think this is happening to you because the installer got far enough to tell GRUB to boot /boot/vmlinuz-2.6.27-generic, but it failed to create the file. 

Fixing the original problem should fix this problem too.

Actually, it has just occurred to me that 11 is a bigger number than 7.
So by booting "Ubuntu 8.10 kernel 2.6.27-**11**-generic" you are using a "better" kernel than kernel version 2.6.27-**7**-generic (which is the kernel you are getting when booting "ubuntu 8.10, kernel 2.6.27-generic").

So maybe we can fix the whole problem by simply uninstalling all packages related to 2.6.27-7:
To do that, run this command in a terminal:
```

dpkg --get-selections | grep 2.6.27-7
```
The output should look something like this:
```

linux-headers-2.6.27-7				install
linux-headers-2.6.27-7-generic			install
linux-image-2.6.27-7-generic			install
linux-restricted-modules-2.6.27-7-generic	install
```

If you remove each of the packages listed as "install"ed, then the update manager will stop trying to upgrade linux-image-2.6.27-7-generic. 

I think the boot error, "Error 13", should go away too. If not, we can fix it manually by editing /boot/grub/menu.lst.

---

### Post by dan1973 on 2009-04-18
Instead of anything listed with install following it, i get the following:

```
dan@ubuntu:~$ dpkg --get-selections | grep 2.6.27-7
linux-image-2.6.27-7-generic			deinstall
linux-restricted-modules-2.6.27-7-generic	deinstall
dan@ubuntu:~$ 
```

should i remove these packages?

---

### Post by unutbu on 2009-04-18
Maybe my understanding of what's going on is not as good as as I thought.

The output from "dpkg --get-selections" says that linux-image-2.6.27-7-generic is not installed (or has already been uninstalled).

If that is so, I don't see why update manager should want to install it.

Would you please post the output of 

```
dpkg --get-selections | grep linux
sudo apt-get update
cat /boot/grub/menu.lst
ls -l /boot
```

---

### Post by dan1973 on 2009-04-18
Update manager doesn't want to update when i have booted into the 2.6.27-11-generic, which is what i am using at the moment due to start up error problem mentioned.

Would like to boot up into this -11 version without the error message and the trying to boot 2.6.27-7-generic.

here are your requested printouts:

```

dan@ubuntu:~$ dpkg --get-selections | grep linux
libselinux1					install
linux-firmware					install
linux-generic					install
linux-headers-2.6.27-11				install
linux-headers-2.6.27-11-generic			install
linux-headers-generic				install
linux-image-2.6.27-11-generic			install
linux-image-2.6.27-7-generic			deinstall
linux-image-generic				install
linux-libc-dev					install
linux-restricted-modules-2.6.27-11-generic	install
linux-restricted-modules-2.6.27-7-generic	deinstall
linux-restricted-modules-common			install
linux-restricted-modules-generic		install
linux-sound-base				install
syslinux					install
util-linux					install
dan@ubuntu:~$ sudo apt-get update
[sudo] password for dan: 
Hit http://gb.archive.ubuntu.com intrepid Release.gpg
Hit http://gb.archive.ubuntu.com intrepid/main Translation-en_GB               
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB        
Hit http://archive.ubuntu.com intrepid Release.gpg                             
Hit http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB         
Hit http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB           
Hit http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB         
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg                  
Hit http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB       
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB 
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB   
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB 
Hit http://gb.archive.ubuntu.com intrepid Release                              
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_GB                   
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_GB                   
Hit http://ppa.launchpad.net intrepid Release.gpg                              
Ign http://ppa.launchpad.net intrepid/main Translation-en_GB                   
Hit http://archive.ubuntu.com intrepid Release                                 
Hit http://gb.archive.ubuntu.com intrepid-updates Release                      
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB  
Hit http://security.ubuntu.com intrepid-security Release                       
Get: 1 http://dl.google.com stable Release.gpg [189B]                          
Ign http://dl.google.com stable/non-free Translation-en_GB                     
Hit http://ppa.launchpad.net intrepid Release                                  
Hit http://ppa.launchpad.net intrepid Release                                  
Hit http://ppa.launchpad.net intrepid Release                                  
Hit http://archive.canonical.com intrepid Release.gpg                          
Ign http://archive.canonical.com intrepid/partner Translation-en_GB            
Get: 2 http://dl.google.com stable Release [1300B]                             
Hit http://gb.archive.ubuntu.com intrepid/main Packages                        
Hit http://packages.medibuntu.org intrepid Release.gpg                         
Ign http://packages.medibuntu.org intrepid/free Translation-en_GB              
Hit http://archive.canonical.com intrepid Release                              
Hit http://archive.ubuntu.com intrepid/main Sources                            
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_GB          
Hit http://packages.medibuntu.org intrepid Release                             
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Hit http://archive.ubuntu.com intrepid/restricted Sources                      
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Hit http://security.ubuntu.com intrepid-security/universe Packages             
Ign http://ppa.launchpad.net intrepid/main Packages                            
Ign http://ppa.launchpad.net intrepid/main Packages                            
Hit http://security.ubuntu.com intrepid-security/universe Sources              
Hit http://security.ubuntu.com intrepid-security/multiverse Packages           
Hit http://security.ubuntu.com intrepid-security/multiverse Sources            
Get: 3 http://dl.google.com stable/non-free Packages [966B]                    
Ign http://archive.canonical.com intrepid/partner Packages                     
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://packages.medibuntu.org intrepid/free Packages                       
Ign http://repository.cairo-dock.org intrepid Release.gpg                      
Ign http://repository.cairo-dock.org intrepid/cairo-dock Translation-en_GB     
Hit http://ppa.launchpad.net intrepid/main Packages                            
Ign http://archive.canonical.com intrepid/partner Sources                      
Hit http://packages.medibuntu.org intrepid/non-free Packages                   
Hit http://ppa.launchpad.net intrepid/main Packages                            
Hit http://archive.canonical.com intrepid/partner Packages                     
Ign http://repository.cairo-dock.org intrepid Release                          
Hit http://archive.canonical.com intrepid/partner Sources                      
Ign http://repository.cairo-dock.org intrepid/cairo-dock Packages              
Hit http://repository.cairo-dock.org intrepid/cairo-dock Packages              
Hit http://gb.archive.ubuntu.com intrepid/restricted Packages     
Hit http://gb.archive.ubuntu.com intrepid/restricted Sources      
Hit http://gb.archive.ubuntu.com intrepid/main Sources
Hit http://gb.archive.ubuntu.com intrepid/multiverse Sources
Hit http://gb.archive.ubuntu.com intrepid/universe Sources
Hit http://gb.archive.ubuntu.com intrepid/universe Packages
Hit http://gb.archive.ubuntu.com intrepid/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://wine.budgetdedicated.com intrepid Release.gpg     
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_GB
Hit http://wine.budgetdedicated.com intrepid Release
Ign http://wine.budgetdedicated.com intrepid/main Packages
Hit http://wine.budgetdedicated.com intrepid/main Packages
Fetched 2455B in 2s (1079B/s)
Reading package lists... Done
dan@ubuntu:~$ cat /boot/grub/menu.lst
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
# kopt=root=UUID=01D0-39CA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=sync

## default grub root device
## e.g. groot=(hd0,0)
# groot=()/ubuntu/disks

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

title		Ubuntu 8.10, kernel 2.6.27-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-generic root=UUID=01D0-39CA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=sync quiet splash 

title		Ubuntu 8.10, kernel 2.6.27-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-generic root=UUID=01D0-39CA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=sync  single

title		Ubuntu 8.10, kernel 2.6.27-11-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=01D0-39CA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=sync quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=01D0-39CA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=sync  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, memtest86+
root		()/ubuntu/disks
kernel		/boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows XP Media Center Edition
root		(hd0,1)
savedefault
chainloader	+1

dan@ubuntu:~$ ls -l /boot
total 13184
-rwxr-xr-x 1 root root  504280 2009-04-01 23:09 abi-2.6.27-11-generic
-rwxr-xr-x 1 root root   85310 2009-04-01 23:09 config-2.6.27-11-generic
drwxr-xr-x 2 root root   32768 2009-04-18 11:27 grub
-rwxr-xr-x 1 root root 8930012 2009-04-16 19:29 initrd.img-2.6.27-11-generic
-rwxr-xr-x 1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rwxr-xr-x 1 root root 1354796 2009-04-01 23:09 System.map-2.6.27-11-generic
-rwxr-xr-x 1 root root    1131 2009-04-01 23:11 vmcoreinfo-2.6.27-11-generic
-rwxr-xr-x 1 root root 2340384 2009-04-01 23:09 vmlinuz-2.6.27-11-generic
-rwxr-xr-x 1 root root       0 2009-04-17 22:19 vmlinuz-2.6.27-generic
dan@ubuntu:~$ 


```

---

### Post by unutbu on 2009-04-18
I think this should fix the Error 13 problem:
```

gksu gedit /boot/grub/menu.lst
```

Remove these two boot stanzas:
```

title		Ubuntu 8.10, kernel 2.6.27-generic
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-generic root=UUID=01D0-39CA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=sync quiet splash 

title		Ubuntu 8.10, kernel 2.6.27-generic (recovery mode)
root		()/ubuntu/disks
kernel		/boot/vmlinuz-2.6.27-generic root=UUID=01D0-39CA loop=/ubuntu/disks/root.disk ro ROOTFLAGS=sync  single

```
Save and exit gedit. Shutdown and reboot to make sure the change to menu.lst works.

The above boot stanzas won't work because they try to boot /boot/vmlinuz-2.6.27-generic, but according to "ls -l /boot", this file is empty:
```

-rwxr-xr-x 1 root root       0 2009-04-17 22:19 vmlinuz-2.6.27-generic
```

You won't be able to boot kernel version 2.6.27-7 anymore (unless you reinstall the packages), but I don't think you should need to because you have version 2.6.27-11, which should be better.

---

### Post by dan1973 on 2009-04-18
Thou art truely wise....!

....and all my problems just melted away. System boots-up great and no update problems either. 

Many heartfelt thanks, Dan.:D:D

---

