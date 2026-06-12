---
title: "broadband modem not detected by Ubuntu 8"
date: 2008-08-31
forum: Networking &amp; Wireless
---

### Post by jofish on 2008-08-31
Sony vaio vgn-cr240e dual boot , vindoze vista and Ubuntu 8.X .
Had Ubuntu 7.X installed but had trouble with sound card detection. Solved the problem by upgrading to Ubuntu 8.x. Now I have a dongle Frankling usb modem cdu-680 for wireless broadband connection. It was being detected fine in Ubuntu 7.x. Now the device is not seen by Ubuntu 8.X. Any suggestions? 
Device is detected and listed by dmesg as a USB media device. That is it!
In Ubuntu 7.x it was also detected as a modem and it was possible to configure it as a modem and use it to get connected.
Please help! something is missing in the kernel that was there in the previous version of Ubuntu. lspci,dmesg and /var/log/messages do not show the device as being there.....?????
Thanks for your help I really don't want to have to revert to 7.X

---

### Post by pytheas22 on 2008-09-01
Probably the wireless driver that was used for the card in 7.10 was either not included in 8.04, or 8.04 uses a different version (there were a lot of changes in wireless support between 7.10 and 8.04 that made things better for most people, but caused some problems for others).  Please post the output of these commands so that we can figure out what you need to do:
```

lsusb
lshw -C Network
```

---

### Post by jofish on 2008-09-01
this is the output of lsusb:
Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 05ca:1839 Ricoh Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 003: ID 16d8:6803  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXx

this is the output of lshw -C Network

  *-network
       description: Network controller
       product: PRO/Wireless 4965 AG or AGN Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwl4965 latency=0 module=iwl4965
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 01
       serial: 00:1a:80:3f:24:20
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=half latency=0 link=no module=r8169 multicast=yes port=twisted pair

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

Previously I could unmount the usb with *$sudo umount /dev/sdb * then I would [I]$modprobe usbserial idXXX product=XXX [I] that would identify the device as a modem and be assigned a "dev/ttyACM0" or "/dev/ttyUSB0" then I could launch the dialer and connect.......

 now the system takes the [I] sudo /sbin/modprobe.....[I] command without return erros but no device ttyAXXX is created..... therefore cannot launch the dialer....

Please help...

---

### Post by jofish on 2008-09-01
Btw I see  lsusb detects the device with vendor-id and product-id as bus 004 dev 003...

---

### Post by pytheas22 on 2008-09-01
Thanks for the information.  I'm still not sure what's going.  I did some googling but most information about this card seems to be in Spanish, which I can't read.  But it does seem possible to make this work on Ubuntu.

I'll keep researching, but in the meantime, could you please unplug the modem, plug it back in, then immediately post the output of this command:
```

dmesg | tail
```

That might help figure out what's going on.

Also, when you say:

> Previously I could unmount the usb with $sudo umount /dev/sdb then I would [i]$modprobe usbserial idXXX product=XXX [i] that would identify the device as a modem and be assigned a "dev/ttyACM0" or "/dev/ttyUSB0" then I could launch the dialer and connect.......

now the system takes the [i] sudo /sbin/modprobe.....[i] command without return erros but no device ttyAXXX is created..... therefore cannot launch the dialer....


was it on Hardy that you could unmount the device, or was this when you were still using Gutsy?

Also, what is the rest of the "sudo modprobe..." that you used to bring the device up?

---

### Post by jofish on 2008-09-02
Thanks for the research...

The modem worked with Ubuntu 7.X. There is a compiled program "itfchg" which unmounts /dev/sdb and attaches a dev/ttyACM0 to the modem. It run 
"sudo itfchg /dev/sdb"
I managed to do the same by running the following: 
"sudo umount sdb"
"sudo /sbin/modprobe usbserial vendor=0x16d8 product=0x6522" 
 then
"bash execute.sh" # dials from  /dev/ttyACM0
and 7 seconds later I was online......with a nice working ppp0 connection full speed.
the program itfchg ( binary) no source code...comes with the modem in the Linux folder . I guess I can somehow send it somewhere to be retreived.
This is my first time posting or using Ubuntu forums , pardon my inexperience.


here is the output of "sudo dmesg | tail "
[   79.064850] sd 3:0:0:0: [sdb] Write Protect is off
[   79.064857] sd 3:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[   79.064862] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   79.073849] sd 3:0:0:0: [sdb] 135169 512-byte hardware sectors (69 MB)
[   79.076833] sd 3:0:0:0: [sdb] Write Protect is off
[   79.076841] sd 3:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[   79.076845] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[   79.076854]  sdb: unknown partition table
[   79.104891] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[   79.104985] sd 3:0:0:0: Attached scsi generic sg2 type 0

XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX

 

Thank you!

---

### Post by pytheas22 on 2008-09-03
Thanks for the information.  This line from dmesg is interesting:

```
[ 79.076854] sdb: unknown partition table
```

It sounds like either the partition table of the device's disk is damaged, or Linux for some reason thinks there's a problem with it.  Does the device still work in Windows?  It could be the case that it's not actually damaged, but that for some reason the kernel in Hardy has a problem with the device, even though Gutsy didn't.

I found [this post]("http://forum.openwrt.org/viewtopic.php?id=14792") where someone seems to have similar problems with the same modem, and also gets the "unknown partition table" error.  Unfortunately there's no clear solution, but the fact that this happened to someone else suggests that it's a problem with the kernel, not your hardware.  You may want to boot the Gutsy live CD and see if the output of "dmesg | tail" after inserting the modem is different there.

Also, in that thread, someone mentions having to modprobe usbserial.  Does it make a difference if after inserting the device you type:
```

sudo modprobe usbserial
```

---

### Post by timcredible on 2008-09-03
if it's usb-connected, you don't need a driver.  just run gnome-ppp, choose the port (/dev/ACM0), and dial the number.

---

