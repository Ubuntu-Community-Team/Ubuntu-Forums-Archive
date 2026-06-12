---
title: "Lost connection to build in wifi after installing driver for USB wifi card"
date: 2017-02-22
forum: Networking &amp; Wireless
---

### Post by Dan Z on 2017-02-22
Ubuntu 14.04

Built in WIFI was working fine except at work, it would connect ok, but no internet. Win 10 worked fine. I bought a USB wifi adapter as a test. It locked up the PC. Has to HARD reboot. It uses rtl8192cu driver. 

Research showed an updated driver 8192cu. So I installed it as below:

From Internet:
Ensure you have the necessary prerequisites:

sudo apt-get install linux-headers-generic build-essential dkms
Clone this repository:

git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
Set it up as a DKMS module:

sudo dkms add ./rtl8192cu-fixes
Build and install it (this version number may change, it is .10 as of october 19 2015

sudo dkms install 8192cu/1.10
Refresh the module list:

sudo depmod -a
Ensure the native (and broken) kernel driver is blacklisted:

sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
And reboot. You're done.

Here are the results of procedure:

-HP-15-TS-Notebook-PC:~$ git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
The program 'git' is currently not installed. You can install it by typing:
sudo apt-get install git


dan@dan-HP-15-TS-Notebook-PC:~$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libdiscid0 libllvm3.5 libllvm3.5:i386 linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-headers-3.16.0-43
  linux-headers-3.16.0-43-generic linux-headers-4.4.0-34
  linux-headers-4.4.0-34-generic linux-headers-4.4.0-59
  linux-headers-4.4.0-59-generic linux-image-3.16.0-30-generic
  linux-image-3.16.0-43-generic linux-image-4.4.0-34-generic
  linux-image-4.4.0-59-generic linux-image-extra-3.16.0-30-generic
  linux-image-extra-3.16.0-43-generic linux-image-extra-4.4.0-34-generic
  linux-image-extra-4.4.0-59-generic linux-signed-image-4.4.0-34-generic
  linux-signed-image-4.4.0-59-generic python-musicbrainz2
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-arch git-bzr git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  git git-man liberror-perl
0 upgraded, 3 newly installed, 0 to remove and 39 not upgraded.
Need to get 3,306 kB of archives.
After this operation, 21.9 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main liberror-perl all 0.17-1.1 [21.1 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main git-man all 1:1.9.1-1ubuntu0.3 [699 kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main git amd64 1:1.9.1-1ubuntu0.3 [2,586 kB]
Fetched 3,306 kB in 11s (286 kB/s)                                             
Selecting previously unselected package liberror-perl.
(Reading database ... 1291579 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17-1.1_all.deb ...
Unpacking liberror-perl (0.17-1.1) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a1.9.1-1ubuntu0.3_all.deb ...
Unpacking git-man (1:1.9.1-1ubuntu0.3) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a1.9.1-1ubuntu0.3_amd64.deb ...
Unpacking git (1:1.9.1-1ubuntu0.3) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up liberror-perl (0.17-1.1) ...
Setting up git-man (1:1.9.1-1ubuntu0.3) ...
Setting up git (1:1.9.1-1ubuntu0.3) ...
dan@dan-HP-15-TS-Notebook-PC:~$ git clone [https://github.com/pvaret/rtl8192cu-fixes.git](https://github.com/pvaret/rtl8192cu-fixes.git)
Cloning into 'rtl8192cu-fixes'...
remote: Counting objects: 465, done.
remote: Total 465 (delta 0), reused 0 (delta 0), pack-reused 465
Receiving objects: 100% (465/465), 1.81 MiB | 343.00 KiB/s, done.
Resolving deltas: 100% (240/240), done.
Checking connectivity... done.
dan@dan-HP-15-TS-Notebook-PC:~$ sudo dkms add ./rtl8192cu-fixes

Creating symlink /var/lib/dkms/8192cu/1.10/source ->
                 /usr/src/8192cu-1.10

DKMS: add completed.
dan@dan-HP-15-TS-Notebook-PC:~$ sudo dkms install 8192cu/1.10

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
make KERNELRELEASE=4.4.0-63-generic -C /lib/modules/4.4.0-63-generic/build M=/var/lib/dkms/8192cu/1.10/build........................
cleaning build area....

DKMS: build completed.

8192cu.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-63-generic/updates/dkms/

depmod.............

Backing up initrd.img-4.4.0-63-generic to /boot/initrd.img-4.4.0-63-generic.old-dkms
Making new initrd.img-4.4.0-63-generic
(If next boot fails, revert to initrd.img-4.4.0-63-generic.old-dkms image)
update-initramfs...............

DKMS: install completed.
dan@dan-HP-15-TS-Notebook-PC:~$ sudo depmod -a
dan@dan-HP-15-TS-Notebook-PC:~$ sudo cp ./rtl8192cu-fixes/blacklist-native-rtl8192.conf /etc/modprobe.d/
dan@dan-HP-15-TS-Notebook-PC:~$ 

After reboot, PC runs ok, but LOST the build it WIFI card, keyboard says it is off, cannot connect it, I assume somehow that driver was lost?

from what I can tell it was a rtl8188ee.

Any help would be appreciated

Thanks Dan

---

