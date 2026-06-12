---
title: "Cannot mount CDRW after write using wodim."
date: 2009-08-20
forum: New to Ubuntu
---

### Post by windyrij on 2009-08-20
I am wanting to use CD-Rs or -RWs for backup of data. So far, I have been able to blank a CD-RW with wodim, but cannot mount it. It looks like I am able to write a file to it, the requirement being multi-session ISO 9660. It is not essential for me to use CD-RW, just more convenient for re-use (I know about their potential unreliability). For the same reason I would avoid UDF.

If I can get it working, it will be part of a script, so that the backup can be made as automatic as possible, hence the use of the terminal.

I have referred to the Community Documentation, to get some ideas:
**_[SIZE=2][CdDvd/Burning - Community Ubuntu Documentation]("https://help.ubuntu.com/community/CdDvd/Burning")[/SIZE]_**


I give the terminal dialogues for blanking, writing a file and trying to mount it, with the dmesg tail following failure. Also the information from Device Manager about the CD drive (cdrom1).

Quote:

*Blanking CDRW*:

john@john-desktop:~$ wodim -vv dev=/dev/scd1 blank=all
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
Using libusal version 'Cdrkit-1.1.6'.
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'LG      '
Identification : 'CD-RW CED-8083B '
Revision       : '1.05'
Device seems to be: Generic mmc CD-RW.
Drive current speed: 4
Drive default speed: 4
Drive max speed    : 4
Selected speed     : 4
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1024000 = 1000 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
Drive DMA Speed: 73309 kB/s 416x CD 52x DVD
 01 00 00 01 00 00 00 00
 01 AA 01 01 00 00 00 00
Track 1 start -150
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -11635 (97:26/65)
  ATIP start of lead out: 337350 (75:00/00)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  power mult factor: 4 6
  recommended erase/write power: 3
  A1 values: 02 4C B0
  A2 values: 00 00 00
Disk type:    Phase change
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Speed set to 706 KB/s
Starting to write CD/DVD at speed   4.0 in real BLANK mode for single session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Performing OPC...
Blanking entire disk
Blanking time: 1196.330s

*Writing a file to CDRW*:

john@john-desktop:~$ wodim dev=/dev/scd1 driveropts=burnfree -v -data -tao -multi ~/backup_tmp/testgz.tar.gz
TOC Type: 1 = CD-ROM
wodim: Operation not permitted. Warning: Cannot raise RLIMIT_MEMLOCK limits.scsidev: '/dev/scd1'
devname: '/dev/scd1'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.6
Driveropts: 'burnfree'
SCSI buffer size: 64512
Device type    : Removable CD-ROM
Version        : 5
Response Format: 2
Capabilities   : 
Vendor_info    : 'LG      '
Identification : 'CD-RW CED-8083B '
Revision       : '1.05'
Device seems to be: Generic mmc CD-RW.
Using generic SCSI-3/mmc   CD-R/CD-RW driver (mmc_cdr).
Driver flags   : MMC SWABAUDIO 
Supported modes: TAO PACKET SAO SAO/R96P SAO/R96R RAW/R16 RAW/R96P RAW/R96R
Drive buf size : 1024000 = 1000 KB
Beginning DMA speed test. Set CDR_NODMATEST environment variable if device
communication breaks or freezes immediately after that.
FIFO size      : 12582912 = 12288 KB
Track 01: data   155 MB        
Total size:      178 MB (17:38.50) = 79388 sectors
Lout start:      178 MB (17:40/38) = 79388 sectors
Current Secsize: 2048
ATIP info from disk:
  Indicated writing power: 5
  Reference speed: 2
  Is not unrestricted
  Is erasable
  ATIP start of lead in:  -11635 (97:26/65)
  ATIP start of lead out: 337350 (75:00/00)
  1T speed low:  0 (reserved val  0) 1T speed high:  4
  power mult factor: 4 6
  recommended erase/write power: 3
  A1 values: 02 4C B0
  A2 values: 00 00 00
Disk type:    Phase change
Manuf. index: 3
Manufacturer: CMC Magnetics Corporation
Blocks total: 337350 Blocks current: 337350 Blocks remaining: 257962
Speed set to 706 KB/s
Starting to write CD/DVD at speed   4.0 in real TAO mode for multi session.
Last chance to quit, starting real write i   0 seconds. Operation starts.
Waiting for reader process to fill input buffer ... input buffer ready.
Performing OPC...
Starting new track at sector: 0
Track 01:  155 of  155 MB written (fifo 100%) [buf  96%]   4.1x.
WARNING: padding up to secsize.
Track 01: Total bytes read/written: 162581306/162582528 (79386 sectors).
Writing  time:  270.361s
Average write speed   3.9x.
Min drive buffer fill was 95%
Fixating...
Fixating time:   82.765s
wodim: fifo had 2561 puts and 2561 gets.
wodim: fifo was 0 times empty and 2355 times full, min fill was 97%.

*Try to mount drive:*

john@john-desktop:~$ sudo mount -t iso9660 -o umask=000 /dev/scd1 /media/cdrom1
[sudo] password for john: 
mount: block device /dev/scd1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

john@john-desktop:~$ dmesg | tail
[   76.001876] agpgart: Putting AGP V2 device at 0000:01:00.0 into 4x mode
[   78.502403] NET: Registered protocol family 10
[   78.503552] lo: Disabled Privacy Extensions
[   89.157523] eth0: no IPv6 routers present
[ 1723.247979] UDF-fs: No VRS found
[ 1723.284814] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1723.287615] ISOFS: changing to secondary root
[ 1854.031108] UDF-fs: No VRS found
[ 1854.058373] ISO 9660 Extensions: Microsoft Joliet Level 3
[ 1854.061289] ISOFS: changing to secondary root
john@john-desktop:~$ 

Quote ends.

S*ummary from Device Manager:Optical Drive*

Model:                        CD-RW CED 8083B
Vedor:                        LG
Device File:                 /dev/scd1
Firmware Version:      1.0
Connection Bus:          SCSI
Connection Type:        Internal
Removable Media:        Yes (ejectable)
Media Compatibility     CD-ROM/CD-RW
Max Read Speed:          37x (45.16 MBps)
Max Write Speed:         4x (5.65 MBps)
Media Capacity:           155.1 MB (162,586,624 bytes)
Partitioning:                 -

Can anyone tell me where I am going wrong, or a better method, using the terminal.

Thank you very much,     John

---

### Post by MrWES on 2009-08-20
can you post your /etc/fstab or at least the entry for the cdrom drive?

Bill

---

### Post by mikechant on 2009-08-21
Is it possible you need to fixate (-fix option) the disc in order for it to be mountable?

---

### Post by windyrij on 2009-08-21
Thanks for getting back so quickly, MrWES and mikechant:

mrWES:

 all of fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f423ebfa-9690-4173-87ef-515ac261b5d6 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda4
UUID=c5d1d305-9a4a-f0a7-edf0-aa1dad37e1f5 none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0


I note that scd1 is mounted on /media/cdrom0. Uh??
-----------------------------

mikechant:

at the end of the write process:-

Performing OPC...
Starting new track at sector: 0
Track 01:  155 of  155 MB written (fifo 100%) [buf  96%]   4.1x.
WARNING: padding up to secsize.
Track 01: Total bytes read/written: 162581306/162582528 (79386 sectors).
Writing  time:  270.361s
Average write speed   3.9x.
Min drive buffer fill was 95%
Fixating...
Fixating time:   82.765s
wodim: fifo had 2561 puts and 2561 gets.
wodim: fifo was 0 times empty and 2355 times full, min fill was 97%.

-------------------------

Regards,          John

---

