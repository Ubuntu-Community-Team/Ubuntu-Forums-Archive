---
title: "HP photosmart camera read error"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by miscellanyous on 2009-02-01
I can't get Kubunutu to read an HP photosmart M417 camera. Upon turning it on the camera is found and mounted as USB mass storage interface. Here are some attempts at a solution so far:

1)  [I]popup window --> "A new medium has been detected ..." --> select "Open in new window"
Dolphin --> "unknown error code 50 \n Unspecified error"[/I]

2)  *digiKam --> autodetect camera --> detected as HP photosmart M407 (PTP mode) --> "Failed to connect to camera ..."*

The most up to date bug report on a digital camera (may or may not be relevant) is [this one]("https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/267238"). Here is the output requested in that bug report:
```
chris@csHome:~$ ck-list-sessions
Session1:
        uid = '1000'
        realname = 'chris s,,,'
        seat = 'Seat1'
        session-type = ''
        active = TRUE
        x11-display = ':0'
        x11-display-device = '/dev/tty7'
        display-device = ''
        remote-host-name = ''
        is-local = TRUE
        on-since = '2009-02-01T23:17:26Z
```
The entry for the camera is in /dev/bus/usb/002/007
```
chris@csHome:/dev/bus/usb/002$ getfacl /dev/bus/usb/002/007
getfacl: Removing leading '/' from absolute path names
# file: dev/bus/usb/002/007
# owner: lp
# group: scanner
user::rw-
user:chris:rw-
group::rw-
mask::rw-
other::---
```

Well, its not a scanner and I don't know who 'lp' is... 
My system: Kubuntu 8.04 (I think), KDE 3.5.10
relevant packages installed: kamera, libgphoto2-2, libgphoto2-port0, libgphoto2-2-dev

---

### Post by miscellanyous on 2009-02-02
Oddly, I found there are no problems reading the camera, transferring and deleting pictures via 'fspot' photomanager in the GNOME desktop (running on a different machine). So it appears this error is a problem with KDE. I will post a bug report... still no solution.

---

### Post by miscellanyous on 2009-02-02
continuing with the monologue, following the advice at the [digiKam FAQ]("http://www.digikam.org/docs.html#q3") I fail once again. The folder /proc/sys/usb/ does not contain the directory /devices, in fact /proc/sys/usb/ is empty. Listing the SCSI devices yields
```
chris@csHome:~$ sudo sg_scan -i
/dev/sg0: scsi0 channel=0 id=0 lun=0 [em]
    ATA       Maxtor 2B020H1    WAH2 [rmb=0 cmdq=0 pqual=0 pdev=0x0]
/dev/sg1: scsi0 channel=0 id=1 lun=0 [em]
    ATA       WDC WD800JB-00JJ  05.0 [rmb=0 cmdq=0 pqual=0 pdev=0x0]
/dev/sg2: scsi1 channel=0 id=0 lun=0 [em]
    SAMSUNG   CD-ROM SC-148C    C002 [rmb=1 cmdq=0 pqual=0 pdev=0x5]
```
Well, none of these is my camera. The link above also suggests tinkering with the kernel which I am **not** going to do. I mean, people have been using cameras with kubuntu for a few years right?

---

### Post by miscellanyous on 2009-03-07
:redface: After hunting around some more, I think the problem (and solution) are with the camera hardware, not KDE. In the camera settings menu (found on the camera itself), one can switch the USB behaviour between "Digital camera" and "Disk drive". After switching this value to "Digital Camera", the errors have disappeared! Images transfer successfully using file manager and digiKam.

To check the USB devices connected at any time:
```
chris@csHome:~$ lsusb
Bus 002 Device 011: ID 03f0:7802 Hewlett-Packard
Bus 002 Device 003: ID 04e8:3268 Samsung Electronics Co., Ltd ML-1610 Mono Laser Printer
Bus 002 Device 002: ID 05e3:0605 Genesys Logic, Inc. USB 2.0 Hub [ednet]
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 413c:2001 Dell Computer Corp.
Bus 001 Device 003: ID 413c:1001 Dell Computer Corp.
Bus 001 Device 002: ID 046d:c002 Logitech, Inc. M-BA47 [MouseMan Plus]
Bus 001 Device 001: ID 0000:0000
```
I believe this shows the mount point of the camera is /dev/bus/usb/002/011. Then check the debug log:
```
chris@csHome:~$ dmesg
...
[ 5509.338894] usb 2-1.2: new full speed USB device using uhci_hcd and address 11
[ 5509.555889] usb 2-1.2: configuration #1 chosen from 1 choice
```

---

