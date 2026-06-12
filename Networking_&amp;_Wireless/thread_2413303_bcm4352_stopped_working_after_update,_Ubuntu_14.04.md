---
title: "bcm4352 stopped working after update, Ubuntu 14.04 lts"
date: 2019-02-24
forum: Networking &amp; Wireless
---

### Post by krfoley on 2019-02-24
I have a Dell XPS 13 (9343) which came installed with Ubuntu 14.04 lts. The bcm4352 worked out of the box and has worked fine for a couple of years. After doing a normal update a week ago, the wifi stopped working. Nothing that i have tried has made any difference. 

I have tried removing and  re-installing the drivers, bcmwl-kernel-source, but I keep getting the error "modprobe: ERROR: could not insert 'wl': Package not installed"

I also tried booting from an earlier kernel and then installing the bcmwl-kernel-source. That didn't help either.

> 
root@kr-XPS-13-9343:~/kr/wireless# apt-get install --reinstall bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  firefox-locale-en
Use 'apt-get autoremove' to remove it.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,511 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 2070125 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu0.2_amd64.deb ...
Removing all DKMS Modules
Done.
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) over (6.30.223.248+bdcom-0ubuntu0.2) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu0.2) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
Building only for 3.16.0-77-generic
Building for architecture x86_64
Building initial module for 3.16.0-77-generic
Secure Boot not enabled on this system.
Done.

wl:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.16.0-77-generic/updates/dkms/

depmod....

DKMS: install completed.
modprobe: ERROR: could not insert 'wl': Package not installed
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.11) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-77-generic


I ran the the wireless-info script and posted the output here: [http://paste.ubuntu.com/p/MggDHt9xVj/](http://paste.ubuntu.com/p/MggDHt9xVj/)

Any help is greatly appreciated. If I can provide any additional info, please let me know.

---

### Post by r10kindsofpeople on 2019-02-25
Just adding a "me too".  System is an Asus G750J, Ubuntu 14.04LTS, Broadcom 4352, lshw -C network says "*-network UNCLAIMED" and attempts to reinstall linux-headers-generic and then bcmwl-kernel-source result in the same error messages about wl package not installed.  

Seems to have stopped working sometime before 2/23.  

Linux 3.13.0-165-generic #215-Ubuntu SMP Wed Jan 16 11:46:47 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

Booting a 'live usb' 18.04 stick and installing bcmwl-kernel-source works, so it's not a hardware problem.

---

### Post by idprism on 2019-02-28
Same problem -network UNCLAIMED despite a purge and reinstall of bwmwl-kernel-source. Fails on both 3.13.0-165-generic and 3.13.0-164-generic (which previously worked just fine).

modprobe: ERROR: could not insert 'wl': package not installed
update-initramfs: deferring update (trigger activated)

same problem with bwmwl-kernel-source versions 6.30.223.141+bdcom-0ubuntu2 and 6.30.223.248+bdcom-0ubuntu0.2 in both kernels.

Something else happened during the last update that did not throw a warning...

---

### Post by pompeosbanfigni on 2019-03-01
Adding me too to same problem after the update. 4 years working finely now everything stopped. I have bcm43142 with the same kernels of the guys above. lshw says the same. wl package not installed and so on. tried uninstall --reinstall , modprobe and whatever but nothing changes. any ideas? thank you guys

---

### Post by idprism on 2019-03-01
[https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1818134](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/1818134) bug report.

---

### Post by krfoley on 2019-03-03
There is a temporary solution for this issue provided by Lurchman in the bug report linked above.

---

### Post by pompeosbanfigni on 2019-03-04
thank you man, I followed the procedure and works finely. many  many thanks

---

