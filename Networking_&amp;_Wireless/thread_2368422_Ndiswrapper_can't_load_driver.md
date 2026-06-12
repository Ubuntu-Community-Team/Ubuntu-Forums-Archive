---
title: "Ndiswrapper can't load driver"
date: 2017-08-10
forum: Networking &amp; Wireless
---

### Post by jet-bundle on 2017-08-10
I have an HP Paviliion TS11 running Lubuntu 16.04, and I've related elsewhere ([https://ubuntuforums.org/showthread.php?t=2365838](https://ubuntuforums.org/showthread.php?t=2365838)) the problems I've had in getting the built-in wireless card to work. To try to get round this I bought a USB dongle, but the supplied Linux driver wouldn't compile (see [https://ubuntuforums.org/showthread.php?t=2366768](https://ubuntuforums.org/showthread.php?t=2366768)) so I decide to try ndiswrapper. I installed it from the Lubuntu Software Centre, and installed the 64-bit Windows XP driver supplied with the dongle, apparently successfully. But I still can't detect any wireless networks, and I note the following:```
$ dmesg | grep ndis
[   18.736534] ndiswrapper version 1.60 loaded (smp=yes, preempt=no)
[   19.386667] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'IoCsqInsertIrp'
[   19.386685] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'IoCsqRemoveNextIrp'
[   19.386695] ndiswrapper (import:232): unknown symbol: ntoskrnl.exe:'IoCsqInitialize'
[   19.386866] ndiswrapper (load_sys_files:200): couldn't prepare driver 'netrtwlanu_xp'
[   19.388008] ndiswrapper (load_wrap_driver:103): couldn't load driver netrtwlanu_xp; check system log for messages from 'loadndisdriver'
[   19.388098] usbcore: registered new interface driver ndiswrapper
```
Any advice would be gratefully received. Here is wireless-info.txt: [https://pastebin.com/9Qw8BYBK](https://pastebin.com/9Qw8BYBK)

---

### Post by jeremy31 on 2017-08-10
Get rid of ndiswrapper ```
sudo apt-get purge ndiswrapper && sudo rm /etc/modprobe.d/ndiswrapper.conf
```
Then see if we can compile some source on github
```
sudo apt-get install git dkms
git clone https://github.com/abperiasamy/rtl8812AU_8821AU_linux.git
cd rtl8812AU_8821AU_linux
sudo make -f Makefile.dkms install
```
If there are no errors after these commands reboot and see if wifi works

EDIT: actually try chili555's idea below first

---

### Post by chili555 on 2017-08-10
I'm confused.

The USB device in your wireless script is not an 8192cu device. The driver you apparently tried to compiled in the link was, however.

You also have a PCI device with a driver that needs to be blacklisted if you want to use the USB.

Your USB is this:> Bus 001 Device 002: ID 0bda:a811 Realtek Semiconductor Corp.The correct driver is 8812au. Here are instructions: [https://askubuntu.com/questions/932092/wireless-antenna-does-not-appear-despite-its-driver-being-installed/932286#932286](https://askubuntu.com/questions/932092/wireless-antenna-does-not-appear-despite-its-driver-being-installed/932286#932286) Please see Edit 2.

You should also remove ndiswrapper:```
sudo apt-get purge ndiswrapper*
```

---

### Post by jet-bundle on 2017-08-11
Thank you both. I am pleased to report success.

First I installed this morning's kernel upgrade, so I'm now running 4.4.0-91-generic. I then removed ndiswrapper. After that, I followed the instructions in the link [https://askubuntu.com/questions/9320.../932286#932286]("https://askubuntu.com/questions/932092/wireless-antenna-does-not-appear-despite-its-driver-being-installed/932286#932286"), with the following result. ```
$ sudo apt-get install git
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  git-man liberror-perl
Suggested packages:
  git-daemon-run | git-daemon-sysvinit git-doc git-el git-email git-gui gitk
  gitweb git-arch git-cvs git-mediawiki git-svn
The following NEW packages will be installed
  git git-man liberror-perl
0 to upgrade, 3 to newly install, 0 to remove and 3 not to upgrade.
Need to get 3,918 kB of archives.
After this operation, 25.6 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu xenial/main amd64 liberror-perl all 0.17-1.2 [19.6 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 git-man all 1:2.7.4-0ubuntu1.2 [736 kB]
Get:3 http://gb.archive.ubuntu.com/ubuntu xenial-updates/main amd64 git amd64 1:2.7.4-0ubuntu1.2 [3,163 kB]
Fetched 3,918 kB in 1s (3,677 kB/s)
Selecting previously unselected package liberror-perl.
(Reading database ... 153528 files and directories currently installed.)
Preparing to unpack .../liberror-perl_0.17-1.2_all.deb ...
Unpacking liberror-perl (0.17-1.2) ...
Selecting previously unselected package git-man.
Preparing to unpack .../git-man_1%3a2.7.4-0ubuntu1.2_all.deb ...
Unpacking git-man (1:2.7.4-0ubuntu1.2) ...
Selecting previously unselected package git.
Preparing to unpack .../git_1%3a2.7.4-0ubuntu1.2_amd64.deb ...
Unpacking git (1:2.7.4-0ubuntu1.2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up liberror-perl (0.17-1.2) ...
Setting up git-man (1:2.7.4-0ubuntu1.2) ...
Setting up git (1:2.7.4-0ubuntu1.2) ...

$ git clone https://github.com/jeremyb31/rtl8812AU.git
Cloning into 'rtl8812AU'...
remote: Counting objects: 2158, done.
remote: Total 2158 (delta 0), reused 0 (delta 0), pack-reused 2158
Receiving objects: 100% (2158/2158), 7.67 MiB | 3.32 MiB/s, done.
Resolving deltas: 100% (1131/1131), done.
Checking connectivity... done.

$ sudo dkms add ./rtl8812AU

Creating symlink /var/lib/dkms/rtl8812AU/5/source ->
                 /usr/src/rtl8812AU-5

DKMS: add completed.
$ sudo dkms install rtl8812AU/5

Kernel preparation unnecessary for this kernel.  Skipping...

Building module:
cleaning build area....
'make' all KVER=4.4.0-91-generic..................................................................
cleaning build area....

DKMS: build completed.

8812au.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/4.4.0-91-generic/updates/dkms/

depmod....

DKMS: install completed.

```
I then rebooted, and wireless networks were detected. I was able to connect successfully to my local network.

For reference: I didn't need to blacklist rt3290sta, as this now doesn't appear in lsmod output, perhaps as a result of the kernel upgrade. And finally > I'm confused.

The USB device in your wireless script is not an 8192cu device. The  driver you apparently tried to compiled in the link was, however.
Well, being a simple soul, I assumed that when a dongle and a mini-CD came in the same shrink-wrapped pack, then the latter would contain drivers for the former.

---

### Post by vocx on 2017-08-11
> **jet-bundle said:**
> ... And finally 
Well, being a simple soul, I assumed that when a dongle and a mini-CD came in the same shrink-wrapped pack, then the latter would contain drivers for the former.
Forget about any "Linux driver" that comes in a product CD.

A Windows computer typically detects a new hardware device and installs the appropriate drivers. Same in Linux.

If the drivers are included in a CD at all, they are mostly outdated source code with cryptic instructions for compiling and installing, which don't generally apply to a modern Linux distribution like Ubuntu.

---

