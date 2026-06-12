---
title: "Fails to build driver from kernel source -  Invalid module format"
date: 2014-03-09
forum: Networking &amp; Wireless
---

### Post by yoave on 2014-03-09
hi,

I'm running Ubuntu 12.04 with kernel 3.2.0-59-generic.
I'm trying to build ixgbe 3.6.7 kernel driver from kernel sources as follows:

1) get the sources:

sudo apt-get source linux-image-$(uname -r)

2) untar and patch:

tar xvzf linux_3.2.0.orig.tar.gz
gzip -d linux_3.2.0-59.90.diff.gz
mv linux-3.2 linux-3.2.0
patch -p0 -i linux_3.2.0-59.90.diff.gz

3) prepare and build:

make oldconfig
make drivers/net/ethernet/intel/ixgbe/ixgbe.ko


however, the kernel module fails loading and contain the wrong vermagic:

root@ubuild01:~/source/temp3/linux-3.2.0# insmod drivers/net/ethernet/intel/ixgbe/ixgbe.ko
insmod: [COLOR=#ff0000]error inserting 'drivers/net/ethernet/intel/ixgbe/ixgbe.ko': -1 Invalid module format[/COLOR]

root@ubuild01:~/source/temp3/linux-3.2.0# modinfo drivers/net/ethernet/intel/ixgbe/ixgbe.ko | grep ver
filename:       drivers/net/ethernet/intel/ixgbe/ixgbe.ko
version:        3.6.7-k
description:    Intel(R) 10 Gigabit PCI Express Network Driver
srcversion:     BB7BF3E3F069BB9966A294D
vermagic:       [COLOR=#ff0000]3.2.54[/COLOR] SMP mod_unload modversions 



any ideas?

---

