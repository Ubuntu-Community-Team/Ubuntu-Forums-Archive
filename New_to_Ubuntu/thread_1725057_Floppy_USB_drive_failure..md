---
title: "Floppy USB drive failure."
date: 2011-04-09
forum: New to Ubuntu
---

### Post by machdohvah on 2011-04-09
I am having problems mounting the floppy USB drive. "Places ->  Computer" sees an icon labelled "Floppy Drive", but it cannot see any  files on the disk. "System -> Administration -> Disk Utility" sees  "Floppy Drive" with "Connection: USB at 12mb/sec". The thing that is  different is that the last screen mentioned also sees "Device: /dev/sdb"  with "Capacity: No media detected". I am new at this and cannot figure  out how capture a screen shot of the Drive Utility page. While back at  "Paces -> Computer -> Floppy Drive -> Properties" there is a  entry:"Location: Computer:///" which do not agree. What should I do?

---

### Post by f1tz on 2011-04-09
> I am new at this and cannot figure  out how capture a screen shot of the Drive Utility page.Press Print Screen and you should see KSnapshot, or something similar pop up, you can then save the image.

Having a vague stab in the dark here... When you plug the USB in, do you end up with a notification? Does it ask you to install any drivers? (Have you got a diskette in there? :P)

If not, try looking through this thread: [http://ubuntuforums.org/showthread.php?t=1066686](http://ubuntuforums.org/showthread.php?t=1066686)

---

### Post by machdohvah on 2011-04-10
> **f1tz said:**
> 
Having a vague stab in the dark here... When you plug the USB in, do you end up with a notification? Does it ask you to install any drivers? (Have you got a diskette in there?)

If not, try looking through this thread: [http://ubuntuforums.org/showthread.php?t=1066686](http://ubuntuforums.org/showthread.php?t=1066686)


There is no notification. And, no, it does not ask me to install any drivers. Of course I have the disk in the thing.

I have looked at the above listing. I have over 35 years of computer experience in general and would like to keep the professionalism of this inquire a little higher than you give me credit. The problem is that I have been bereft of all my coding capabilities ever since DOS became obsolete. No, I am not published, just retired like many others.

I looked at lsusb -v: (only the section pertaining to the USB Floppy)

```

Bus 004 Device 002: ID 03ee:6901 Mitsumi SmartDisk FDD
Device Descriptor:
  bLength                18
  bDescriptorType         1
  bcdUSB               1.10
  bDeviceClass            0 (Defined at Interface level)
  bDeviceSubClass         0 
  bDeviceProtocol         0 
  bMaxPacketSize0        64
  idVendor           0x03ee Mitsumi
  idProduct          0x6901 SmartDisk FDD
  bcdDevice            2.00
  iManufacturer           1 MITSUMI
  iProduct                2 MITSUMI USB FDD 061M
  iSerial                 0 
  bNumConfigurations      1
  Configuration Descriptor:
    bLength                 9
    bDescriptorType         2
    wTotalLength           39
    bNumInterfaces          1
    bConfigurationValue     1
    iConfiguration          0 
    bmAttributes         0x80
      (Bus Powered)
    MaxPower              500mA
    Interface Descriptor:
      bLength                 9
      bDescriptorType         4
      bInterfaceNumber        0
      bAlternateSetting       0
      bNumEndpoints           3
      bInterfaceClass         8 Mass Storage
      bInterfaceSubClass      4 Floppy (UFI)
      bInterfaceProtocol      0 Control/Bulk/Interrupt
      iInterface              0 
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x82  EP 2 IN
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x01  EP 1 OUT
        bmAttributes            2
          Transfer Type            Bulk
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0040  1x 64 bytes
        bInterval               0
      Endpoint Descriptor:
        bLength                 7
        bDescriptorType         5
        bEndpointAddress     0x83  EP 3 IN
        bmAttributes            3
          Transfer Type            Interrupt
          Synch Type               None
          Usage Type               Data
        wMaxPacketSize     0x0002  1x 2 bytes
        bInterval             127
Device Status:     0x0001
  Self Powered

```Waiting for someone to truly help me with this problem. I need access to my disks.

Hopefully, when I install Ubuntu 11.04 (beta) this problem will be solved.

---

### Post by JKyleOKC on 2011-04-10
> **machdohvah said:**
> I have over 35 years of computer experience in general and would like to keep the professionalism of this inquire a little higher than you give me credit.

...

Waiting for someone to truly help me with this problem. I need access to my disks.

Hopefully, when I install Ubuntu 11.04 (beta) this problem will be solved.When we see an initial posting, especially in this forum, we have no way of knowing the poster's experience level, and so we tend to start out at the lowest common denominator. Since you have extensive experience with MS-DOS, it'll be easier to help you!

Linux, unlike MS-DOS, has a clear distinction between the data physically stored on the disk, and that same data as it exists in RAM where the system can deal with it. In MS-DOS, it would have been like differentiating between the disk data and the buffer in which it's stored. MS-DOS hid the distinction, but Linux requires that explicit action be taken to move the data between the two areas. That's done by the "mount" and "umount" commands. At boot time, some drives are mounted automatically in defined directories (mount points) but others can be added later.

My initial guess, since your listing from lspci shows the drive's attributes, is that the device is being detected properly but is not being mounted. To confirm this you can issue the "mount" command by itself to get a list of all mounted devices. First, though, use the command "sudo fdisk -l" (that's lower-case L, not the numeral 1) to get a listing of all detected devices. One of those listed should be the floppy, with a name similar to either "/dev/fd?" or "/dev/usb?" where the "?" is a numeral, probably 0. Then look for that same name in the results from "mount" -- it probably will not be there.

Post the results of both commands and we'll be able to tell you how to add the device to the automount listing. And don't be too disappointed if the move to 11.04 makes no difference at all. Use of floppies is so rare these days that many of the newer kids on the block don't even seem to know that they exist!

BTW, if you remember a book from the early 90s called "Undocumented DOS," you may recognize my name. It's good to see another veteran of those days and before!

---

### Post by machdohvah on 2011-04-10
Here is the result of sudo fdisk -l:
```
root@michael-A770E3:/home/michael# sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000acea9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      119785   962170880   83  Linux
/dev/sda2          119785      121602    14588929    5  Extended
/dev/sda5          119785      121602    14588928   82  Linux swap / Solaris

Disk /dev/sdb: 0 MB, 737280 bytes
1 heads, 2 sectors/track, 720 cylinders
Units = cylinders of 2 * 512 = 1024 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7369440a

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?   850999991  1463369661   612369670+  20  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(372, 111, 47) logical=(850999990, 0, 1)
Partition 1 has different physical/logical endings:
     phys=(361, 102, 33) logical=(1463369660, 0, 1)
Partition 1 does not end on cylinder boundary.
/dev/sdb2   ?   556050088  1254901966   698851878+  4f  QNX4.x 3rd part
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(329, 77, 2) logical=(556050087, 0, 2)
Partition 2 has different physical/logical endings:
     phys=(67, 32, 32) logical=(1254901965, 0, 2)
Partition 2 does not end on cylinder boundary.
/dev/sdb3   ?           1           1           0   4d  QNX4.x
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(335, 32, 3) logical=(0, 0, 1)
Partition 3 has different physical/logical endings:
     phys=(0, 0, 0) logical=(2147483647, 0, 2)
Partition 3 does not end on cylinder boundary.

Partition table entries are not in disk order

```

Here is the result of mount:
```
root@michael-A770E3:/home/michael# mount
/dev/sda1 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/michael/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=michael)

```

---

### Post by JKyleOKC on 2011-04-10
Great! Your floppy is /deb/sdb and since floppies do not have partition tables, the error message and partition information for it are meaningless; they don't indicate any serious problem.

However, it's a puzzlement as to why the system is detecting the floppy as a SCSI drive (the "sd" prefix in the assigned device name) and this is probably why it's not mounting.

Try unplugging the USB cable and rebooting, to make sure that the system doesn't detect any "/dev/sdb" device, then plug in the USB cable and see whether the drive shows up within a minute or so. I've had to do this with some devices; the auto-detection code that runs at boot time is a bit different from the hot-swap USB code that runs when a new device gets plugged in, and that sometimes makes a world of difference.

If it doesn't, try these commands in a terminal window, with the USB cable plugged in: ```
sudo mkdir /media/floppy
sudo mount -t msdos /dev/sdb /media/floppy
```Once the /media/floppy directory gets created you don't need to run mkdir again, of course. Hopefully this should make the floppy's files available in the /media/floppy directory, although you probably won't be able to write to them because of permissions conflicts. We can handle that with automounting code, if this works to give you access, but first let's find out which approach works best...

Hopefully a few others will pitch in here with ideas as to why the floppy is being detected as SCSI (or at least as a hard disk, since recent releases of Ubuntu have treated all hard disks as SCSI). Once that is cleared up, the floppy details can be added to the /etc/fstab file and you should be in good shape.

---

### Post by machdohvah on 2011-04-10
> **JKyleOKC said:**
> Try unplugging the USB cable and rebooting, to make sure that the system doesn't detect any "/dev/sdb" device, then plug in the USB cable and see whether the drive shows up within a minute or so. I've had to do this with some devices; the auto-detection code that runs at boot time is a bit different from the hot-swap USB code that runs when a new device gets plugged in, and that sometimes makes a world of difference.

I have done this and, yes, the icon shows up as Floppy Drive (see first detailed post). This icon points to "computer:///", but the "Disk Utility" reports that it is connected to "/dev/sdb".

---

### Post by JKyleOKC on 2011-04-10
I've asked for help from a file system guru and hopefully he'll drop in soon.

I think it's possible to force the drive to be detected properly, by creating a rule for the automount code (udev); I have to do this to make my network cards behave properly. However before I offer possibly bad advice on how to do it, I prefer to get another opinion!

---

### Post by f1tz on 2011-04-12
> I have over 35 years of computer experience in general and would like to  keep the professionalism of this inquire a little higher than you give  me credit.

I'm very sorry if I came across as unhelpful or patronising, this wasn't intended in the slightest. Hopefully JKyleOKC's filesystem guru will help solve this!

---

### Post by warsev on 2011-09-25
I got a nice, new, cheap Mitsumi USB floppy for reading old disks and quickly found I had this exact same problem. After a day or so of messing around I found a good fix. The solution is to tell udev that the device _**isn't**_ a floppy!! (go figure...) That's done by overriding the environment variable "ID_DRIVE_FLOPPY" from "1", which is set in the general rule, to "0". A custom udev rule is necessary to override the generic rule for USB floppies that's in /lib/udev/rules.d/80-udisks.rules. In this case I chose to make a custom rule that would only apply to my specific disk vendor and model, leaving all others to be handled generically. The rule looks like so:
```
# This should run AFTER the general rule in /lib/udev/rules.d that deals with generic usb floppys
ATTRS{vendor}=="MITSUMI*", ATTRS{model}=="USB UFDD 061M*", GROUP="floppy", ENV{ID_DRIVE_FLOPPY}="0"
```Upon stopping and restarting udev, it works perfectly, almost. When a floppy is inserted into the drive it is mounted and a file browser opens to the disk root. The only flaw is that the "Eject" option in some pull-down lists unmounts the disk but doesn't actually eject it. I have to manually press the button on the drive to eject the disk. (heck, I can live with that...)

To find the vendor and model of your disk drive, first determine where in the device tree it's being loaded. Probably /dev/sdb or /dev/sdc. You can do that rather simply by just disconnecting the disk, looking at the /dev directory, connecting the disk, and looking at /dev again. Next, you can find many particulars suitable for use in udev rules. At a terminal type:
```
udevadm info -a -p `udevadm info -q path -n /dev/sdc`
```You will get a long list of parameters and variables for the device and its parent devices. Somewhere you will find the vendor and model of the disk, like so:
```
    ATTRS{vendor}=="MITSUMI "
    ATTRS{model}=="USB UFDD 061M   "
```Plug those values into the rule as above to uniquely identify your drive.

Hints:

[LIST]
[*]Put your custom rule into /etc/udev/rules.d/, not /lib/udev/rules.d/ if you want it to survive your next OS upgrade.
[*]Make sure the file name of your custom rule ends in ".rules" and collates after the name of the general rule (at this writing, "80-udisks.rules").
[*]Make sure the permissions on your custom rule match the permissions of the other custom rules you find in /etc/udev/rules.d
[*]Make sure you user name has access to group "floppy"
[/LIST]

---

### Post by lkraemer on 2011-09-25
machdohvah,
I had saved this information during my install of Ubuntu 10.04.  It was somewhere on the forum.
Maybe it will be of help for you.

PROBLEM:  Can't mount Floppy in 10.04 LTS

To summarize, reading (and writing) a floppy disk in Lucid Lynx (10.04) requires three steps:

1. Allow yourself to use the floppy by going to System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

2. Use the old version of udisks () by going to System->Administration->Synaptic Package Manager, find the udisks package, mark udisks for reinstallation, click on Package->Force Version, and select the 1.0.1-1build1 version (which is the old version). Then click on apply to finish the installation.

3. Remember to unclick udisks whenever Update Manager wants to install new updates, or you'll get the new version and floppy disks won't work anymore!

After the old udisks is installed (and the machine is rebooted), when you insert a floppy a cute little icon comes up on the desktop and in Nautilus (and on Disk Mounter if you have that installed). Left clicking on the icon and select Mount Floppy Disk will put an icon in Nautilus, and then you read, write, and format the floppy just like any other drive.


Finally found it:
[http://ubuntuforums.org/showthread.php?t=1772291&highlight=Can%27t+mount+Floppy](http://ubuntuforums.org/showthread.php?t=1772291&highlight=Can%27t+mount+Floppy)
Posting #10


LK

---

### Post by tb2012 on 2011-11-24
Is there also a solution for 10.10 (Maverick)? Because the "force version" option in synaptics is greyed out :(

[COLOR=Red]***[EDIT & SOLVED]***[/COLOR]

Under Ubuntu 10.10. Maverick I used:
- 1. Allow yourself to use the floppy by going to 
System->Administration->Users and Groups->Advanced Settings->User Privileges and click on "Use floppy drives"

- 2. Download 1.0.1-1build1  from here:
[https://launchpad.net/ubuntu/+source/udisks](https://launchpad.net/ubuntu/+source/udisks)
Select the 1.0.1-1build1 and download your processor version; example
for 32bit:

- 3. In Maveric: open a terminal cd (go) to the download (folder) &:
$ sudo dpkg -i udisks_1.0.1-1build1_i386.deb

- 4. reboot

If and which side effects this downgrade has/will have on other programs, is not known yet ;)

---

### Post by cthlhu1987 on 2012-11-06
> **warsev said:**
> I got a nice, new, cheap Mitsumi USB floppy for reading old disks and quickly found I had this exact same problem. After a day or so of messing around I found a good fix. The solution is to tell udev that the device _**isn't**_ a floppy!! (go figure...) That's done by overriding the environment variable "ID_DRIVE_FLOPPY" from "1", which is set in the general rule, to "0". A custom udev rule is necessary to override the generic rule for USB floppies that's in /lib/udev/rules.d/80-udisks.rules. In this case I chose to make a custom rule that would only apply to my specific disk vendor and model, leaving all others to be handled generically. The rule looks like so:
```
# This should run AFTER the general rule in /lib/udev/rules.d that deals with generic usb floppys
ATTRS{vendor}=="MITSUMI*", ATTRS{model}=="USB UFDD 061M*", GROUP="floppy", ENV{ID_DRIVE_FLOPPY}="0"
```Upon stopping and restarting udev, it works perfectly, almost. When a floppy is inserted into the drive it is mounted and a file browser opens to the disk root. The only flaw is that the "Eject" option in some pull-down lists unmounts the disk but doesn't actually eject it. I have to manually press the button on the drive to eject the disk. (heck, I can live with that...)

To find the vendor and model of your disk drive, first determine where in the device tree it's being loaded. Probably /dev/sdb or /dev/sdc. You can do that rather simply by just disconnecting the disk, looking at the /dev directory, connecting the disk, and looking at /dev again. Next, you can find many particulars suitable for use in udev rules. At a terminal type:
```
udevadm info -a -p `udevadm info -q path -n /dev/sdc`
```You will get a long list of parameters and variables for the device and its parent devices. Somewhere you will find the vendor and model of the disk, like so:
```
    ATTRS{vendor}=="MITSUMI "
    ATTRS{model}=="USB UFDD 061M   "
```Plug those values into the rule as above to uniquely identify your drive.

Hints:

[LIST]
[*]Put your custom rule into /etc/udev/rules.d/, not /lib/udev/rules.d/ if you want it to survive your next OS upgrade.
[*]Make sure the file name of your custom rule ends in ".rules" and collates after the name of the general rule (at this writing, "80-udisks.rules").
[*]Make sure the permissions on your custom rule match the permissions of the other custom rules you find in /etc/udev/rules.d
[*]Make sure you user name has access to group "floppy"
[/LIST]
Thx, it worked!!! :guitar::guitar::guitar:

---

