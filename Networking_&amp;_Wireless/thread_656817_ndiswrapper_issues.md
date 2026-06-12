---
title: "ndiswrapper issues"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by merlin666 on 2008-01-02
I am having a hard time getting wireless going again after upgrading to gutsy. I thought I had removed  previous ndiswrapper before installing the latest (1.51) version, but it still seems to be around:

rolf@ubuntu:~/downloads$     dmesg | grep ndiswrapper
[   46.322938] ndiswrapper version 1.50 loaded (smp=yes, preempt=no)
[   46.414665] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[   46.415671] ndiswrapper: driver netbc564 (,10/01/2002,3.70.17.5) loaded
[   46.420960] ndiswrapper: using IRQ 18
[   46.734821] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[   46.744953] usbcore: registered new interface driver ndiswrapper
[ 5795.551131] ndiswrapper: device eth1 removed
[ 5795.551547] usbcore: deregistering interface driver ndiswrapper
[ 6919.138679] ndiswrapper version 1.51 loaded (smp=yes, preempt=no)
[ 6919.162968] ndiswrapper (link_pe_images:576): fixing KI_USER_SHARED_DATA address in the driver
[ 6919.164065] ndiswrapper: driver netbc564 (,10/01/2002,3.70.17.5) loaded
[ 6919.167502] ndiswrapper: using IRQ 18
[ 6919.283281] ndiswrapper: changing interface name from 'wlan0' to 'eth1'
[ 6919.288571] usbcore: registered new interface driver ndiswrapper
[ 6924.448987] ndiswrapper: device eth1 removed
[ 6924.449122] usbcore: deregistering interface driver ndiswrapper

whereas:
rolf@ubuntu:~/downloads$ ndiswrapper -v
utils version: '1.9', utils version needed by module: '1.9'
module details:
filename:       /lib/modules/2.6.22-14-generic/misc/ndiswrapper.ko
version:        1.51
vermagic:       2.6.22-14-generic SMP mod_unload 


rolf@ubuntu:~/downloads$ ndiswrapper -l
netbc564 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)
rolf@ubuntu:~/downloads$ 


How can I get rid of the 1.50 loaded and the dreaded bcm43xx driver?

---

### Post by Ripfox on 2008-01-03
[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice#head-f744e28e6c78eb83d22be77819b130016a8e51f3](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice#head-f744e28e6c78eb83d22be77819b130016a8e51f3)

I have used this many times...just replace the version of ndiswrapper with the current one in the commands. I used it like a week ago on a laptop that freaks out when I use the restricted driver (touchpad freaks) and it worked like a charm.

Good luck!

---

### Post by merlin666 on 2008-01-03
> **ripfox said:**
> [https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice#head-f744e28e6c78eb83d22be77819b130016a8e51f3](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice#head-f744e28e6c78eb83d22be77819b130016a8e51f3)

I have used this many times...just replace the version of ndiswrapper with the current one in the commands. I used it like a week ago on a laptop that freaks out when I use the restricted driver (touchpad freaks) and it worked like a charm.

Good luck!

Thanks, unfortunately some of these commands don't work anymore. For example when I was trying to edit iftab I got this:

# This file is no longer used and has been automatically replaced.
# See /etc/udev/rules.d/70-persistent-net.rules for more information.
#

# This file assigns persistent names to network interfaces.  See iftab(5).
#eth0 mac 00:03:25:15:5f:eb

---

### Post by kevdog on 2008-01-03
Can you do the following:

sudo updatedb
locate ndiswrapper

Can you post the results of the last command --> This will basically tell you were all the ndiswrapper files are located.

---

