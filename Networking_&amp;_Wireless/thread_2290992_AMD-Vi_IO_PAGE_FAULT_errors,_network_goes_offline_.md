---
title: "AMD-Vi IO_PAGE_FAULT errors, network goes offline until restart"
date: 2015-08-17
forum: Networking &amp; Wireless
---

### Post by caperrigo on 2015-08-17
So I recently upgraded the internals of my Ubuntu Server so that it's running a new motherboard, new processor, etc.  And ever since then, I've been getting errors that look like this:
```
AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain 0x001d address=0x0000000000003000 flags=0x0050]
```
Sometimes they don't appear to do anything, however sometimes after encountering this, the network stops working properly.

I've searched for answers regarding this, however most are either unresolved or involve hardware that isn't relevant here (such as the graphics card causing the fault, and issues starting the desktop environment).  Running ```
sudo lspci -vnn | grep 02:00.0 -A9
``` confirms this and lists info about the ethernet controller:
```
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev. 0c)
        Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:7969]
        Flags: bus master, fast devsel, latency 0, IRQ 87
        I/O ports at e000 [size=256]
        Memory at fe900000 (64-bit, non-prefetchable) [size=4K]
        Memory at d0800000 (64-bit, prefetchable) [size=16K]
        Capabilities: [40] Power Management version 3
        Capabilities: [50] MSI: Enable+ Count=1/1 Maskable- 64bit+
        Capabilities: [70] Express Endpoint, MSI 01
        Capabilities: [b0] MSI-X: Enable- Count=4 Masked-

```

I've also read that there is probably an issue with IOMMU, however I have no way to control whether or not this is turned on in the BIOS (there is no option), and adding ```
iommu=pf
``` or ```
iommu=soft
``` doesn't have any effect on the problem.  Is there anyone that could shed some light on this?  The server is currently unusable, since the problem happens usually within 5 minutes of booting, and only a reboot can fix it.

---

### Post by chili555 on 2015-08-17
Here is a long thread about the subject that suggests the later r8168 driver fixes the issue: [https://github.com/HSAFoundation/HSA-Drivers-Linux-AMD/issues/4](https://github.com/HSAFoundation/HSA-Drivers-Linux-AMD/issues/4)

I suggest you do:```
sudo apt-get install r8168-dkms
```If you have no internet access, you will need to download the r8168-dkms package, linux-headers-`uname -r` and dkms and transfer them on a USB key. You seem knowledgeable and adept, so I've abbreviated the process. If you need better guidance, post back and I'll help.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by caperrigo on 2015-08-17
I was able to install it without the network going down first, so did that, and we'll see where it gets me.  So far so good though.

---

### Post by caperrigo on 2015-08-17
Nope, still getting the same issue as before.  Was there something else that I may have had to do?  (inkling of a feeling that "iommu=pf" as a boot arg may work now?)

Here's the output from installing r8168-dkms, in case it helps

```
no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  dkms
The following NEW packages will be installed:
  dkms r8168-dkms
0 upgraded, 2 newly installed, 0 to remove and 15 not upgraded.
Need to get 159 kB of archives.
After this operation, 1,170 kB of additional disk space will be used.
Do you want to continue? [Y/n]
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main dkms all 2.2.0.3-                                                                      1.1ubuntu5.14.04.1 [64.6 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty/universe r8168-dkms all 8.037.                                                                      00-1 [94.9 kB]
Fetched 159 kB in 0s (219 kB/s)
Selecting previously unselected package dkms.
(Reading database ... 214166 files and directories currently installed.)
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.1_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.1) ...
Selecting previously unselected package r8168-dkms.
Preparing to unpack .../r8168-dkms_8.037.00-1_all.deb ...
Unpacking r8168-dkms (8.037.00-1) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.1) ...
Setting up r8168-dkms (8.037.00-1) ...
Loading new r8168-8.037.00 DKMS files...
First Installation: checking all kernels...
Building only for 3.13.0-35-generic
Building initial module for 3.13.0-35-generic
Done.

r8168:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/3.13.0-35-generic/updates/dkms/

depmod....

Backing up initrd.img-3.13.0-35-generic to /boot/initrd.img-3.13.0-35-generic.ol                                                                      d-dkms
Making new initrd.img-3.13.0-35-generic
(If next boot fails, revert to initrd.img-3.13.0-35-generic.old-dkms image)
update-initramfs....

