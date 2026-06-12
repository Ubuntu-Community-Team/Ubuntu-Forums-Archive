---
title: "External harddrive not detected"
date: 2010-09-08
forum: New to Ubuntu
---

### Post by UbubtuNewbie on 2010-09-08
<- Complete ubuntu amature...
im trying to move files from my hard drive to my external hard drive though a ubuntu disk because i cant boot windows. My only problem is i cant find my external hard drive anywhere on ubuntu. It dosent show up on places or 'computer'. Where else should i be looking?
 Thanks in advance;)

---

### Post by Peter09 on 2010-09-08
How is it formated? NTFS, ext3, ext4
 
If its a USB drive try the following command in a terminal
 
```

lsusb

```
 
this should list all your usb devices. Post the output here.

---

### Post by nothingspecial on 2010-09-08
Look in /media

If it`s not there go to the menu and click applications, accessories, terminal

then copy and paste

```
sudo fdisk -l
```

into it

then copy and paste the gobbldygook that comes up back here

Then do the same with this

```
dmesg | tail -n 20
```

---

### Post by UbubtuNewbie on 2010-09-08
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14946   120053713+   7  HPFS/NTFS
ubuntu@ubuntu:~$

ubuntu@ubuntu:~$ dmesg | tail -n 20
[  116.722658] lo: Disabled Privacy Extensions
[  116.722686] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  116.722688] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  116.722753] IPv6 over IPv4 tunneling driver
[  116.831501] eth2: duplicate address detected!
[  128.232814] ACPI: Power Button (FF) [PWRF]
[  128.232821] ACPI: Power Button (CM) [PWRB]
[  128.290194] ibm_acpi: ec object not found
[  128.303139] pcc_acpi: loading...
[  141.956145] lp: driver loaded but no devices found
[  141.990486] ppdev: user-space parallel port driver
[  149.627579] Bluetooth: Core ver 2.8
[  149.627584] NET: Registered protocol family 31
[  149.627585] Bluetooth: HCI device and connection manager initialized
[  149.627594] Bluetooth: HCI socket layer initialized
[  149.657118] Bluetooth: L2CAP ver 2.8
[  149.657121] Bluetooth: L2CAP socket layer initialized
[  149.913775] Bluetooth: RFCOMM socket layer initialized
[  149.913789] Bluetooth: RFCOMM TTY layer initialized
[  149.913791] Bluetooth: RFCOMM ver 1.7


And how do i work out if it  NTFS, ext3, ext4?

---

### Post by CharlesA on 2010-09-08
It's not showing up in fdisk. What kind of drive is it?

Unplug it and then plug it back in then run this:

```
dmesg | tail -n 20
```

That'll let us know if it was detected or not.

---

### Post by lavinog on 2010-09-08
Do a dmesg shortly after plugging in the drive.
It should show the usb being detected.

---

### Post by UbubtuNewbie on 2010-09-08
ubuntu@ubuntu:~$ dmesg | tail -n 20
[  116.722658] lo: Disabled Privacy Extensions
[  116.722686] ADDRCONF(NETDEV_UP): eth0: link is not ready
[  116.722688] ADDRCONF(NETDEV_UP): eth1: link is not ready
[  116.722753] IPv6 over IPv4 tunneling driver
[  116.831501] eth2: duplicate address detected!
[  128.232814] ACPI: Power Button (FF) [PWRF]
[  128.232821] ACPI: Power Button (CM) [PWRB]
[  128.290194] ibm_acpi: ec object not found
[  128.303139] pcc_acpi: loading...
[  141.956145] lp: driver loaded but no devices found
[  141.990486] ppdev: user-space parallel port driver
[  149.627579] Bluetooth: Core ver 2.8
[  149.627584] NET: Registered protocol family 31
[  149.627585] Bluetooth: HCI device and connection manager initialized
[  149.627594] Bluetooth: HCI socket layer initialized
[  149.657118] Bluetooth: L2CAP ver 2.8
[  149.657121] Bluetooth: L2CAP socket layer initialized
[  149.913775] Bluetooth: RFCOMM socket layer initialized
[  149.913789] Bluetooth: RFCOMM TTY layer initialized
[  149.913791] Bluetooth: RFCOMM ver 1.7

---

### Post by lavinog on 2010-09-08
It appears that it isn't being detected.
Do you have another usb device that you can test to see if that is detected, such as a flash drive, a digital camera, or mp3 player?

---

### Post by jshepherd on 2010-09-08
I had a similar problem a while ago. It turned out that the BIOS was unable to detect USB HDD. I installed Ubuntu via USB stick in the end. I know it's the BIOS because I couldn't even install Windows that way either. I've since installed an internal CD drive and installed XP and Lucid but not even XP detects the USB HDD. Mine is an HP PC btw. Sorry if that sounds negative but for some strange reason the machine will only recognize an internal drive.

---

### Post by bredman on 2010-09-08
It looks as if the USB bus is not detecting your external drive.

Does the external drive have a power connector, and are you sure it is powered on?

Some external devices do not register on the USB bus until they are fully powered-on.

---

### Post by UbubtuNewbie on 2010-09-08
This is with a camera just plugged in

ubuntu@ubuntu:~$ dmesg | tail -n 20
[ 6258.979966] scsi6 : SCSI emulation for USB Mass Storage devices
[ 6258.980070] usb-storage: device found at 6
[ 6258.980073] usbcore: registered new driver usb-storage
[ 6258.980075] usb-storage: waiting for device to settle before scanning
[ 6258.980078] USB Mass Storage support registered.
[ 6263.980983]   Vendor: OLYMPUS   Model: SP550UZ           Rev: 1.00
[ 6263.980996]   Type:   Direct-Access                      ANSI SCSI revision: 02
[ 6263.991955] SCSI device sdb: 2047815 512-byte hdwr sectors (1048 MB)
[ 6263.998943] sdb: Write Protect is off
[ 6263.998946] sdb: Mode Sense: 18 00 00 08
[ 6263.998949] sdb: assuming drive cache: write through
[ 6264.017913] SCSI device sdb: 2047815 512-byte hdwr sectors (1048 MB)
[ 6264.024901] sdb: Write Protect is off
[ 6264.024904] sdb: Mode Sense: 18 00 00 08
[ 6264.024906] sdb: assuming drive cache: write through
[ 6264.024909]  sdb: sdb1
[ 6264.038887] sd 6:0:0:0: Attached scsi removable disk sdb
[ 6264.038916] sd 6:0:0:0: Attached scsi generic sg1 type 0
[ 6264.039204] usb-storage: device scan complete
[ 6264.884559] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!

---

### Post by bredman on 2010-09-08
What this tells us is that your PC is capable of reading from a usb-storage device.

For some reason, it cannot read your external disk.

Have you tried your external disk on any other PC? There is a chance it may be faulty.

Have you tried another USB cable? There is a chance the cable is faulty.

---

### Post by UbubtuNewbie on 2010-09-08
Strange.. 0.o It worked with this cable on a different computer but i switch cable for this computer now it has detected it lol *face palm* thanks for the help :) simple fix :P

---

### Post by CharlesA on 2010-09-08
Nice. Glad it's working now. Don't forget to mark the thread as solved. :)

---

### Post by Potter117 on 2013-04-29
Hey there. I am having an external hdd problem on my ubuntu 12.04. I ran dmesg | tail -n 20 in the terminal. It is showing that I have a western digital hard drive. I have a WD digital drive that I know is failing, and I have already dtopped using it. The problem, now, is that the hdd in question is NOT my western digital. The hdd that is showing as a failing western digital is, in fact, a 500GB seagate. WTF? Please help.

---

### Post by oldos2er on 2013-04-29
[COLOR=#000000]If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.[/COLOR]

---

