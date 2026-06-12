---
title: "hardy ndiswrapper help"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by adonikam on 2008-04-24
getting my wireless to work has been like pulling teeth.

I followed along this
[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306)
and i got ndiswrapper installed and everything, but no networks shown

if i type ifconfig
all i get is eth0 (my wired LAN) and lo

where should i go from here?

---

### Post by kevdog on 2008-04-24
Sorry that link didnt exactly work.

How about posting the following
lshw -C network
modinfo ndiswrapper
ndiswrapper -l

---

### Post by adonikam on 2008-04-24
thanks for helping meee

cs@cs-laptop:~$ sudo lshw -C network
  *-network:0             
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:ad:b7:98
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=full ip=192.168.0.105 latency=32 link=yes module=ssb multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Network controller
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=b43-pci-bridge latency=32 module=ssb
  *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:90:4b:62:fe:37
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11g

---

### Post by adonikam on 2008-04-24
cs@cs-laptop:~$ sudo modinfo ndiswrapper
modinfo: could not open ndiswrapper: No such device

thats probably bad

---

### Post by adonikam on 2008-04-24
cs@cs-laptop:~$ ndiswrapper -l
bcmwl5 : driver installed
	device (14E4:4320) present (alternate driver: bcm43xx)

---

### Post by adonikam on 2008-04-24
[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+4306)

---

### Post by kevdog on 2008-04-24
Weird

Try 

sudo modprobe ndiswrapper

and then retry
modinfo ndiswrapper

I think you may be OK.

Make sure the bcm43xx module is blacklisted
echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist

---

### Post by adonikam on 2008-04-24
cs@cs-laptop:~$ sudo modprobe ndiswrapper
cs@cs-laptop:~$ modinfo ndiswrapper
modinfo: could not open ndiswrapper: No such device
cs@cs-laptop:~$ echo "blacklist bcm43xx" | sudo tee -a /etc/modprobe.d/blacklist
blacklist bcm43xx
cs@cs-laptop:~$ 

Did you notice it says network disabled in the lshw output? 
i'm not OK :(

---

### Post by kevdog on 2008-04-25
Did you compile ndiswrapper from source or where did you get it?

Do the following:

sudo updatedb
locate ndiswrapper

---

### Post by adonikam on 2008-04-25
i compiled it from the source. i got it of the ndiswrapper website, 1.52


