---
title: "Wifi not running on  HP 15-bs051od laptop with RealTek wifi controller"
date: 2018-04-29
forum: Networking &amp; Wireless
---

### Post by Randy M on 2018-04-29
I just loaded 16.04 alongside Windows 10. Wifi works fine in Windows, but the driver for Linux doesn't seem to exist. I checked Additional Drivers, but nothing's listed. Another thread recommended creation of the wireless-info.txt document, but I'm more of a user than a deep dive tech. I'm attaching the document in case anyone has any recommendations on how to get the driver to load. As always, thanks for any and all help.

[ATTACH=CONFIG]279491[/ATTACH]

---

### Post by jeremy31 on 2018-04-29
This should work
```
sudo apt-get install build-essential git dkms
git clone https://github.com/jeremyb31/rtl8723de.git
sudo dkms add ./rtl8723de
sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414
```
Reboot

---

### Post by Randy M on 2018-04-29
Thanks, but that didn't seem to make any difference. There are still no wifi connections showing. Here's a capture of the install.

```
randy@randy-HP-Laptop-15-bs0xx:~$ sudo apt-get install build-essential git dkms
[sudo] password for randy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version (12.1ubuntu2).
The following additional packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-arch git-cvs git-mediawiki git-svn
The following NEW packages will be installed:
  dkms git git-man liberror-perl
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 3,924 kB of archives.
After this operation, 25.8 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 dkms all 2.2.0.3-2ubuntu11.5 [66.3 kB]
Get:2 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial/main amd64 liberror-perl all 0.17-1.2 [19.6 kB]
Get:3 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 git-man all 1:2.7.4-0ubuntu1.3 [736 kB]
Get:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates/main amd64 git amd64 1:2.7.4-0ubuntu1.3 [3,102 kB]
Fetched 3,924 kB in 1s (2,428 kB/s)
Selecting previously unselected package dkms.
(Reading database ... 212792 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-2ubuntu11.5_all.deb ...
Unpacking dkms (2.2.0.3-2ubuntu11.5) ...
Selecting previously unselected package liberror-perl.
Preparing to unpack .../liberror-perl_0.17-1.2_all.deb ...
Unpacking liberror-perl (0.17-1.2) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a2.7.4-0ubuntu1.3_all.deb ...
Unpacking git-man (1:2.7.4-0ubuntu1.3) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a2.7.4-0ubuntu1.3_amd64.deb ...
Unpacking git (1:2.7.4-0ubuntu1.3) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up dkms (2.2.0.3-2ubuntu11.5) ...
Setting up liberror-perl (0.17-1.2) ...
Setting up git-man (1:2.7.4-0ubuntu1.3) ...
Setting up git (1:2.7.4-0ubuntu1.3) ...
randy@randy-HP-Laptop-15-bs0xx:~$ git clone [https://github.com/jeremyb31/rtl8723de.git](https://github.com/jeremyb31/rtl8723de.git)
Cloning into 'rtl8723de'...
remote: Counting objects: 536, done.
remote: Total 536 (delta 0), reused 0 (delta 0), pack-reused 536
Receiving objects: 100% (536/536), 2.41 MiB | 0 bytes/s, done.
Resolving deltas: 100% (195/195), done.
Checking connectivity... done.
randy@randy-HP-Laptop-15-bs0xx:~$ sudo dkms add ./rtl8723de

Creating symlink /var/lib/dkms/rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414/source ->
                 /usr/src/rtl8723de-5.1.1.8_21285.20171026_COEX20170111-1414

DKMS: add completed.
randy@randy-HP-Laptop-15-bs0xx:~$ sudo dkms install rtl8723de/5.1.1.8_21285.20171026_COEX20170111-1414

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' all KVER=4.13.0-39-generic.........................
cleaning build area....

DKMS: build completed.

rtl8723de.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.13.0-39-generic/updates/dkms/

depmod............

DKMS: install completed.
randy@randy-HP-Laptop-15-bs0xx:~$
```

---

### Post by jeremy31 on 2018-04-29
Check ```
mokutil --sb-state
```
If it says secure boot enabled, it needs to be disabled in UEFI/BIOS settings

---

### Post by Randy M on 2018-04-29
Turning off secure boot eliminated Grub, now it'll only boot up in Windows.

---

### Post by jeremy31 on 2018-04-29
I have never heard that before, Do you have a live ISO to boot into to check ```
sudo efibootmgr
```
Maybe something got switched around in UEFI

---

### Post by Randy M on 2018-04-29
Pressing the ESC key repeatedly brings up the boot device menu and Ubuntu is one of the options. Will SUDO EFIBOOTMGR work if I boot from the hard drive, or should I only use it when booted from the DVD?

---

### Post by Randy M on 2018-04-29
As a side note, Wifi is working now.

---

### Post by jeremy31 on 2018-04-29
efibootmgr will work from the install

---

### Post by Randy M on 2018-04-29
Ok, I didn't want to screw things up even more.

```
randy@randy-HP-Laptop-15-bs0xx:~$ sudo efibootmgr
[sudo] password for randy: 
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0001,3001,0002,2001,2002,2004
Boot0000* Internal CD/DVD ROM Drive (UEFI) (hp       DVDRW GUE1N)
Boot0001* Windows Boot Manager
Boot0002* ubuntu
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot3001* Internal Hard Disk or Solid State Disk
randy@randy-HP-Laptop-15-bs0xx:~$ 
```

---

### Post by jeremy31 on 2018-04-29
Did you happen to boot into Windows before loosing Grub menu?

---

### Post by Randy M on 2018-04-29
I got it working! I did a search on EFIBOOTMGR and found out how to change the boot order and timeout. It now boots correctly.
 
My special thanks for your help and patience. I'll tag this as Solved.

---

### Post by jeremy31 on 2018-04-29
Can you post the efibootmgr command you used in case someone else finds this through a search?

---

### Post by Randy M on 2018-04-29
I didn't boot into Windows intentionally after losing Grub, it went to Windows on its own and gave no option for anything else.

---

### Post by Randy M on 2018-04-29
> **jeremy31 said:**
> Can you post the efibootmgr command you used in case someone else finds this through a search?


The exact command propably wouldn't help since the numbers associated with each boot device change, but a link to the explanation of efibootmgr might. 

[https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027](https://www.lifewire.com/change-the-efi-boot-order-efibootmgr-4028027)

---

