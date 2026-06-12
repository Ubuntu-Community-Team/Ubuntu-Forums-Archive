---
title: "Lucid Lynx doesn't mount my Canon 450d :("
date: 2010-05-09
forum: New to Ubuntu
---

### Post by naomibrown on 2010-05-09
Hi,

I'm having problems with 10.04 because it doesn't mount my Canon 450d. I've used this camera a lot before the upgrade and it always worked fine.

Have I forgotten to add something?

Thanks,
Naomi

---

### Post by naomibrown on 2010-05-09
Had a google, but couldn't find anything. 

I tried sudo lsusb before I plugged it in and it said:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

And after:

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 04fc:0003 Sunplus Technology Co., Ltd CM1092 Optical Scroller Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 04a9:3145 Canon, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

So I guess it is there ... I just can't access it :(

---

### Post by streeker on 2010-05-21
Hi,
I believe I'm having the same issue with a Canon 350D although an occasional attempt is made to mount the device with the following errors:

I get a popup -
Error initializing camera: -114: OS error in camera communication

and from the log

$ dmesg | tail | grep usb
[ 6379.040532] usb 1-3: usbfs: USBDEVFS_CONTROL failed cmd gvfsd-gphoto2 rqt 64 rq 4 len 80 ret -110

additional info:

$ lsusb
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 017: ID 04a9:30ee Canon, Inc. EOS 350D
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

$ lspci | grep USB
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)

Ubuntu Release 10.04
Kernel 2.6..32-22-Generic
libgphoto2-2 / libgphoto2-port0 Version: 2.4.8-0ubuntu2

The CF card mounts with gphotofs in a card reader without issue. The camera is mounted in 9.10 without issue.

Thanks!

---

### Post by Koppie on 2010-06-09
Found the solution here: [http://ubuntuforums.org/showpost.php?p=7173964&postcount=3](http://ubuntuforums.org/showpost.php?p=7173964&postcount=3)

Short answer: run the following commands
> sudo killall gvfs-gphoto2-volume-monitor
sudo chmod -x /usr/lib/gvfs/gvfs-gphoto2-volume-monitor


---

### Post by misterspider on 2010-06-20
> **Koppie said:**
> Found the solution here: [http://ubuntuforums.org/showpost.php?p=7173964&postcount=3](http://ubuntuforums.org/showpost.php?p=7173964&postcount=3)

Short answer: run the following commands

I'm not quite getting the same output from dmesg, but my canon ixus 430 will not mount either.

```
david@david-desktop:~$ dmesg | tail | grep usb
[   95.820010] usb 6-1: new full speed USB device using uhci_hcd and address 2
[   95.980962] usb 6-1: configuration #1 chosen from 1 choice

```

I tried the "killall" command followed by "chmod +x" suggested, but nothing.

The camera is being detected (although not sure that its a powershot as ubuntu thinks it is).

```
david@david-desktop:~$ lsusb
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 003: ID 04a9:30ba Canon, Inc. PowerShot S410 Digital Elph
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c512 Logitech, Inc. LX-700 Cordless Desktop Receiver
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

I'm using Xubuntu, and there is a removable drives and media settings option for cameras. It says "import digital photos when connected", and then asks for a command. Is this where to solve the problem?

---

