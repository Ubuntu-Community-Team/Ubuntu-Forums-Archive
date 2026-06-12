---
title: "Microsoft LifeCam VX1000"
date: 2009-02-08
forum: New to Ubuntu
---

### Post by um_nirvani on 2009-02-08
Web Cam Not detected.

unirvani@MetalMachine:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 005: ID 045e:00f7 Microsoft Corp. LifeCam VX-1000.


dmesg output
[ 4280.948021] usb 3-2: new full speed USB device using uhci_hcd and address 5
[ 4281.110224] usb 3-2: configuration #1 chosen from 1 choice
[ 4281.116042] usb 3-2: SN9C105 PC Camera Controller detected (vid:pid 0x045E:0x00F7)
[ 4281.255047] usb 3-2: No supported image sensor detected for this bridge
[ 4577.112713] usbcore: deregistering interface driver sn9c102


In cheese it says no camera detected and in camorama it says 'could not connect to video device'.... 

Please help me resolve this.

---

### Post by flanagan on 2009-02-09
The suggestions in this thread seemed to have helped some people:

[http://ubuntuforums.org/showthread.php?t=1034988&highlight=lifecam+vx1000](http://ubuntuforums.org/showthread.php?t=1034988&highlight=lifecam+vx1000)

---

### Post by um_nirvani on 2009-02-09
> **flanagan said:**
> The suggestions in this thread seemed to have helped some people:

[http://ubuntuforums.org/showthread.php?t=1034988&highlight=lifecam+vx1000](http://ubuntuforums.org/showthread.php?t=1034988&highlight=lifecam+vx1000)



Yes..  I found this link few mins back and working on it. 
Thank you.

---

