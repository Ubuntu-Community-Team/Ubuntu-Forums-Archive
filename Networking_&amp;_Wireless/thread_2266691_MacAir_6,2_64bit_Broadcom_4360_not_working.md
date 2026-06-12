---
title: "MacAir 6,2 64bit Broadcom 4360 not working"
date: 2015-02-24
forum: Networking &amp; Wireless
---

### Post by Mathias_Fossum on 2015-02-24
Macbook Air mid 2013 6,2 Ubuntu 14.04 fresh install.

Output from ```
lspci -nn -d 14e4:
```

02:00.0 Multimedia controller [0480]: Broadcom Corporation Device [14e4:1570]
03:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)

Followed this guide (sticky in this forum topic): [http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110) 

when I do this step:```
sudo apt-get install bcmwl-kernel-source
```
 it seems like it fails

OUTPUT:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1 126 kB of archives.
After this operation, 5 800 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 193265 files and directories currently installed.)
Preparing to unpack .../bcmwl-kernel-source_6.30.223.141+bdcom-0ubuntu2_amd64.deb ...
Unpacking bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Setting up bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Loading new bcmwl-6.30.223.141+bdcom DKMS files...
Building only for 3.16.0-31-generic
Building for architecture x86_64
Building initial module for 3.16.0-31-generic
Error! Bad return status for module build on kernel: 3.16.0-31-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.30.223.141+bdcom/build/make.log for more information.
modprobe: FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.16.0-31-generic

Ubuntu prompts me with a system program problem with bcmwl-kernel-source as the reason.

I did exactely like the guide.
*reboot* = no magic

the broadcom driver is listed under "Additional Drivers" in Software & drivers. and ticked.

What could be the problem here? Please direct me to a guide, if possible, as I hate when I create new threads about well-answered problems.

I have the dkms dependency as i've read that it is required by bcmwl-kernel-source, also tried firmwareb43 something like that.

---

### Post by jeremy31 on 2015-02-24
You actually need to download from [http://packages.ubuntu.com/utopic/amd64/bcmwl-kernel-source/download](http://packages.ubuntu.com/utopic/amd64/bcmwl-kernel-source/download) select a mirror site and double click on the downloaded file to install.  For some reason Ubuntu has not put this file in the trusty repos even after the 3.16 kernels are installed that need the patch for Utopic

---

### Post by Mathias_Fossum on 2015-02-25
I have done that already with sudo dpkg -i "kernel.deb". Still no luck

---

### Post by jeremy31 on 2015-02-25
```
[COLOR=#000000]Unpacking bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
``` is the wrong version for kernel 3.16, you need version 6.30.223.248

```
[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 [/FONT][/COLOR]http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb
```
```
sudo dpkg -i bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb
```

---

### Post by Mathias_Fossum on 2015-02-25
> **jeremy31 said:**
> ```
[COLOR=#000000]Unpacking bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...[/COLOR]
```[COLOR=#000000] is the wrong version for kernel 3.16, you need version 6.30.223.248

[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]wget -N -t 5 -T 10 [/FONT][/COLOR]http://mirrors.kernel.org/ubuntu/pool/restricted/b/bcmwl/bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb
```
```
sudo dpkg -i bcmwl-kernel-source_6.30.223.248+bdcom-0ubuntu1_amd64.deb
```

I must have got the wrong .deb from the start on. Thank you very much! The wifi is now working.

---

### Post by Naimisharanya on 2015-02-25
You rescued me from a very bad day at the office!

For reference, new HP Probook and I couldn't get the wireless to work ALL DAY. As 5pm strikes I find the answer. Thanks.

---

### Post by jeremy31 on 2015-02-25
Could you edit the topic to include 14.04, kernel 3.16 as it might help

---

