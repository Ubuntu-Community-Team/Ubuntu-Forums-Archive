---
title: "Module wl not found in directory /lib/modules/4.4.8-040408-generic"
date: 2016-07-02
forum: Networking &amp; Wireless
---

### Post by hikkamorii on 2016-07-02
Help please, wireless won't work at all... Tried lots of solutions, but nothing's working...

Output after sudo apt-get install bcmwl-kernel-source
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1 515 kB of archives.
After this operation, 8 013 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 365474 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu8_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu8) ...
Setting up bcmwl-kernel-source (6.30.223.248+bdcom-0ubuntu8) ...
Loading new bcmwl-6.30.223.248+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 4.4.8-040408-generic
Building for architecture x86_64
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
modprobe: FATAL: Module wl not found in directory /lib/modules/4.4.8-040408-generic
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.122ubuntu8.1) ...
update-initramfs: Generating /boot/initrd.img-4.4.8-040408-generic

```
and lspci
```
> lspci -vnn -d 14e4:   
13:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company BCM43142 802.11b/g/n [103c:804a]
    Flags: fast devsel, IRQ 255
    Memory at c2000000 (64-bit, non-prefetchable) [size=32K]
    Capabilities: <access denied>
    Kernel modules: bcma

```

---

### Post by praseodym on 2016-07-02
Kernel too new, driver too old:

```
sudo apt-get install linux-headers-$(uname -r) build-essential dkms
wget http://de.archive.ubuntu.com/ubuntu/pool/multiverse/b/broadcom-sta/broadcom-sta-dkms_6.30.223.271-2_all.deb
sudo dpkg -i broadcom-sta-dkms_6.30.223.271-2_all.deb 
```

---

### Post by hikkamorii on 2016-07-02
I tried to do that, but it again do not work...
```
hikkamorii@hp-250-g4:~$ sudo apt-get install linux-headers-$(uname -r) build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-4.4.8-040408-generic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'linux-headers-4.4.8-040408-generic' has no installation candidate

```

I also tried this, but no result...
```
root@hp-250-g4:~# apt-get install linux-headers-4.4.8-040408 build-essential dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'linux-headers-4.4.8-040408-generic' for regex 'linux-headers-4.4.8-040408'
build-essential is already the newest version (12.1ubuntu2).
dkms is already the newest version (2.2.0.3-2ubuntu11).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
Maybe, I can kinda use Wlan on older kernel (booting from grub), however, that means that I won't be able to go in sleep mode (Stupid bug on Haswell machines, it's the only reason why I installed newer version of kernel...)

---

### Post by hikkamorii on 2016-07-02
[B]Update:
[/B]
I actually booted into older kernel version, and after installing drivers and rebooting it actually works, and works pretty good... Magically, there is no more this sleep mode issue, so, I think I can live with that now...

---

