---
title: "unable to enumerate USB device on port 1"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by Lozza1980 on 2011-04-28
Hi,

I have a 2TB Western Digital Drive in an external usb enclosure formatted with NTFS. For some reason this works with ubuntu for a week or so at a time and then disappears.

I can see the following in dmesg when this happens:

[785503.625035] usb 2-1: new high speed USB device using ehci_hcd and address 9
[785503.665284] usb 2-1: device descriptor read/8, error -71
[785503.796279] usb 2-1: device descriptor read/8, error -71
[785503.897041] hub 2-0:1.0: unable to enumerate USB device on port 1
[785504.289042] usb 5-1: new full speed USB device using uhci_hcd and address 5
[785504.409034] usb 5-1: device descriptor read/64, error -32
[785504.632041] usb 5-1: device descriptor read/64, error -32
[785504.849052] usb 5-1: new full speed USB device using uhci_hcd and address 6
[785504.969046] usb 5-1: device descriptor read/64, error -32
[785505.192046] usb 5-1: device descriptor read/64, error -32
[785505.409032] usb 5-1: new full speed USB device using uhci_hcd and address 7
[785505.439452] usb 5-1: device descriptor read/8, error -71
[785505.567458] usb 5-1: device descriptor read/8, error -71
[785505.784062] usb 5-1: new full speed USB device using uhci_hcd and address 8
[785505.815455] usb 5-1: device descriptor read/8, error -71
[785505.943450] usb 5-1: device descriptor read/8, error -71
[785506.044044] hub 5-0:1.0: unable to enumerate USB device on port 1

Output from lsusb:

:~$ lsusb
Bus 007 Device 002: ID 046d:c52a Logitech, Inc. 
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 192f:0616 Avago Technologies, Pte. 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 0dc4:00d3 Macpower Peripherals, Ltd 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

My ubuntu release:

:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 10.10
Release:	10.10
Codename:	maverick

My computer is a Dell Studio Hybrid.

I've had a good search on the net but nothing concrete as to why this occurs. Sometimes it screws up the drive and I cannot access it anymore, sometimes if I power it off and back on again ubuntu can see it again. Its driving me a little mad!!

Ive tried 2 usb cables (this could be that they are both faulty????), different HDD enclosures and different power supplies. 

I read to unload the ehci_hcd module, this doesnt work and I think would reduce the speed of the USB device?

:~$ sudo rmmod ehci_hcd
ERROR: Module ehci_hcd does not exist in /proc/modules

---

### Post by jtarin on 2011-04-28
Have you tried a different kernel to boot with? Has this problem only surfaced after an upgrade or update?

[Follow this thread]("http://www.mailrepository.com/ubuntu-bugs.lists.ubuntu.com/msg/3513332/")......seems to be a bug in one of the kernels but taken care of.

I have a 1 TB drive and have never had a problem with it....through 10.04-10.10.....now on newest kernel in repository...32 bit.

---

### Post by Lozza1980 on 2011-05-01
Hi,

Thanks for your reply.

Ive just upgraded my ubuntu over the weekend to:

Distributor ID:	Ubuntu
Description:	Ubuntu 11.04
Release:	11.04
Codename:	natty

Im hoping this will resolve the problem!

Regards

Lawrence

---

### Post by Lozza1980 on 2011-05-01
My kernel version

2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

---

### Post by robert leleu on 2011-11-12
I have this problem now, from about 1 month under Ubuntu 11.04

---

