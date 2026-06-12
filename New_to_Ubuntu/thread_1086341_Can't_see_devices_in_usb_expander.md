---
title: "Can't see devices in usb expander"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by gjahns on 2009-03-03
I'm a newbie to Ubuntu--just installed 8.04.  I have an old i386 that only has 2 usb ports on the backside--very inconvenient.  Long ago I bought a Belkin 4-port expander that worked fine under Windows 2000 and Fedora.  Now,if I plug a memory stick directly in one of the backside usb ports, Ubuntu automatically mounts it no-problem.  But if I put in the expander and then the memory stick into an expander port, it is not recognized.  If I do lsusb, I can see the expansion ports and the stick, but I don't know how to reference it to mount it.  I would appreciate any advice, ideally to have Ubuntu mount the stick automatically, or in any case how to manually mount it.  Thanks.

---

### Post by blueridgedog on 2009-03-04
Can you post the output of:
```

lsusb 
```

and

```
fdisk -l 
```

While the flash drive is in the expander which is in the PC?

---

### Post by gjahns on 2009-03-04
Sure...
:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 003: ID 08ec:0020 M-Systems Flash Disk Pioneers 
Bus 002 Device 002: ID 0451:2046 Texas Instruments, Inc. TUSB2046 Hub
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 04a9:10c2 Canon, Inc. (my printer, plugged in back)
Bus 001 Device 001: ID 0000:0000

~$ sudo fdisk -l
[sudo] password for gjahns: 

Disk /dev/sda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd7456d78

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9598    77095903+  83  Linux
/dev/sda2            9599       10011     3317422+   5  Extended
/dev/sda5            9599       10011     3317391   82  Linux swap / Solaris

..that's it.  I will be interested to hear what you think.  Thanks!

---

### Post by blueridgedog on 2009-03-05
I assume the M-Systems Flash Disk Pioneers usb device is the flash drive?

I am curious to see how your system sees the drive.  I suggest you unplug it, then run:

```
dmesg
```

Note what the last entry is, then plug it in, run dmesg again and post the output that is produced from plugging in the drive.  

Just by way of example, here is what happens when I plug in a drive:

```
[259820.712516] usb 4-5: new high speed USB device using ehci_hcd and address 2
[259820.843241] usb 4-5: configuration #1 chosen from 1 choice
[259821.116136] usbcore: registered new interface driver libusual
[259821.131877] Initializing USB Mass Storage driver...
[259821.132309] scsi4 : SCSI emulation for USB Mass Storage devices
[259821.133242] usb-storage: device found at 2
[259821.133249] usb-storage: waiting for device to settle before scanning
[259821.133254] usbcore: registered new interface driver usb-storage
[259821.134685] USB Mass Storage support registered.
[259826.128552] usb-storage: device scan complete
[259826.129646] scsi 4:0:0:0: Direct-Access     Kingston DataTraveler 2.0 1.00 PQ: 0 ANSI: 2
[259826.131119] sd 4:0:0:0: [sdc] 8089600 512-byte hardware sectors (4142 MB)
[259826.131615] sd 4:0:0:0: [sdc] Write Protect is off
[259826.131619] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[259826.131621] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[259826.133241] sd 4:0:0:0: [sdc] 8089600 512-byte hardware sectors (4142 MB)
[259826.133742] sd 4:0:0:0: [sdc] Write Protect is off
[259826.133746] sd 4:0:0:0: [sdc] Mode Sense: 23 00 00 00
[259826.133748] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[259826.133756]  sdc: sdc1
[259826.204983] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[259826.205071] sd 4:0:0:0: Attached scsi generic sg4 type 0
```

---

### Post by gjahns on 2009-03-05
Yes, M-Systems is the flash drive.
Following your instructions, here is the tail end of the second dmesg output. The first line is the last message after unplugging the flash drive and running dmesg the first time; lines 2 and beyond are what is added in the second dmesg:

[  464.784496] usb 2-1.4: USB disconnect, address 3
[  519.763762] usb 2-1.4: new full speed USB device using uhci_hcd and address 4
[  519.867728] usb 2-1.4: not running at top speed; connect to a high speed hub
[  519.903889] usb 2-1.4: rejected 1 configuration due to insufficient available bus power

...certainly a problem, but what is the solution/workaround?  Remember that my old configurations had no problem mounting the stick, so I doubt that it is purely a hardware problem.

Thanks for your help on this.  FYI, I will not be online until later tonight--please don't take my absence as a lack of appreciation!

---

### Post by blueridgedog on 2009-03-05
I know you said it worked before, but...

The power warning is telling, so my advice is:
-try it with nothing else in the hub
-consider a powered hub (cheap)
-try and bypass your system's power checking with:

```
sudo echo -n 1 >/sys/bus/usb/devices/2-1.4/bConfigurationValue
```

Then plug in the device.

(note the 2-1.4 above comes from your post, but it may have another name)

---

### Post by gjahns on 2009-03-06
-try it with nothing else in the hub
That is how I have been doing it
-consider a powered hub (cheap)
It is a powered hub (but I am going to check the power)
-try and bypass your system's power checking with:

Code:

sudo echo -n 1 >/sys/bus/usb/devices/2-1.4/bConfigurationValue

You were right, 2-1.4 is not the designation;  
~$ ls /sys/bus/usb/devices
1-0:1.0  1-1  1-1:1.0  2-0:1.0  2-1  2-1:1.0  3-0:1.0  4-0:1.0  usb1  usb2  usb3  usb4

I tried the command with all the 2s:  2-1 and usb2 gave "Permission denied", the others gave "No such file or directory"

I am going to move my hub to another machine and see if it has problems there.  Manana.  Thanks again.

---

### Post by gjahns on 2009-03-06
Mystery Solved!  Ultimately it was my stupidity.  There is an obscure switch on the edge of the hub: "bus" or "self", referring to the power source.  In moving the hub around, I apparently switched it from self-powered to powered through the usb.  Now I'm back to powered-up and good to go.

Great thanks, Blueridgedog, for your help!

---

### Post by blueridgedog on 2009-03-06
Excellent!

Is this really a 386 system?  

I know schools/institutions/governments that are disposing of P4's in the landfill.

---

### Post by gjahns on 2009-03-06
Yeah, I'm getting close to getting a new machine for the next 8 years...

---

