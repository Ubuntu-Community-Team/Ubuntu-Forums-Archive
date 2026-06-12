---
title: "No eth0 with ubuntu-mininal but LiveCD works"
date: 2014-07-09
forum: Networking &amp; Wireless
---

### Post by maherhome on 2014-07-09
Hi,


On an HP230 booting with 12.4.04 desktop LiveCD ethernet works fine, with e1000e module running, but after I install no ethernet device is found.

I'm doing a special install ([zfs on root]("https://github.com/zfsonlinux/pkg-zfs/wiki/HOWTO-install-Ubuntu-to-a-Native-ZFS-Root-Filesystem")) that installs ubuntu-minimal.  After reboot ZFS works great, but there's no ethernet device (ifconfig -a shows only *lo*)

I retried the install with ubuntu-standard but still got no eth device.

lspci shows the following (with the ZFS system and LiveCD):

```
00:19.0 Ethernet Controller [0200]: Intel Corporation Device [8086:153a] (rev 05)
```

/etc/udev/rules.d/70-persistent-net.rules has only comments.

*modprobe e1000e *works but doesn't seem to find any hardware.  Only lines in dmesg are as follows:

```
e1000e: Intel(R) PRO/1000 Network Driver  - 1.5.1-k
e1000e: Copyright(c) 1999-2011 Intel Corporation
```

Doing lsmod with LiveCD had many more modules loaded.

Any help would be greatly appreciated!

Thanks
Steve

---

### Post by chili555 on 2014-07-09
> e1000e: Intel(R) PRO/1000 Network Driver  - [COLOR="#FF0000"]1.5.1-k[/COLOR]It looks like the version of e1000e in 12.04.4 doesn't cover your device; confirm:```
modinfo e1000e | grep 153A
```You will probably get a blank. In my later version, I see:```
chili@T410:~$ modinfo e1000e | grep -e 153A -e version
version:        [COLOR="#FF0000"]2.3.2-k[/COLOR]
srcversion:     FAFC167239309C03F11F440
alias:          pci:v0000[COLOR="#FF0000"]8086[/COLOR]d0000[COLOR="#FF0000"]153A[/COLOR]sv*sd*bc*sc*i*
```You might try a later version of Ubuntu.

---

### Post by maherhome on 2014-07-09
Thanks for the response Chili555.

Hmm, I was using a 12.4.04 install DVD, and its "Try Ubuntu" boot had a functioning e1000e.  Hmm, perhaps my apt-get install ubuntu-minimal installs an older e1000e module compared to the install DVD.  I'll try downloading the latest e1000e (from [here]("https://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&lang=eng")) when doing the install.

---

### Post by chili555 on 2014-07-09
> **maherhome said:**
> Thanks for the response Chili555.

Hmm, I was using a 12.4.04 install DVD, and its "Try Ubuntu" boot had a functioning e1000e.  Hmm, perhaps my apt-get install ubuntu-minimal installs an older e1000e module compared to the install DVD.  I'll try downloading the latest e1000e (from [here]("https://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=15817&lang=eng")) when doing the install.Please note that to compile this driver, you will also need build-essential and linux-headers-generic and all their dependencies.

---

### Post by maherhome on 2014-07-10
This looks promising as the 1.5.1 version indeed does **not** have a 153A vendor ID (using *modinfo*).

So it looks like the 12.4.04 DVD has the newer driver (which works) but the following combination leaves me with the older driver:


[LIST=1]
[*]debootstrap precise /mnt
[*]chroot /mnt /bin/bash --login
[*]apt-get install ubuntu-minimal
[*]apt-get dist-upgrade
[/LIST]


Perhaps somehow the newer e1000e isn't compatible with 12.4? (FYI I am stuck with 12.4 for various reasons))

Steve

---

### Post by chili555 on 2014-07-10
> Perhaps somehow the newer e1000e isn't compatible with 12.4? Well, I assume it is compatible, since the live CD includes it. I haven't even a wild guess as to why the minimal doesn't use the same driver version. Does it use the same kernel?```
uname -r
```If they are the same or probably reasonably close, you might try copying over the driver and its dependency from the live CD.```
modinfo e1000e | grep depends
```On my 14.04 system, it is *ptp*.

If the kernel versions are similar, 3.8.0-xx or some such, copy over /lib/modules/3.1whatever-generic/kernel/drivers/ptp/ptp.ko to the minimal system, as well as /lib/modules/3.1whatever-generic/kernel/drivers/net/ethernet/intel/e1000e/e1000e.ko.

If the live CD is 3.13.0-xx and the minimal is 3.8.0-xx, it may not work, but it just takes just a few moments to try. Dr. Chili recommends that you back up responsibly.

Load the new module:```
sudo modprobe e1000e
```If it springs to life, then compile.

This is all very experimental; I haven't tried it myself.

---

### Post by maherhome on 2014-07-11
All fixed.  Downloaded e1000e tarball when still booted from LiveCD, did my install (which included build-essential), rebooted, than built/installed e1000e and all is good.

Thanks Chili!

Steve

---

