---
title: "No wireless--wifi after upgraded from 17.04 to 17.10"
date: 2017-10-21
forum: Networking &amp; Wireless
---

### Post by hoboy on 2017-10-21
After I have upgrade from 17.04 to 17.10 I am getting this error 
No wifi adapter found .
make sure you have wifi adapter plugged and turned on.
Before the upgrade I was only using wireless.


 iwconfig
docker0   no wireless extensions.

lxcbr0    no wireless extensions.

enp2s0    no wireless extensions.

virbr0    no wireless extensions.

virbr0-nic  no wireless extensions.

lo        no wireless extensions.


LSB Version:	core-9.20160110ubuntu5-amd64:core-9.20160110ubuntu5-noarch:security-9.20160110ubuntu5-amd64:security-9.20160110ubuntu5-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 17.10
Release:	17.10
Codename:	artful

tks

---

### Post by jeremy31 on 2017-10-21
See the wireless script link in my signature and post results.

---

### Post by hoboy on 2017-10-21
sudo apt install pastebinit
[sudo] password for xxxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  pastebinit
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 14.6 kB of archives.
After this operation, 160 kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) artful/main amd64 pastebinit all 1.5-1 [14.6 kB]
Fetched 14.6 kB in 0s (94.4 kB/s)     
Selecting previously unselected package pastebinit.
(Reading database ... 587781 files and directories currently installed.)
Preparing to unpack .../pastebinit_1.5-1_all.deb ...
Unpacking pastebinit (1.5-1) ...
Setting up pastebinit (1.5-1) ...
Processing triggers for man-db (2.7.6.1-2) ...

Wireless info text at 
[http://paste.ubuntu.com/25786894/](http://paste.ubuntu.com/25786894/)

---

### Post by jeremy31 on 2017-10-21
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Reboot

---

### Post by hoboy on 2017-10-21
hi 
running sudo apt-get install --reinstall bcmwl-kernel-source
has not helped 
Tks

---

### Post by jeremy31 on 2017-10-21
What does ```
sudo modprobe -v wl; dkms status
```
Tell us?

---

### Post by hoboy on 2017-10-21
modprobe: FATAL: Module wl not found in directory /lib/modules/4.13.0-16-lowlatency
bcmwl, 6.30.223.271+bdcom: added
virtualbox, 5.1.30, 4.10.0-38-generic, x86_64: installed
virtualbox, 5.1.30, 4.13.0-16-generic, x86_64: installed
virtualbox-guest, 5.1.30, 4.10.0-38-generic, x86_64: installed
virtualbox-guest, 5.1.30, 4.13.0-16-generic, x86_64: installed

sudo apt-get install --reinstall bcmwl-kernel-source
[sudo] password for xxxxxxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/1,544 kB of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 587440 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.271+bdcom-0ubuntu3_amd64.deb ...
Removing all DKMS Modules
Done.
Unpacking bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu3) over (6.30.223.271+bdcom-0ubuntu3) ...
Setting up bcmwl-kernel-source (6.30.223.271+bdcom-0ubuntu3) ...
Loading new bcmwl-6.30.223.271+bdcom DKMS files...
Building for 4.13.0-16-lowlatency
Building for architecture x86_64
Module build for kernel 4.13.0-16-lowlatency was skipped since the
kernel headers for this kernel does not seem to be installed.
modprobe: FATAL: Module wl not found in directory /lib/modules/4.13.0-16-lowlatency
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.125ubuntu12) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-16-lowlatency
W: Possible missing firmware /lib/firmware/amdgpu/raven_gpu_info.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_rlc.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_mec2.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_mec.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_me.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_pfp.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_ce.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_sdma.bin for module amdgpu
W: Possible missing firmware /lib/firmware/amdgpu/raven_vcn.bin for module amdgpu

---

### Post by jeremy31 on 2017-10-21
It complains about not having the kernel headers, let's see if we can install them
```
sudo apt-get install linux-headers-4.13.0-16-lowlatency
```
If no errors
```
sudo apt-get install --reinstall bcmwl-kernel-source
```
Reboot

---

### Post by hoboy on 2017-10-21
Tks guys 
the last commands have done the tick
it is working now

---

