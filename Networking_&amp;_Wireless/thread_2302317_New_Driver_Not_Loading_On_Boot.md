---
title: "New Driver Not Loading On Boot"
date: 2015-11-09
forum: Networking &amp; Wireless
---

### Post by mike265 on 2015-11-09
I am running  Ubuntu Server 12.0.4.4 LTS with an Intel NIC driver version 3.13.10-k. I am able upgrade the driver successfully to 4.1.5, however when I reboot, the system reverts back to the originally driver. Any suggestions? Thanks!

---

### Post by chili555 on 2015-11-09
Was part of the procedure 'sudo make install'? Have you in the meantime, gotten an updated linux-image, for example, from 3.2.0-23 to 3.2.0-24 or some such?

If so, you need to recompile:```
cd ~/e1000e-4.1.5
make clean
make
sudo make install
sudo modprobe -r e1000e && sudo modprobe e1000e
```This must be repeated whenever an updated linux-image is installed.

---

### Post by mike265 on 2015-11-09
I have not tried an updated linux-image. Maybe I'll give that a go tomorrow. I did the exact codes you entered, and the new driver loads, but once I reboot it reverts back.

---

### Post by chili555 on 2015-11-09
Are you saying that in all the time since you installed 12.04, you've never updated the kernel version?

When you did the make and sudo make install steps, was it apparent that the module is built against your exact running kernel version?```
uname -r
```May we also see:```
sudo dpkg -s linux-image-generic | grep Status
```

---

### Post by mike265 on 2015-11-09
Ha! The server is actually a fresh install so the kernel has not been updated. It's for a developer who believes in never upgrading.

```
uname -r
```

3.11.0-15-generic

and 

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg -s linux-image-generic | grep Status[/FONT][/COLOR]
```

returned this

Package `linux-image-generic' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

---

### Post by chili555 on 2015-11-10
Please try installing it:```
sudo apt-get install linux-image-generic
```Recompile the (I assume) e1000e package and then reboot. 

Any improvement?

---

### Post by mike265 on 2015-11-10
OK so I ran

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install linux-image-generic[/FONT][/COLOR]
```
returns this

Status: install ok installed

I also ran
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg -s linux-headers-`uname -r`[/FONT][/COLOR]
```[COLOR=#000000][FONT=Ubuntu Mono]
which returns this
[/FONT][/COLOR]
Package: linux-headers-3.11.0-15-generic
Status: install ok installed
Priority: optional
Section: devel
Installed-Size: 12556
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Source: linux-lts-saucy
Version: 3.11.0-15.25~precise1
Depends: linux-headers-3.11.0-15, libc6 (>= 2.14)
Description: Linux kernel headers for version 3.11.0 on 64 bit x86 SMP
 This package provides kernel header files for version 3.11.0 on
 64 bit x86 SMP.

then I did 

```
[COLOR=#000000][FONT=Ubuntu Mono]cd ~/[/FONT][/COLOR]ixgbe-4.1.5/src 
[COLOR=#000000][FONT=Ubuntu Mono]make clean 
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]make
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo make install 
[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r ixgbe && sudo modprobe ixgbe[/FONT][/COLOR]
```

Which installs the driver fine, but same thing happens on reboot. It goes back to driver version 3.13.10-k

[COLOR=#000000][FONT=Ubuntu Mono]
[/FONT][/COLOR]

---

### Post by chili555 on 2015-11-10
Does your 'sudo make install' look like this, excluding the kernel version?> make -C /lib/modules/4.2.0-17-generic/build SUBDIRS=/home/chili/Downloads/ixgbe-4.1.5/src modules
make[1]: Entering directory '/usr/src/linux-headers-4.2.0-17-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory '/usr/src/linux-headers-4.2.0-17-generic'
gzip -c ../ixgbe.7 > ixgbe.7.gz
[COLOR="#FF0000"]# remove all old versions of the driver[/COLOR]
find /lib/modules/4.2.0-17-generic -name ixgbe.ko -exec rm -f {} \; || true
find /lib/modules/4.2.0-17-generic -name ixgbe.ko.gz -exec rm -f {} \; || true
install -D -m 644 ixgbe.ko /lib/modules/4.2.0-17-generic/kernel/drivers/net/ethernet/intel/ixgbe/ixgbe.ko
/sbin/depmod -a 4.2.0-17-generic || true
install -D -m 644 ixgbe.7.gz /usr/share/man/man7/ixgbe.7.gz
Where did you get the driver? May I see a link?

---

### Post by mike265 on 2015-11-10
Here is the output of 
```
sudo make install
```

make -C /lib/modules/3.11.0-15-generic/build SUBDIRS=/home/mike/ixgbe-4.1.5/src modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-15-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-15-generic'
gzip -c ../ixgbe.7 > ixgbe.7.gz
# remove all old versions of the driver
find /lib/modules/3.11.0-15-generic -name ixgbe.ko -exec rm -f {} \; || true
find /lib/modules/3.11.0-15-generic -name ixgbe.ko.gz -exec rm -f {} \; || true
install -D -m 644 ixgbe.ko /lib/modules/3.11.0-15-generic/kernel/drivers/net/ethernet/intel/ixgbe/ixgbe.ko
/sbin/depmod -a 3.11.0-15-generic || true
install -D -m 644 ixgbe.7.gz /usr/share/man/man7/ixgbe.7.gz


and here is the link to the driver

[https://downloadcenter.intel.com/download/14687/Network-Adapter-Driver-for-PCI-E-10-Gigabit-Network-Connections-under-Linux-](https://downloadcenter.intel.com/download/14687/Network-Adapter-Driver-for-PCI-E-10-Gigabit-Network-Connections-under-Linux-)

---

### Post by chili555 on 2015-11-10
I think I got it!!!

I downloaded the file from the link you gave and read the README. This package has an unusual installation procedure:> 4. Compile the driver module:
   # make install

   The binary will be installed as:
   /lib/modules/<KERNEL VERSION>/kernel/drivers/net/ixgbe/ixgbe.[k]o

   The install location listed above is the default location. This may differ
   for various Linux distributions.In other words, it skips the usual preliminary 'make.' I tried it thus:```
cd ~/Downloads/ixgbe-4.1.5/src
make clean
sudo make install
```I checked the version:```
modinfo ixgbe
<snip>
version:        4.1.5

```After a reboot, it is the same!

Please try it.

---

### Post by mike265 on 2015-11-10
Should I still run 

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r ixgbe && sudo modprobe ixgbe[/FONT][/COLOR]
```

after

```
sudo make install
```

---

### Post by mike265 on 2015-11-10
Should I still run 

```
[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -r ixgbe && sudo modprobe ixgbe[/FONT][/COLOR]
```

after

```
sudo make install
```

---

### Post by mike265 on 2015-11-10
OK that did it!! You are awesome!! Thank you once again for all your help. I truly appreciate it. I wish I could buy you a beer.

---

### Post by chili555 on 2015-11-10
Glad it's working!

---

