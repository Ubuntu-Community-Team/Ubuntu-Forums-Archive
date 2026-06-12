---
title: "Upgrade Kernel Error"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-05-11
I had a few upgrades suggested, after I upgraded (or rather tried to upgrade) in synaptic I got the following error:

```

Do you want to continue [Y/n]? y
Setting up linux-image-2.6.28-12-generic (2.6.28-12.43) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.28-12-generic
Running postinst hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-12-generic
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-12-generic          
 *  nvidia (180.44)...                                                          nvidia (180.44): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/postinst.d/nvidia-common
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.28-12-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.28-12-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-restricted-modules-2.6.28-12-generic:
 linux-restricted-modules-2.6.28-12-generic depends on linux-image-2.6.28-12-generic; however:
  Package linux-image-2.6.28-12-generic is not configured yet.
dpkg: error processing linux-restricted-modules-2.6.28-12-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.28-12-generic; however:
  Package linux-image-2.6.28-12-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-restricted-modules-generic:
 linux-restricted-modules-generic depends on linux-restricted-modules-2.6.28-12-generic; however:
  Package linux-restricted-modules-2.6.28-12-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configNo apport report written because the error message indicates its a followup error from a previous failure.
           No apport report written because the error message indicates its a followup error from a previous failure.
                                     No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
 ure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.28.12.16); however:
  Package linux-image-generic is not configured yet.
 linux-generic depends on linux-restricted-modules-generic (= 2.6.28.12.16); however:
  Package linux-restricted-modules-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.28-12-generic (2.6.28-12.43) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-12-generic          
 *  nvidia (180.44)...                                                          nvidia (180.44): Already installed on this kernel.
                                                                         [ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.28-12-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.28-12-generic (--configure):
 subprocess post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.28-12-generic; however:
  Package linux-headers-2.6.28-12-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.28-12-generic
 linux-restricted-modules-2.6.28-12-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

My Sources:

```

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.                                    

deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty main restricted

## Major bug fix updates produced after the final release of the
## distribution.                                                
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in     
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.                                                                   
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in      
## multiverse WILL NOT receive any review or updates from the Ubuntu        
## security team.                                                           
deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-security universe

## Uncomment the following two lines to add software from the 'backports'
## repository.                                                           
## N.B. software from this repository may not have been tested as        
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.                               
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is 
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.                                                                
deb http://archive.canonical.com/ubuntu jaunty partner
deb-src http://archive.canonical.com/ubuntu jaunty partner


###################################################################################################################

#Personal Packages

#Gnome-Do
deb http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/do-core/ppa/ubuntu jaunty main

#Dropbox
deb http://linux.getdropbox.com/ubuntu jaunty main
deb-src http://linux.getdropbox.com/ubuntu jaunty main

#Medibuntu
deb http://packages.medibuntu.org/ jaunty free non-free

#Amarok 1.4
deb http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/bogdanb/ppa/ubuntu jaunty main

#VLC 1.0
deb http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/kow/ppa/ubuntu jaunty main

#Gm-Notify
deb http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu jaunty main

#Chromium
deb http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/chromium-daily/ppa/ubuntu jaunty main
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe

```

Any thoughts?

---

### Post by jhonyrod on 2009-05-11
Try:
```
sudo dpkg --configure -a
```
If it doesn't work try:
```
sudo apt-get -f install
```
If it doesn't work too try purging those packages and then reinstalling them, I had that kind of errors many times...
```
sudo apt-get purge (package names here)
sudo apt get install (package names here)
```

---

### Post by abhiroopb on 2009-05-11
First two commands didn't work (same errors).

I purged the various kernels that were trying to update, etc and I got the following:

```

sudo apt-get purge linux-image-2.6.28-12-generic linux-restricted-modules-2.6.28-12-generic linux-image-generic linux-restricted-modules-generic linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-generic* linux-image-2.6.28-12-generic* linux-image-generic*
  linux-restricted-modules-2.6.28-12-generic*
  linux-restricted-modules-generic*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
7 not fully installed or removed.
After this operation, 98.4MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 144505 files and directories currently installed.)
Removing linux-generic ...
Removing linux-restricted-modules-generic ...
Removing linux-restricted-modules-2.6.28-12-generic ...
rmdir: failed to remove `/lib/modules/2.6.28-12-generic/volatile/': No such file or directory
update-initramfs: Generating /boot/initrd.img-2.6.28-12-generic
Purging configuration files for linux-restricted-modules-2.6.28-12-generic ...
Removing linux-image-generic ...
Removing linux-image-2.6.28-12-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms
Uninstalling: nvidia 180.44 (2.6.28-12-generic) (i686)

-------- Uninstall Beginning --------
Module:  nvidia
Version: 180.44
Kernel:  2.6.28-12-generic (i686)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

nvidia.ko:
 - Uninstallation
   - Deleting from: /lib/modules/2.6.28-12-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.
depmod....

DKMS: uninstall Completed.
run-parts: executing /etc/kernel/prerm.d/last-good-boot
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz is a damaged link
Removing symbolic link vmlinuz 
 you may need to re-run your boot loader[grub]
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img is a damaged link
Removing symbolic link initrd.img 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.28-12-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-headers-2.6.28-12-generic (2.6.28-12.43) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.28-12-generic                                                                                
 *  nvidia (180.44)...                                                     nvidia (180.44): Installing module.
......
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.28-12-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.28-12-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.28-12-generic; however:
  Package linux-headers-2.6.28-12-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                               Errors were encountered while processing:
 linux-headers-2.6.28-12-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Thanks a lot!

---

### Post by abhiroopb on 2009-05-11
Tried everything the error is still there.

Cleaned up my sources.list...

```

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main universe restricted multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty main universe restricted multiverse #Added by software-properties

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) jaunty-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) jaunty-security restricted main universe

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe main multiverse restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-updates universe main multiverse restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-proposed universe main multiverse restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-proposed universe main multiverse restricted

deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) jaunty-backports main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) jaunty partner

###################################################################################################################

#Personal Packages

#Gnome-Do
deb [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/do-core/ppa/ubuntu](http://ppa.launchpad.net/do-core/ppa/ubuntu) jaunty main

#Dropbox
deb [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) jaunty main
deb-src [http://linux.getdropbox.com/ubuntu](http://linux.getdropbox.com/ubuntu) jaunty main

#Medibuntu
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) jaunty free non-free

#Amarok 1.4
deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main

#VLC 1.0
deb [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/kow/ppa/ubuntu](http://ppa.launchpad.net/kow/ppa/ubuntu) jaunty main

#Gm-Notify
deb [http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu](http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu](http://ppa.launchpad.net/gm-notify-maintainers/ppa/ubuntu) jaunty main

#Chromium
deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) jaunty main

#OpenOffice
deb [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ppa/ubuntu) jaunty main

#Compiz Fusion
deb [http://ppa.launchpad.net/compiz/ppa/ubuntu](http://ppa.launchpad.net/compiz/ppa/ubuntu) jaunty main

#Free Fonts
deb [http://ppa.launchpad.net/corenominal/ubuntu](http://ppa.launchpad.net/corenominal/ubuntu) hardy main

#VirtualBox
deb [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) jaunty non-free

#Liferea
deb [http://ppa.launchpad.net/liferea/ppa/ubuntu](http://ppa.launchpad.net/liferea/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/liferea/ppa/ubuntu](http://ppa.launchpad.net/liferea/ppa/ubuntu) jaunty main
deb [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/webkit-team/ppa/ubuntu](http://ppa.launchpad.net/webkit-team/ppa/ubuntu) jaunty main

```

---

### Post by abhiroopb on 2009-05-11
Other updates seem to not want to work either!! :(

---

### Post by cknipe on 2009-09-16
Quite frankly - it looks to me that the package Ubuntu has on their FTP servers is corrupt :( 
 
```

root@netsonic:/var/cache/apt/archives# wget [ftp://ftp.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb](ftp://ftp.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb)
--2009-09-16 13:34:26--  [ftp://ftp.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb](ftp://ftp.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb)
           => `linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb'
Resolving [ftp.ubuntu.com]("ftp://ftp.ubuntu.com")... 91.189.88.46, 91.189.88.140, 91.189.88.31, ...
Connecting to [ftp.ubuntu.com|91.189.88.46|:21]("ftp://ftp.ubuntu.com|91.189.88.46|:21")... connected.
Logging in as anonymous ... Logged in!
==> SYST ... done.    ==> PWD ... done.
==> TYPE I ... done.  ==> CWD /ubuntu/pool/main/l/linux ... done.
==> SIZE linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb ... 23070986
==> PASV ... done.    ==> RETR linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb ... done.
Length: 23070986 (22M)
100%[===================================================================================================================================================================================================>] 23,070,986  23.2K/s   in 15m 20s
2009-09-16 13:49:49 (24.5 KB/s) - `linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb' saved [23070986]
root@netsonic:/var/cache/apt/archives# dpkg -i linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb
(Reading database ... 17942 files and directories currently installed.)
Unpacking linux-image-2.6.27-14-server (from linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb) ...
Done.
dpkg: error processing linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb (--install):
 corrupted filesystem tarfile - corrupted package archive
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.27-7-server
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done
Errors were encountered while processing:
 linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb
root@netsonic:/var/cache/apt/archives#

```
 
And...
```

[EMAIL="root@netsonic:/var/cache/apt/archives"]root@netsonic:/var/cache/apt/archives[/EMAIL]# dpkg-deb -x linux-image-2.6.27-14-server_2.6.27-14.41_amd64.deb /tmp/a
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
dpkg-deb: subprocess tar returned error exit status 2

```
 
 
 
Which brings up another question... Is there no checksum validation on the files (packages) that is downloaded?? Surely, this package must have been tested, a MD5 (or similar) checksum taken, and downloads verified against it?

---

