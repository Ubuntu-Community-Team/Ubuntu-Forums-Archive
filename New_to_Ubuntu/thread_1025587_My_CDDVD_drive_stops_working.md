---
title: "My CD/DVD drive stops working"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by amitlinux on 2008-12-30
I have ubuntu 8.10 and it seems to be working fine, with one large exception. My DVD/CD rom drive stops working after usually 5-10 minutes. It will detect the cd at boot and for a few minutes, then it hangs. If there was a CD in the drive, the icon stays on the desktop even after removing the disk. 
Here is the output to dmesg|tail
[ 3735.488401] ata1.00: configured for PIO0
[ 3735.488415] ata1: EH complete
[ 3765.488059] ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen
[ 3765.488073] ata1.00: cmd a0/00:00:00:00:00/00:00:00:00:00/a0 tag 0
[ 3765.488077]          cdb 00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00
[ 3765.488081]          res 40/00:03:00:00:00/00:00:00:00:00/a0 Emask 0x4 (timeout)
[ 3765.488088] ata1.00: status: { DRDY }
[ 3765.488108] ata1: soft resetting link
[ 3765.668370] ata1.00: configured for PIO0
[ 3765.668383] ata1: EH complete

and here my /etc/fstab

proc            /proc           proc    defaults        0       0
UUID=47a3e6b5-438d-446a-8e81-674567cd035b /               ext3    relatime,errors=remount-ro 0       1
UUID=56627c13-cae5-4d57-8ccc-34b4488d9321 none            swap    sw              0       0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

I have tried manually mounting the drive w/o success. Thank you for any help you can provide.

---

### Post by amitlinux on 2008-12-30
Also, I forgot to add that the CD-rom is an IDE and the hard drive is SATA. Thanks

---

### Post by Michael.Godawski on 2008-12-30
hi, 

can you please post the output from:
```
sudo lshw -C disk
```

---

### Post by amitlinux on 2008-12-30
Thanks

I tried the command and it just stops on SCSI

---

