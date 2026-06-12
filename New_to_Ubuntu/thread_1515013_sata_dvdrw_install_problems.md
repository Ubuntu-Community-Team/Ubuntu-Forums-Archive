---
title: "sata dvdrw install problems"
date: 2010-06-21
forum: New to Ubuntu
---

### Post by distorted on 2010-06-21
My specs/system is here: 

CPUs: 8
CPU Model Name: Intel(R) Core(TM) i7 CPU @ 9200 @ 2.67GHz
Frequency: 1596.000 MHz
L2 cache: 8192 KB

Release: Ubuntu 10.04 (lucid)
GNOME 2.30.0
Kernel 2.6.32-22-generic

(New DVD-RW)
SCSi device scsi0
vendor optiarc
model dvd rw ad-7241s

(Old DVD-R)
SCSi device scsi0
vendor ATAPI
model ihas324 a

Anymore issues or problems, I will answer you ASAP. My SATA jacks are different because I needed to install my new DVD-RW drive. Thus, 3 SATA jacks, not 2 now. 
:~$ dev/scsi0
bash: dev/scsi0: No such file or directory
:~$ dev/cdrom0
bash: dev/cdrom0: No such file or directory

What's the problem, now? My DVD-RW is not recognize my ifuse anymore and my dvd drives are slow, too. 

Thanks, in advance.

---

### Post by wesleybishop on 2010-06-21
hey do not know much about your issue or how to help but maybe this link might help [http://ubuntuforums.org/showthread.php?t=836894](http://ubuntuforums.org/showthread.php?t=836894) good luck :)

---

### Post by distorted on 2010-06-21
I need help, it was totally separate for the old message.

  	 	 	 	 	 	  *In addition to "dmesg", I would try the command "lshw" to see if the drive is present.*
 

 -cdrom:0
                 description: DVD-RAM writer
                 product: DVD RW AD-7241S
                 vendor: Optiarc
                 physical id: 0.0.0
                 bus info: scsi@0:0.0.0
                 logical name: /dev/cdrom1
                 logical name: /dev/cdrw1
                 logical name: /dev/dvd1
                 logical name: /dev/dvdrw1
                 logical name: /dev/scd0
                 logical name: /dev/sr0
                 version: 1.03
                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                 configuration: ansiversion=5 status=ready
               *-medium
                    physical id: 0
                    logical name: /dev/cdrom1
            *-cdrom:1
                 description: DVD-RAM writer
                 product: iHAS324   A
                 vendor: ATAPI
                 physical id: 0.1.0
                 bus info: scsi@0:0.1.0
                 logical name: /dev/cdrom
                 logical name: /dev/cdrw
                 logical name: /dev/dvd
                 logical name: /dev/dvdrw
                 logical name: /dev/scd1
                 logical name: /dev/sr1
                 version: BL1H
                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                 configuration: ansiversion=5 status=ready
               *-medium
                    physical id: 0
                    logical name: /dev/cdrom
 *In addition to "dmesg", I would try the command "lshw" to see if the drive is present.*
 

 -cdrom:0
                 description: DVD-RAM writer
                 product: DVD RW AD-7241S
                 vendor: Optiarc
                 physical id: 0.0.0
                 bus info: scsi@0:0.0.0
                 logical name: /dev/cdrom1
                 logical name: /dev/cdrw1
                 logical name: /dev/dvd1
                 logical name: /dev/dvdrw1
                 logical name: /dev/scd0
                 logical name: /dev/sr0
                 version: 1.03
                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                 configuration: ansiversion=5 status=ready
               *-medium
                    physical id: 0
                    logical name: /dev/cdrom1
            *-cdrom:1
                 description: DVD-RAM writer
                 product: iHAS324   A
                 vendor: ATAPI
                 physical id: 0.1.0
                 bus info: scsi@0:0.1.0
                 logical name: /dev/cdrom
                 logical name: /dev/cdrw
                 logical name: /dev/dvd
                 logical name: /dev/dvdrw
                 logical name: /dev/scd1
                 logical name: /dev/sr1
                 version: BL1H
                 capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                 configuration: ansiversion=5 status=ready
               *-medium
                    physical id: 0
                    logical name: /dev/cdrom
 

 

 [I]Does your BIOS list the DVD drive and is it seen on your POST screen?
 [/I]
 BIOS: SOX5810J.86A.2127.2008.0914.1638
 SATA PORT 0: OPTIARC DVD RW A-ATAPI (NEW DVD RW)
 SATA PORT 2: ATAPI IH BS324 ATAPI (OLD DVD RW)
 SATA PORT 4: 1000.2 GB (HARD DRIVE)
 SATA 1,3, 5 ARE NOT INSTALLED
 

 POST:GRUB LOADER
 MANY I/O ERRORS. (20-25 ERRORS)
 

 I will try the live-CD after my thread.


Could not open the location: “cdda://sr1/'
 Failed to execute child process "sound-juicer" (No such file or directory)
 
Thanks again.

---

