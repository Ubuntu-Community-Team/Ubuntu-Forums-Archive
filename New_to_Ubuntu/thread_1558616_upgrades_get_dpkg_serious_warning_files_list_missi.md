---
title: "upgrades get dpkg: serious warning: files list missing assuming no files installed..."
date: 2010-08-22
forum: New to Ubuntu
---

### Post by GMachine_24 on 2010-08-22
hi - running 8.04 lts

When I update/upgrade my installation I get a lot of output to the effect of

dpkg: serious warning: files list file for package `openoffice.org-impress' missing, assuming package has no files currently installed.

Here is the entire code from the upgrade I just did:

```


user@user-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-headers-2.6.24-28 linux-headers-2.6.24-28-generic
  linux-image-2.6.24-28-generic
3 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 27.2MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy-updates/main linux-image-2.6.24-28-generic 2.6.24-28.75 [18.4MB]
Get:2 http://us.archive.ubuntu.com hardy-updates/main linux-headers-2.6.24-28 2.6.24-28.75 [8150kB]
Get:3 http://us.archive.ubuntu.com hardy-updates/main linux-headers-2.6.24-28-generic 2.6.24-28.75 [660kB]
Fetched 27.2MB in 38s (714kB/s)                                                
(Reading database ... 
dpkg: serious warning: files list file for package `openoffice.org-style-human' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-impress' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-restricted-modules-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-draw' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-image-generic' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-ubuntu-modules-2.6.24-28-generic' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-calc' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-image-2.6.24-27-generic' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libc6-i686' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `linux-generic' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libc6' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `openoffice.org-common' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `libkrb53' missing, assuming package has no files currently installed.
129419 files and directories currently installed.)
Preparing to replace linux-image-2.6.24-28-generic 2.6.24-28.73 (using .../linux-image-2.6.24-28-generic_2.6.24-28.75_i386.deb) ...
Done.
Unpacking replacement linux-image-2.6.24-28-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-28-generic
Found kernel: /boot/vmlinuz-2.6.24-27-generic
Found kernel: /boot/vmlinuz-2.6.24-26-generic
Found kernel: /boot/vmlinuz-2.6.24-25-generic
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Preparing to replace linux-headers-2.6.24-28 2.6.24-28.73 (using .../linux-headers-2.6.24-28_2.6.24-28.75_all.deb) ...
Unpacking replacement linux-headers-2.6.24-28 ...
Preparing to replace linux-headers-2.6.24-28-generic 2.6.24-28.73 (using .../linux-headers-2.6.24-28-generic_2.6.24-28.75_i386.deb) ...
Unpacking replacement linux-headers-2.6.24-28-generic ...
Setting up linux-image-2.6.24-28-generic (2.6.24-28.75) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.24-28-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.24-28.73 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.24-28.73 was configured last, according to dpkg)
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.24-28-generic
Found kernel: /boot/vmlinuz-2.6.24-27-generic
Found kernel: /boot/vmlinuz-2.6.24-26-generic
Found kernel: /boot/vmlinuz-2.6.24-25-generic
Found kernel: /boot/vmlinuz-2.6.24-24-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
Setting up linux-headers-2.6.24-28 (2.6.24-28.75) ...
Setting up linux-headers-2.6.24-28-generic (2.6.24-28.75) ...
user@user-desktop:~$ 

```


However, some - maybe all - of these packages are installed. I attempted to install one of them and got the message that the installed package was the most recent. Here:

```

user@user-desktop:~$ sudo apt-get install libc6
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libc6 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@user-desktop:~$

```

I can upgrade the Open Office package as it is old - v. 2.4 - but I rarely use it on this computer.

Anyway, if anyone has input on how to fix this I'd appreciate it.

TIA.

GM

---

### Post by cogier on 2010-08-22
It looks as if there has been an update issue somewhere. I would try the following to see if it helps.
```
sudo apt-get -f install
```
```
sudo apt-get autoremove
```
```
sudo apt-get purge
```
```
sudo apt-get clean
```

---

### Post by GMachine_24 on 2010-08-23
thanks for your reply. I did as you suggested - and picked a package to install and it went fine. although it wasn't an update from ubuntu it was a new package so I'll have to check the next time the blue arrow shows up and make sure that the errors aren't repeated. If that happens, I will marked this thread as "solved."

Thanks again for your help.

---

