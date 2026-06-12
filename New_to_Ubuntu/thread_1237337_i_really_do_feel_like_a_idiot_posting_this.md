---
title: "i really do feel like a idiot posting this"
date: 2009-08-11
forum: New to Ubuntu
---

### Post by systemchris on 2009-08-11
just set up a dual boot for xp pro and jaunty 64bit

every attempt thus far to keep the ubuntu running relatively stable it all goes pear shaped on me :s i've tried burning fresh disks to make sure it isn't the install

the most i've done is use the system update thing to update to latest build and activate the nvidia 180 drivers it recommends

i just keep getting a load of problems with the archives, even when i just run the update manager and locking up on me etc etc

would you say my system is just unstable or am i actually doing something wrong?

sorry for the sheer vagueness of all this i'm just entirely unsure what's going wrong, cause i fix one hole using these forums as a guide and another 2 show themselves

---

### Post by Garrovick on 2009-08-11
What computer do your have?  Is it a 32 bit computer or a 64 bit computer?

---

### Post by systemchris on 2009-08-11
> **Garrovick said:**
> What computer do your have?  Is it a 32 bit computer or a 64 bit computer?

amd64 socket 939 4000+ it's a pretty early 64bit processor so i thought it should work

tried a 32bit install, i just keep getting package errors and everytime i follow the fix it just finds another one :s

previous ubuntu live cds refused to boot at all to be fair but i didn't think hardware would cause package and dpkg and list problems all the time

---

### Post by halitech on 2009-08-11
what actual video card do you have?

---

### Post by tom66 on 2009-08-11
Have you done a memory test?

---

### Post by systemchris on 2009-08-11
> **halitech said:**
> what actual video card do you have?

got a geforce 7900GS

also got an old bog standard ide hard drive

some generic ram i got from ebay

and an asus A8N32 - SLI motherboard

---

### Post by halitech on 2009-08-11
the 185 drivers should work

[http://www.nvidia.com/object/linux_display_ia32_185.18.31.html](http://www.nvidia.com/object/linux_display_ia32_185.18.31.html)

not sure how liked Envy is anymore but you could also try Envy to install the drivers (don't use it so not sure how good it is anymore)

---

### Post by LowSky on 2009-08-11
what kind of errors are you getting, I really doubt its hardware based, I run a AMD 64 3700+ (a modle very similar to yours) using 64bit Ubuntu on one of my boxes.

sounds more like a bad burn of your install CD or corrupting files from the hard drive, but I doubt the latter.

When you burn the ISO make sure it is at a slow speed, the slower the better for important CD, especially for operating systems. 

also what errors are you seeing? can you give an example verbatium. Thanks

---

### Post by systemchris on 2009-08-11
> **LowSky said:**
> what kind of errors are you getting, I really doubt its hardware based, I run a AMD 64 3700+ (a modle very similar to yours) using 64bit Ubuntu on one of my boxes.

sounds more like a bad burn of your install CD or corrupting files from the hard drive, but I doubt the latter.

When you burn the ISO make sure it is at a slow speed, the slower the better for important CD, especially for operating systems. 

also what errors are you seeing? can you give an example verbatium. Thanks

ill get round to burning another disk and see how it goes at a low speed :)

just libary errors of all sorts if i get another ill write ti down

---

### Post by systemchris on 2009-08-12
well today i'm on my ubuntu cause wow is having maintanence morning :p

run my update manager today and got a package problem and crash alert for linux-img-2.6.28-14-generic or something this is my screenshot

[http://img.photobucket.com/albums/v458/systemofachris/Screenshot-1.png](http://img.photobucket.com/albums/v458/systemofachris/Screenshot-1.png)

i get all sorts of errors all the time, i have a fresh cd which was burnt at 4x speed just to make sure but this is my current installation

edit: just got this, which i think is referring to the previous error "you have 1 broken package on your system"

using the package manager, my broken package is linux-restricted-modules-2.6.28-14-generic, i ran the fix broken packages option in 'edit' and got this error as a result: E: /var/cache/apt/archives/linux-image-2.6.28-14-generic_2.6.28-14.47_amd64.deb: corrupted filesystem tarfile - corrupted package archive

i tried the same thing through the command line with sudo apt-get -f install after a spt-get check and got back this as an error

The following extra packages will be installed:
  linux-image-2.6.28-14-generic
Suggested packages:
  fdutils linux-doc-2.6.28 linux-source-2.6.28
The following NEW packages will be installed
  linux-image-2.6.28-14-generic
0 upgraded, 1 newly installed, 0 to remove and 159 not upgraded.
1 not fully installed or removed.
Need to get 0B/24.2MB of archives.
After this operation, 112MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 101703 files and directories currently installed.)
Unpacking linux-image-2.6.28-14-generic (from .../linux-image-2.6.28-14-generic_2.6.28-14.47_amd64.deb) ...
Done.
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.28-14-generic_2.6.28-14.47_amd64.deb (--unpack):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.28-14-generic_2.6.28-14.47_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by systemchris on 2009-08-12
just done a sudo apt-get clean to remove the old archive and got a new one with the sudo apt-get -f install

it's asking me for a restart but it had one fail in the giant wall of text

Get: 1 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) jaunty-updates/main linux-image-2.6.28-14-generic 2.6.28-14.47 [24.2MB]
Fetched 24.2MB in 20s (1205kB/s)                                               
(Reading database ... 101703 files and directories currently installed.)
Unpacking linux-image-2.6.28-14-generic (from .../linux-image-2.6.28-14-generic_2.6.28-14.47_amd64.deb) ...
Done.
Setting up linux-image-2.6.28-14-generic (2.6.28-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-14-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.28-14-generic
Found kernel: /vmlinuz-2.6.28-11-generic
Found kernel: /memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-14-generic          
 *  nvidia (180.44)...                                                          nvidia (180.44): Installing module.
  Kernel headers for 2.6.28-14-generic are not installed.  Cannot install this module.
  Try installing linux-headers-2.6.28-14-generic or equivalent.
                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-restricted-modules-2.6.28-14-generic (2.6.28-14.19) ...
update-initramfs: Generating /boot/initrd.img-2.6.28-14-generic


sorry for all this posting, well i got another kernel appear in the grub list so i'm on that at the moment, so who knows!?

had a red circle for a moment in the top right but it seems to have gone again, just ran a check on the update manager and that said it was okay to update and i apparantly have no broken packages - let's pray

---

### Post by systemchris on 2009-08-12
the 2nd kernel it installed, after running the update manager again, and resseting, refuses to boot on me i get a line 41 error during init with the kernel sync :s

posting this on my old one atm

comes as something like /init: /scripts/functions : line 41 : bad sytnax

---