DKMS: install completed.
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-61-generic
grep: /boot/config-3.13.0-61-generic: No such file or directory
```

---

### Post by chili555 on 2015-08-17
This is troubling:>  - Installation
   - **Installing to /lib/modules/3.13.0-[COLOR="#FF0000"]35[/COLOR]-generic**/updates/dkms/

depmod....

Backing up initrd.img-3.13.0-35-generic to /boot/initrd.img-3.13.0-35-generic.ol                                                                      d-dkms
Making new initrd.img-3.13.0-35-generic
(If next boot fails, revert to initrd.img-3.13.0-35-generic.old-dkms image)
update-initramfs....

DKMS: install completed.
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-61-generic
grep: /boot/config-**3.13.0-[COLOR="#FF0000"]61[/COLOR]-generic: No such file or directory**Which version are you actually running?```
uname -r
```Did you have an update pending where a later kernel version was installed but awaiting reboot?

Which driver is actually running?```
lsmod | grep r816
```If it's r8169, then you need a reboot.

And this is even more troubling!> no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memoryGoogling, and I recommend you do so, too.

---

### Post by caperrigo on 2015-08-17
```
$ uname -r
3.13.0-35-generic
```

```
$ lsmod | grep r816
r8168                 261399  0
r8169                  67581  0
mii                    13934  1 r8169
```

The machine shouldn't have been waiting for a reboot, the server was shut down and rebooted directly before I installed the new driver.  Though I suppose I can go in and clean up some of the older kernel images if I only ever run the latest installed version?

```
[COLOR=#000000]*no talloc stackframe at ../source3/param/loadparm.c:4864, leaking memory*[/COLOR]
```
This has been occurring the first time in a session that I need to put in my password for a sudo command, and I haven't seen any apparent effects.  I'll google it as well though.

EDIT:  [http://ubuntuforums.org/showthread.php?t=2214042](http://ubuntuforums.org/showthread.php?t=2214042)
This thread indicates it's an issue with Samba and how it synchronizes system passwords with itself (I do have Samba, it was turned on, and turning it off has stopped the messages)

---

### Post by chili555 on 2015-08-17
> $ lsmod | grep r816
r8168                 261399  0
r8169                  67581  0
mii                    13934  1 r8169Yikes! *BOTH* are loaded! Let's see if we can fix it:```
sudo -i
echo "blacklist r8169"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r r8169
exit
```Any improvement?

---

### Post by caperrigo on 2015-08-17
```
echo "blacklist r8169"  >>  /etc/modprobe.d/blacklist.conf
```
This wasn't able to execute, and I got a "Permission denied" error, even when appending "sudo" to the beginning of that.  From my understanding though, this statement is to prevent it from loading at boot-time, correct?\

It's very strange though, since I thought root had permission to access EVERYthing.  Thought only Windows pulled this.

```
modprobe -r r8169
```
I figured this would happen, but the network is dead after this.  I'll figure this out when I get home in a few hours (all of this has so far been done through SSH, so now my efforts are in vain until I can return to the server physically).

I'll update as soon as I get home.

---

### Post by caperrigo on 2015-08-17
So that didn't seem to actually do much, the network is still down, and running ifconfig shows that the eth0 adapter is missing.

I was able to add the blacklist line via nano, so that's in.  After rebooting however both of the driver's still appear to be loaded, and killing r8169 manually brings me right back to this network-less state.

---

### Post by chili555 on 2015-08-17
May I see:```
lspci -nn | grep 0200
cat /etc/modprobe.d/r8168-dkms.conf
```Very interesting; and by 'interesting,' I mean weird!

---

### Post by caperrigo on 2015-08-17
```
lspci -nn | grep 0200
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)
```

```
cat /etc/modprobe.d/r8168-dkms.conf
# blacklisted by r8168-dkms
blacklist r8169
```

---

### Post by praseodym on 2015-08-18
Hi,

the package r8168-dkms contains driver version 37 (Ubuntu vivid version 39), meanwhile we have version 40 (since today) available as dkms package, see here

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#r8168-mittels-dkms](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#r8168-mittels-dkms)

---

### Post by chili555 on 2015-08-18
> **praseodym said:**
> Hi,

the package r8168-dkms contains driver version 37 (Ubuntu vivid version 39), meanwhile we have version 40 (since today) available as dkms package, see here

[http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#r8168-mittels-dkms](http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#r8168-mittels-dkms)I certainly agree that you should try it. 

Thank you, praseodym.

---

### Post by caperrigo on 2015-08-18
Tried installing v40 and it seems to have worked alright, rebooted and found that r8169 wasn't loading anymore, so now it looks like things are under control.  I'll keep an eye on it, but it looks like all of the big issues have been resolved.  Thanks a bunch for your help, I feel like I've learned quite a bit from this!

Log just in case it's useful:
```
$ sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkmsReading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  linux-generic linux-headers-3.13.0-62 linux-headers-3.13.0-62-generic
  linux-image-3.13.0-62-generic linux-image-extra-3.13.0-62-generic
  linux-image-generic