cs@cs-laptop:~$ locate ndiswrapper
/etc/ndiswrapper
/etc/modprobe.d/ndiswrapper
/etc/ndiswrapper/bcmwl5
/etc/ndiswrapper/bcmwl5/14E4:4320.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:0013:1737.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:0014:1737.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:0417:14E4.5.conf
/etc/ndiswrapper/bcmwl5/14E4:4320:0418:14E4.5.conf
/etc/ndiswrapper/bcmwl5/bcmwl5.inf
/etc/ndiswrapper/bcmwl5/bcmwl5.sys
/home/cs/ndiswrapper
/home/cs/ndiswrapper-1.52
/home/cs/ndiswrapper-1.52.tar.gz
/home/cs/.local/share/Trash/files/ndiswrapper
/home/cs/.local/share/Trash/files/ndiswrapper.2
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48.tar.gz
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/AUTHORS
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/ChangeLog
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/INSTALL
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/Makefile
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/README
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/loadndisdriver.8
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/ndiswrapper.8
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/ndiswrapper.spec
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/utils
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/.tmp_versions
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/Makefile
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/compat.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/crt.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/crt_exports.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/divdi3.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/hal.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/hal_exports.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/iw_ndis.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/iw_ndis.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/lin2win.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/loader.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/loader.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/longlong.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/ndis.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/ndis.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/ndis_exports.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/ndiswrapper.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel_exports.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel_io.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/ntoskernel_io_exports.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/pe_linker.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/pe_linker.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/pnp.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/pnp.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/proc.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/rtl.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/rtl_exports.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/usb.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/usb.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/usb_exports.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/win2lin_stubs.S
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/winnt_types.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/workqueue.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/wrapmem.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/wrapmem.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/wrapndis.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/wrapndis.h
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/driver/wrapper.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/utils/Makefile
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/utils/loadndisdriver.c
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/utils/ndiswrapper
/home/cs/.local/share/Trash/files/ndiswrapper/ndiswrapper-1.48/utils/ndiswrapper-buginfo
/home/cs/.local/share/Trash/info/ndiswrapper.2.trashinfo
/home/cs/.local/share/Trash/info/ndiswrapper.trashinfo
/home/cs/ndiswrapper-1.52/AUTHORS
/home/cs/ndiswrapper-1.52/ChangeLog
/home/cs/ndiswrapper-1.52/INSTALL
/home/cs/ndiswrapper-1.52/Makefile
/home/cs/ndiswrapper-1.52/README
/home/cs/ndiswrapper-1.52/driver
/home/cs/ndiswrapper-1.52/loadndisdriver.8
/home/cs/ndiswrapper-1.52/ndiswrapper.8
/home/cs/ndiswrapper-1.52/ndiswrapper.spec
/home/cs/ndiswrapper-1.52/utils
/home/cs/ndiswrapper-1.52/driver/.built-in.o.cmd
/home/cs/ndiswrapper-1.52/driver/.crt.o.cmd
/home/cs/ndiswrapper-1.52/driver/.divdi3.o.cmd
/home/cs/ndiswrapper-1.52/driver/.hal.o.cmd
/home/cs/ndiswrapper-1.52/driver/.iw_ndis.o.cmd
/home/cs/ndiswrapper-1.52/driver/.loader.o.cmd
/home/cs/ndiswrapper-1.52/driver/.ndis.o.cmd
/home/cs/ndiswrapper-1.52/driver/.ndiswrapper.ko.cmd
/home/cs/ndiswrapper-1.52/driver/.ndiswrapper.mod.o.cmd
/home/cs/ndiswrapper-1.52/driver/.ndiswrapper.o.cmd
/home/cs/ndiswrapper-1.52/driver/.ntoskernel.o.cmd
/home/cs/ndiswrapper-1.52/driver/.ntoskernel_io.o.cmd
/home/cs/ndiswrapper-1.52/driver/.pe_linker.o.cmd
/home/cs/ndiswrapper-1.52/driver/.pnp.o.cmd
/home/cs/ndiswrapper-1.52/driver/.proc.o.cmd
/home/cs/ndiswrapper-1.52/driver/.rtl.o.cmd
/home/cs/ndiswrapper-1.52/driver/.usb.o.cmd
/home/cs/ndiswrapper-1.52/driver/.wrapmem.o.cmd
/home/cs/ndiswrapper-1.52/driver/.wrapndis.o.cmd
/home/cs/ndiswrapper-1.52/driver/.wrapper.o.cmd
/home/cs/ndiswrapper-1.52/driver/Makefile
/home/cs/ndiswrapper-1.52/driver/Module.symvers
/home/cs/ndiswrapper-1.52/driver/built-in.o
/home/cs/ndiswrapper-1.52/driver/compat.h
/home/cs/ndiswrapper-1.52/driver/crt.c
/home/cs/ndiswrapper-1.52/driver/crt.o
/home/cs/ndiswrapper-1.52/driver/crt_exports.h
/home/cs/ndiswrapper-1.52/driver/divdi3.c
/home/cs/ndiswrapper-1.52/driver/divdi3.o
/home/cs/ndiswrapper-1.52/driver/hal.c
/home/cs/ndiswrapper-1.52/driver/hal.o
/home/cs/ndiswrapper-1.52/driver/hal_exports.h
/home/cs/ndiswrapper-1.52/driver/iw_ndis.c
/home/cs/ndiswrapper-1.52/driver/iw_ndis.h
/home/cs/ndiswrapper-1.52/driver/iw_ndis.o
/home/cs/ndiswrapper-1.52/driver/lin2win.h
/home/cs/ndiswrapper-1.52/driver/loader.c
/home/cs/ndiswrapper-1.52/driver/loader.h
/home/cs/ndiswrapper-1.52/driver/loader.o
/home/cs/ndiswrapper-1.52/driver/longlong.h
/home/cs/ndiswrapper-1.52/driver/ndis.c
/home/cs/ndiswrapper-1.52/driver/ndis.h
/home/cs/ndiswrapper-1.52/driver/ndis.o
/home/cs/ndiswrapper-1.52/driver/ndis_exports.h
/home/cs/ndiswrapper-1.52/driver/ndiswrapper.h
/home/cs/ndiswrapper-1.52/driver/ndiswrapper.ko
/home/cs/ndiswrapper-1.52/driver/ndiswrapper.mod.c
/home/cs/ndiswrapper-1.52/driver/ndiswrapper.mod.o
/home/cs/ndiswrapper-1.52/driver/ndiswrapper.o
/home/cs/ndiswrapper-1.52/driver/ntoskernel.c
/home/cs/ndiswrapper-1.52/driver/ntoskernel.h
/home/cs/ndiswrapper-1.52/driver/ntoskernel.o
/home/cs/ndiswrapper-1.52/driver/ntoskernel_exports.h
/home/cs/ndiswrapper-1.52/driver/ntoskernel_io.c
/home/cs/ndiswrapper-1.52/driver/ntoskernel_io.o
/home/cs/ndiswrapper-1.52/driver/ntoskernel_io_exports.h
/home/cs/ndiswrapper-1.52/driver/pe_linker.c
/home/cs/ndiswrapper-1.52/driver/pe_linker.h
/home/cs/ndiswrapper-1.52/driver/pe_linker.o
/home/cs/ndiswrapper-1.52/driver/pnp.c
/home/cs/ndiswrapper-1.52/driver/pnp.h
/home/cs/ndiswrapper-1.52/driver/pnp.o
/home/cs/ndiswrapper-1.52/driver/proc.c
/home/cs/ndiswrapper-1.52/driver/proc.o
/home/cs/ndiswrapper-1.52/driver/rtl.c
/home/cs/ndiswrapper-1.52/driver/rtl.o
/home/cs/ndiswrapper-1.52/driver/rtl_exports.h
/home/cs/ndiswrapper-1.52/driver/usb.c
/home/cs/ndiswrapper-1.52/driver/usb.h
/home/cs/ndiswrapper-1.52/driver/usb.o
/home/cs/ndiswrapper-1.52/driver/usb_exports.h
/home/cs/ndiswrapper-1.52/driver/win2lin_stubs.S
/home/cs/ndiswrapper-1.52/driver/winnt_types.h
/home/cs/ndiswrapper-1.52/driver/workqueue.c
/home/cs/ndiswrapper-1.52/driver/wrapmem.c
/home/cs/ndiswrapper-1.52/driver/wrapmem.h
/home/cs/ndiswrapper-1.52/driver/wrapmem.o
/home/cs/ndiswrapper-1.52/driver/wrapndis.c
/home/cs/ndiswrapper-1.52/driver/wrapndis.h
/home/cs/ndiswrapper-1.52/driver/wrapndis.o
/home/cs/ndiswrapper-1.52/driver/wrapper.c
/home/cs/ndiswrapper-1.52/driver/wrapper.o
/home/cs/ndiswrapper-1.52/utils/Makefile
/home/cs/ndiswrapper-1.52/utils/loadndisdriver
/home/cs/ndiswrapper-1.52/utils/loadndisdriver.c
/home/cs/ndiswrapper-1.52/utils/ndiswrapper
/home/cs/ndiswrapper-1.52/utils/ndiswrapper-buginfo
/lib/modules/2.6.24-16-generic/misc/ndiswrapper.ko
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper
/lib/modules/2.6.24-16-generic/ubuntu/misc/ndiswrapper/ndiswrapper.ko
/usr/sbin/ndiswrapper
/usr/sbin/ndiswrapper-1.9
/usr/sbin/ndiswrapper-buginfo
/usr/share/doc/ndiswrapper-common
/usr/share/doc/ndiswrapper-utils-1.9
/usr/share/doc/ndiswrapper-common/AUTHORS
/usr/share/doc/ndiswrapper-common/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-common/README
/usr/share/doc/ndiswrapper-common/README.Debian
/usr/share/doc/ndiswrapper-common/changelog.Debian.gz
/usr/share/doc/ndiswrapper-common/copyright
/usr/share/doc/ndiswrapper-utils-1.9/AUTHORS
/usr/share/doc/ndiswrapper-utils-1.9/NEWS.Debian.gz
/usr/share/doc/ndiswrapper-utils-1.9/README
/usr/share/doc/ndiswrapper-utils-1.9/changelog.Debian.gz
/usr/share/doc/ndiswrapper-utils-1.9/copyright
/usr/share/man/man8/ndiswrapper-1.9.8.gz
/usr/share/man/man8/ndiswrapper.8
/usr/share/man/man8/ndiswrapper.8.gz
/var/cache/apt/archives/ndiswrapper-common_1.50-1ubuntu1_all.deb
/var/cache/apt/archives/ndiswrapper-utils-1.9_1.50-1ubuntu1_i386.deb
/var/lib/dpkg/info/ndiswrapper-common.list
/var/lib/dpkg/info/ndiswrapper-common.md5sums
/var/lib/dpkg/info/ndiswrapper-utils-1.9.list
/var/lib/dpkg/info/ndiswrapper-utils-1.9.md5sums

---

### Post by kevdog on 2008-04-25
Did you try to install ndiswrapper from repository first?

When you do
sudo modprobe -r ndiswrapper 
sudo modprobe ndiswrapper

and then check dmesg (post only relevant to ndiswrapper), what does it say?

---

### Post by dmartin on 2008-05-04
Wow, thanks so much for this guide.  I've tried everything I could find, and failed for the last couple of weeks to get the wireless on my laptop (HP DV9627CL) working with Hardy.  This worked perfectly.  It was a great feeling when I saw the light change from orange to blue during the reboot for the first time since Gutsy.

---

