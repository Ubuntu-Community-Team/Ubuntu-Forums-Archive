---
title: "usb drive not recognized in fdisk"
date: 2010-10-01
forum: New to Ubuntu
---

### Post by icoben on 2010-10-01
I upgraded to ubuntu 10.04.
After that, the system cannot recognize the usb drive.
It shows in lsusb, but not in fdisk.
It appears the system does not give a name (sdb1, sdb2...) to the usb drive.

here is the info..

```
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 059f:0341 LaCie, Ltd 
Bus 001 Device 002: ID 413c:8104 Dell Computer Corp. Wireless 1450 Dual-band (802.11a/b/g) USB2.0 Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
[  225.673184] usb 1-5: configuration #1 chosen from 1 choice
[  410.822799] usb 1-5: USB disconnect, address 5
[  416.820038] usb 1-5: new high speed USB device using ehci_hcd and address 6
[  416.953063] usb 1-5: configuration #1 chosen from 1 choice
[  900.144800] usb 1-5: USB disconnect, address 6
[  905.968036] usb 1-6: new high speed USB device using ehci_hcd and address 7
[  906.101735] usb 1-6: configuration #1 chosen from 1 choice
[12473.842593] usb 1-6: USB disconnect, address 7
[12516.432029] usb 1-6: new high speed USB device using ehci_hcd and address 8
[12516.565714] usb 1-6: configuration #1 chosen from 1 choice

``````
Disk /dev/sda: 40.0 GB, 40027029504 bytes
255 heads, 63 sectors/track, 4866 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xab68ab68

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4796    38523838+  83  Linux
/dev/sda2            4797        4866      562275   82  Linux swap / Solaris

```

---

### Post by cariboo on 2010-10-01
How is the external drive formatted? If it's NTFS, it may be suffering from an unclean shutdown.

---

### Post by srs5694 on 2010-10-02
An unclean filesystem shutdown could not account for the lack of a device filename for the whole disk or even for the partition.

I recommend unplugging the disk, typing "dmesg | tail", plugging the disk back in, waiting a minute or so, and typing "dmesg | tail -n 20". Any new lines between the two dmesg outputs reflect kernel actions related to plugging the disk in. Such messages may be diagnostic.

My initial suspicion is that the drive's interface, or perhaps its cable, is bad, and that the upgrade to 10.04 just coincidentally happened at the same time as the hardware failure. That's just a suspicion, though. You could test it by trying the disk on another computer and/or by using an emergency disc (say, your previous Ubuntu's installer in live CD mode) on the same computer.

---

### Post by coffeecat on 2010-10-02
I noticed this:

> **icoben said:**
> Bus 001 Device 008: ID 059f:0341 LaCie, Ltd 

On a certain Mac forum I sometimes follow, LaCies have acquired a bad reputation because of premature failures of the power supply. LaCie drives are, or were, popular with Mac owners. I do not know whether this reputation is fair or whether LaCie's power supplies are more or less reliable than other manufacturers. My only (indirect) experience of this is with a Mac-owing friend who asked for my help with their non-functional LaCie USB drive. Yes, you've guessed it - the power supply had failed.

I can't remember whether the failure was total, or whether there was enough power to give the impression something was working. Whatever, have you tried this drive in another computer and/or OS? Do you have another LaCie whose power supply you could try?

---

### Post by RJ12 on 2010-10-02
I had this problem. Seemed that the Kernel was not loading the usb_storage module during startup

If you could unplug the drive and run the following command ```
sudo modprobe usb_storage
``` give it your password (it looks as if it isn't typing, but it is :)) and then plug in the drive. Does it start working?

---

### Post by icoben on 2010-10-03
Thanks RJ12 !!!
The usb drive showed up after that command.

It seems I need to run the command every time after the system restarts.
If the usb was plugged before the system starts, it will show up.

Is there a way to do it automatically??

---

### Post by RJ12 on 2010-10-03
> **icoben said:**
> Thanks RJ12 !!!
The usb drive showed up after that command.

It seems I need to run the command every time after the system restarts.
If the usb was plugged before the system starts, it will show up.

Is there a way to do it automatically??

No problem, I had that exact problem.

To have it do it by itself

Open a terminal and type the following command

```
sudo gedit /etc/modules
```

Then The text editor will open and on a new line type usb_storage and then save and close the file. It should then do it automatically on boot up

Glad I could help!:)

 :P

---

