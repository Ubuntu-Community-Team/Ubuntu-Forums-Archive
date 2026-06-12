---
title: "What does this mean?"
date: 2009-01-28
forum: New to Ubuntu
---

### Post by oiler on 2009-01-28
What does below reference to USB mean?  Are the USB ports faulty? Nothing connected to USB is recognized even though power to device (memory sticks) is there.  Any help would be greatly appreciated.

Thanks,
Oiler

caf@caf-desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
caf@caf-desktop:~$ dmesg | tail
[  129.516029] usb 3-2: device descriptor read/64, error -62
[  129.804025] usb 3-2: device descriptor read/64, error -62
[  130.084030] usb 3-2: new full speed USB device using ohci_hcd and address 11
[  130.268022] usb 3-2: device descriptor read/64, error -62
[  130.556023] usb 3-2: device descriptor read/64, error -62
[  130.836018] usb 3-2: new full speed USB device using ohci_hcd and address 12
[  131.244024] usb 3-2: device not accepting address 12, error -62
[  131.420026] usb 3-2: new full speed USB device using ohci_hcd and address 13
[  131.828020] usb 3-2: device not accepting address 13, error -62
[  131.828585] hub 3-0:1.0: unable to enumerate USB device on port 2

caf@caf-desktop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xec0e08d4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9506    76356913+  83  Linux
/dev/sda2            9507        9729     1791247+   5  Extended
/dev/sda5            9507        9729     1791216   82  Linux swap / Solaris

caf@caf-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              72G  2.1G   67G   3% /
tmpfs                 299M     0  299M   0% /lib/init/rw
varrun                299M  108K  299M   1% /var/run
varlock               299M     0  299M   0% /var/lock
udev                  299M  2.7M  296M   1% /dev
tmpfs                 299M     0  299M   0% /dev/shm
lrm                   299M  2.0M  297M   1% /lib/modules/2.6.27-9-generic/volatile

---

### Post by Cypher on 2009-01-28
Either the USB port or the devices you are using are faulty. The message "device descriptor read/64, error -62" means that Linux is trying to figure out what kind of device is plugged in. That information is stored in the USB device itself in a known area for USB devices.

Once the discovery fails, the Kernel will try a different USB address to see if it can talk to the device, and it looks like the new addresses aren't be accepted by the device probably because it accepted the previous address but the discovery process got halted because of the errors.

Have you tried other USB devices and does this problem occur on every USB port?

---

### Post by Kevbert on 2009-01-28
I also get the same messages, but am able to the USB ports.  I read somewhere that it's caused by noise on the USB lines. It you have an option in the bios to set the USB to 1.1 (as opposed to 2.0) that may help but you'll access any USB devices at reduced speeds). If the USB connections are mounted off the motherboard you could try moving the joining cable(s).

---

### Post by oiler on 2009-01-28
Thanks folks!  Found one USB port on back of CPU that works.  Believe may have noise issue or faulty connection to motherboard.  All devices work in other computers so problem is definately in sytem.

---