Suggested packages:
  fdutils linux-doc-3.13.0 linux-source-3.13.0 linux-tools
The following NEW packages will be installed:
  linux-headers-3.13.0-62 linux-headers-3.13.0-62-generic
  linux-image-3.13.0-62-generic linux-image-extra-3.13.0-62-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 4 newly installed, 3 reinstalled, 0 to remove and 4 not upgraded.
Need to get 61.6 MB/62.4 MB of archives.
After this operation, 271 MB of additional disk space will be used.
Do you want to continue? [Y/n]
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-62-generic amd64 3.13.0-62.102 [15.2 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-3.13.0-62-generic amd64 3.13.0-62.102 [36.8 MB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-generic amd64 3.13.0.62.69 [1,786 B]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-generic amd64 3.13.0.62.69 [2,300 B]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-62 all 3.13.0-62.102 [8,873 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-62-generic amd64 3.13.0-62.102 [707 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic amd64 3.13.0.62.69 [2,278 B]
Fetched 61.6 MB in 29s (2,084 kB/s)
Selecting previously unselected package linux-image-3.13.0-62-generic.
(Reading database ... 214206 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-62-generic_3.13.0-62.102_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-62-generic (3.13.0-62.102) ...
Preparing to unpack .../build-essential_11.6ubuntu6_amd64.deb ...
Unpacking build-essential (11.6ubuntu6) over (11.6ubuntu6) ...
Preparing to unpack .../dkms_2.2.0.3-1.1ubuntu5.14.04.1_all.deb ...
Unpacking dkms (2.2.0.3-1.1ubuntu5.14.04.1) over (2.2.0.3-1.1ubuntu5.14.04.1) ...
Selecting previously unselected package linux-image-extra-3.13.0-62-generic.
Preparing to unpack .../linux-image-extra-3.13.0-62-generic_3.13.0-62.102_amd64.deb ...
Unpacking linux-image-extra-3.13.0-62-generic (3.13.0-62.102) ...
Preparing to unpack .../linux-generic_3.13.0.62.69_amd64.deb ...
Unpacking linux-generic (3.13.0.62.69) over (3.13.0.61.68) ...
Preparing to unpack .../linux-image-generic_3.13.0.62.69_amd64.deb ...
Unpacking linux-image-generic (3.13.0.62.69) over (3.13.0.61.68) ...
Selecting previously unselected package linux-headers-3.13.0-62.
Preparing to unpack .../linux-headers-3.13.0-62_3.13.0-62.102_all.deb ...
Unpacking linux-headers-3.13.0-62 (3.13.0-62.102) ...
Selecting previously unselected package linux-headers-3.13.0-62-generic.
Preparing to unpack .../linux-headers-3.13.0-62-generic_3.13.0-62.102_amd64.deb ...
Unpacking linux-headers-3.13.0-62-generic (3.13.0-62.102) ...
Preparing to unpack .../linux-headers-generic_3.13.0.62.69_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.62.69) over (3.13.0.61.68) ...
Preparing to unpack .../linux-headers-3.13.0-35-generic_3.13.0-35.62_amd64.deb ...
Unpacking linux-headers-3.13.0-35-generic (3.13.0-35.62) over (3.13.0-35.62) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up linux-image-3.13.0-62-generic (3.13.0-62.102) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /vmlinuz is a dangling linkto /boot/vmlinuz-3.13.0-61-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
: Unable to find an initial ram disk that I know how to handle.
Will not try to make an initrd.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Generating grub configuration file ...
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
done
Setting up build-essential (11.6ubuntu6) ...
Setting up dkms (2.2.0.3-1.1ubuntu5.14.04.1) ...
Setting up linux-image-extra-3.13.0-62-generic (3.13.0-62.102) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Generating grub configuration file ...
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-35-generic
Found initrd image: /boot/initrd.img-3.13.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-44-generic
Found initrd image: /boot/initrd.img-3.8.0-44-generic
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
  Couldn't find device with uuid 6xw9mh-z8dw-wheW-TP3R-2a8f-0RZc-n3d9if.
done
Setting up linux-image-generic (3.13.0.62.69) ...
Setting up linux-headers-3.13.0-62 (3.13.0-62.102) ...
Setting up linux-headers-3.13.0-62-generic (3.13.0-62.102) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-62-generic /boot/vmlinuz-3.13.0-62-generic
Setting up linux-headers-generic (3.13.0.62.69) ...
Setting up linux-generic (3.13.0.62.69) ...
Setting up linux-headers-3.13.0-35-generic (3.13.0-35.62) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-35-generic /boot/vmlinuz-3.13.0-35-generic


$ wget https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz
--2015-08-18 13:54:23--  https://media-cdn.ubuntu-de.org/forum/attachments/28/33/3005217-r8168-dkms-8.040.00.tar.gz
Resolving media-cdn.ubuntu-de.org (media-cdn.ubuntu-de.org)... 2001:780:0:25:dead:beef:cafe:1, 213.95.41.4
Connecting to media-cdn.ubuntu-de.org (media-cdn.ubuntu-de.org)|2001:780:0:25:dead:beef:cafe:1|:443... failed: Connection timed out.
Connecting to media-cdn.ubuntu-de.org (media-cdn.ubuntu-de.org)|213.95.41.4|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 122335 (119K) [application/octet-stream]
Saving to: &#8216;3005217-r8168-dkms-8.040.00.tar.gz&#8217;


100%[=====================================================================================================================================>] 122,335      313KB/s   in 0.4s


2015-08-18 13:56:32 (313 KB/s) - &#8216;3005217-r8168-dkms-8.040.00.tar.gz&#8217; saved [122335/122335]


$ sudo tar xvf 3005217-r8168-dkms-8.040.00.tar.gz -C /usr/src
r8168-dkms-8.040.00/src/
r8168-dkms-8.040.00/src/Makefile
r8168-dkms-8.040.00/src/r8168_asf.c
r8168-dkms-8.040.00/src/Makefile_linux24x
r8168-dkms-8.040.00/src/r8168_asf.h
r8168-dkms-8.040.00/src/r8168_dash.h
r8168-dkms-8.040.00/src/r8168_n.c
r8168-dkms-8.040.00/src/rtltool.h
r8168-dkms-8.040.00/Makefile
r8168-dkms-8.040.00/dkms.conf
r8168-dkms-8.040.00/
r8168-dkms-8.040.00/README
r8168-dkms-8.040.00/src/rtl_eeprom.h
r8168-dkms-8.040.00/autorun.sh
r8168-dkms-8.040.00/src/rtltool.c
r8168-dkms-8.040.00/src/rtl_eeprom.c
r8168-dkms-8.040.00/src/r8168.h
r8168-dkms-8.040.00/src/r8168_realwow.h


$ sudo dkms add -m r8168-dkms -v 8.040.00


Creating symlink /var/lib/dkms/r8168-dkms/8.040.00/source ->
                 /usr/src/r8168-dkms-8.040.00


DKMS: add completed.


$ sudo dkms build -m r8168-dkms -v 8.040.00


Kernel preparation unnecessary for this kernel.  Skipping...


Building module:
cleaning build area....
'make' -C src/ all.........
cleaning build area....


DKMS: build completed.


$ sudo dkms install -m r8168-dkms -v 8.040.00


r8168:
Running module version sanity check.


Good news! Module version 8.040.00-NAPI for r8168.ko
exactly matches what is already found in kernel 3.13.0-35-generic.
DKMS will not replace this module.
You may override by specifying --force.


depmod....


DKMS: install completed.


$ sudo depmod -a


$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-3.13.0-62-generic


$ echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf
blacklist r8169
```

---

