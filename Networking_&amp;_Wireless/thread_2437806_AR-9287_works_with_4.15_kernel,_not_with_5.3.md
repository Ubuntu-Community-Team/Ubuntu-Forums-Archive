---
title: "AR-9287 works with 4.15 kernel, not with 5.3"
date: 2020-02-29
forum: Networking &amp; Wireless
---

### Post by jwbrase on 2020-02-29
My home desktop, running Ubuntu-Mate 18.04 has a PCI AR9287 Wireless card, which has until recently been using a linux-image-4.15.0-91-generic. The machine has had 14.04 and 16.04 installed over its history without connectivity problems. I recently tried installing linux-image-5.3.0-40-generic, but with that kernel booted the card does not show up in ifconfig, and I have no wireless connectivity. I have tried installing firmware-ath9k-htc, to no avail. When I revert to booting the 4.15 kernel, connectivity is restored. Does anyone know what needs to be done to get the card working with a 5.3 kernel?

Wireless info script output from the 4.15 and 5.3 kernels is attached.

[ATTACH]285112[/ATTACH]
[ATTACH]285113[/ATTACH]

---

### Post by chili555 on 2020-02-29
> 
I recently tried installing linux-image-5.3.0-40-generic
How, exactly? 

Did you also install linux-modules, linux-headers and linux-image-generic?

---

### Post by jwbrase on 2020-03-01
Yes:

The exact package name linux-image-generic depends on the working 4.15 kernel that I started with.

For the 5.3 package, linux-image-5.3.0-40-generic, I have the corresponding linux-headers and linux-modules packages.

---

### Post by chili555 on 2020-03-01
What is the exact response to the terminal command:```
sudo modprobe ath9k && dmesg | grep ath
```

---

### Post by jwbrase on 2020-03-01
dmesg | grep ath returns nothing, either before or after the modprobe.

The modprobe itself emits the following on stderr:

```
modprobe: FATAL: Module ath9k not found in directory /lib/modules/5.3.0-40-generic
```

I have double checked that linux-modules-5.3.0... is installed, and that the /lib/modules/5.3.0-40-generic directory exists and is populated with other modules.

```
dpkg-query -L linux-modules-5.3.0-40-generic | grep ath
```

returns the following (included for completeness, no results relevant to ath9k):

```
/lib/modules/5.3.0-40-generic/kernel/drivers/md/dm-multipath.ko
/lib/modules/5.3.0-40-generic/kernel/drivers/md/multipath.ko
/lib/modules/5.3.0-40-generic/kernel/lib/math
/lib/modules/5.3.0-40-generic/kernel/lib/math/cordic.ko
```


```
dpkg-query -L firmware-ath9k-htc
```

returns:


```
/.
/etc
/etc/modprobe.d
/etc/modprobe.d/ath9k_htc.conf
/lib
/lib/firmware
/lib/firmware/ath9k_htc
/lib/firmware/ath9k_htc/htc_7010-1.dev.0.fw
/lib/firmware/ath9k_htc/htc_9271-1.dev.0.fw
/usr
/usr/share
/usr/share/doc
/usr/share/doc/firmware-ath9k-htc
/usr/share/doc/firmware-ath9k-htc/changelog.Debian.gz
/usr/share/doc/firmware-ath9k-htc/copyright
/usr/share/metainfo
/usr/share/metainfo/firmware-ath9k-htc.metainfo.xml
```

```
aptitude show linux-modules-5.3.0-40-generic firmware-ath9k-htc
```

returns:

```
Package: linux-modules-5.3.0-40-generic
Version: 5.3.0-40.32~18.04.1
New: yes
State: installed
Automatically installed: yes
Priority: optional
Section: kernel
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Architecture: amd64
Uncompressed Size: 69.4 M
Conflicts: linux-modules-5.3.0-40-generic:i386
Description: Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
 Contains the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in an unbootable state after an update. 
 
 Supports Generic processors. 
 
 Geared toward desktop and server systems. 
 
 You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed.


Package: firmware-ath9k-htc
Version: 1.4.0-97-g75b3e59+dfsg-1
New: yes
State: installed
Automatically installed: no
Multi-Arch: foreign
Priority: extra
Section: universe/misc
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Uncompressed Size: 164 k
Description: QCA ath9k-htc Firmware
 Opensource version of QCA ath9k-htc Firmware. Supported chips are: ar9271 and ar7010
Homepage: https://github.com/qca/open-ath9k-htc-firmware


```

---

### Post by jeremy31 on 2020-03-01
Try ```
sudo apt install --reinstall linux-modules-extra-5.3.0-40-generic
```
Reboot

---

### Post by jwbrase on 2020-03-01
That does seem to be what was missing. I now have connectivity on the 5.3 kernel.

Looking into it further, I figured out what went wrong: The linux-generic-hwe-$UBUNTU_VERSION packages bring in the more recent kernels, but don't sort together with the linux-generic package, so  it wasn't immediately obvious that the hwe was just a designator for more recent kernel versions: I assumed hwe-generic was compiled with a different configuration than just generic. However, the packages they bring in aren't marked with hwe, so the linux-image-5.3...-generic package looked to be the most basal package I could find for a plain 5.3 kernel. That pulled in modules, and I pulled in headers myself, but it didn't pull in modules-extra, and I didn't notice.

I figured out that the linux-generic-hwe packages were just the more recent kernels for generic when I looked through the available linux-* packages with zsh tab completion, and saw the whole linux-generic* list together.

---

