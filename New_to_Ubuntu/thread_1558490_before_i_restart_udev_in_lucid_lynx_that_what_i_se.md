---
title: "before i restart udev in lucid lynx that what i see"
date: 2010-08-22
forum: New to Ubuntu
---

### Post by cool Cpu on 2010-08-22
cpu 35% !!!! without even starting any app or firefox 

it is issue with optiarc dvd or cdroom and i need some advice maybe how to switch dvd permanently off. 

the output i get before i restart udev :

ID_CDROM=1
ID_CDROM_CD_R=1
ID_CDROM_CD_RW=1
ID_CDROM_DVD=1
ID_CDROM_DVD_R=1
ID_CDROM_DVD_RW=1
ID_CDROM_DVD_RAM=1
ID_CDROM_DVD_PLUS_R=1
ID_CDROM_DVD_PLUS_RW=1
ID_CDROM_DVD_PLUS_R_DL=1
ID_CDROM_MRW=1
ID_CDROM_MRW_W=1
ID_SCSI=1
ID_VENDOR=Optiarc
ID_VENDOR_ENC=Optiarc\x20
ID_MODEL=DVD_RW_AD-7560S
ID_MODEL_ENC=DVD\x20RW\x20AD-7560S\x20
ID_REVISION=SX01
ID_TYPE=cd
ID_BUS=scsi
ID_PATH=pci-0000:00:1f.2-scsi-4:0:0:0
ACL_MANAGE=1
GENERATED=1
UDISKS_PRESENTATION_NOPOLICY=0
MAJOR=11
MINOR=0
DEVLINKS=/dev/block/11:0 /dev/scd0 /dev/disk/by-path/pci-0000:00:1f.2-scsi-4:0:0:0 /dev/cdrom /dev/cdrw /dev/dvd /dev/dvdrw

KERNEL[1282489526.420743] change   /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0 (scsi)
UDEV_LOG=3
ACTION=change
DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0
SUBSYSTEM=scsi
SDEV_MEDIA_CHANGE=1
DEVTYPE=scsi_device
DRIVER=sr
MODALIAS=scsi:t-0x05
SEQNUM=3110

KERNEL[1282489526.420937] change   /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sr0 (block)
UDEV_LOG=3
ACTION=change
DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sr0
SUBSYSTEM=block
DEVNAME=sr0
DEVTYPE=disk
SEQNUM=3111
MAJOR=11
MINOR=0

UDEV  [1282489526.421066] change   /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0 (scsi)
UDEV_LOG=3
ACTION=change
DEVPATH=/devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0
SUBSYSTEM=scsi
SDEV_MEDIA_CHANGE=1
DEVTYPE=scsi_device
DRIVER=sr
MODALIAS=scsi:t-0x05




UDEV  [1282489552.633890] change   /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sr0 (block)
KERNEL[1282489552.635087] change   /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0 (scsi)
KERNEL[1282489552.635530] change   /devices/pci0000:00/0000:00:1f.2/host4/target4:0:0/4:0:0:0/block/sr0 (block)
etc etc etc
etc etc etc

drecord -scanbus
scsibus4:
    4,0,0    400) 'Optiarc ' 'DVD RW AD-7560S ' 'SX01' Removable CD-ROM

Linux microsoft 2.6.32-24-generic #41-Ubuntu SMP Thu Aug 19 01:12:52 UTC 2010 i686 GNU/Linux

i would like to know if there is anything i could do to sort out this problem out?

ahh and after i restart or stop  udev cpu is down to 1% but i dont want everytime i boot up restart udev i would like to know better way of sorting it out

---

### Post by corrytonapple on 2010-08-22
Have you proved your restart theory more than once? Is it external or internal DVD player? Is it software (I assume) you are talking about or the hardware?

---

### Post by cool Cpu on 2010-08-22
> **corrytonapple said:**
> Have you proved your restart theory more than once? Is it external or internal DVD player? Is it software (I assume) you are talking about or the hardware?


it is internal dvd rw called optiarc as you can see about i think the dvd is an issue and im looking for some sort of solution better than restarting udev every time i boot up lucid

and i been looking for new firmware but there is none

---

### Post by corrytonapple on 2010-08-22
Please use proper grammar. I am having a hard time understanding you. So it is a internal DVD-RW drive and a disc is in it that you think is causing the issue? Have you proven the theory that you had to restart after shutdown multiple times? Do this: To install hardware drivers, go to the top of the screen, then to **System>Administration>Hardware Drivers**  and download and install any drivers for your DVD drive. See picture (I have no drivers to install.)

---

### Post by cool Cpu on 2010-08-22
> **corrytonapple said:**
> Please use proper grammar. I am having a hard time understanding you. So it is a internal DVD-RW drive and a disc is in it that you think is causing the issue? Have you proven the theory that you had to restart after shutdown multiple times? Do this: To install hardware drivers, go to the top of the screen, then to **System>Administration>Hardware Drivers**  and download and install any drivers for your DVD drive. See picture (I have no drivers to install.)


hehehehehe 

i have ati card so i use catalyst and i wont install open source ati driver it cuz it doesnt work. thats all i found in hardware drivers.

second as you can see from what i showed before i restart udev it pull out optirac dvd can u see it ?

after i restart udev everything is working just fine but i have to restart udev every time i boot up lucid and i don't like it.

im looking for  some better than restarting udev solution to it.


edit:

and im sorry for my english lang it is cuz im from America and i speak American bit different than english i believe u still can understand me can you?

---

### Post by cool Cpu on 2010-08-22
there is an issue with optiarc devices in ubuntu lucid udev to much cpu used so i want to block it i mean just dvd not usb or anything else . i dont use dvd at all n ubuntu so i dont really need it.

anyone know how to do that ?

4,0,0    400) 'Optiarc ' 'DVD RW AD-7560S ' 'SX01' Removable CD-ROM
    4,1,0    401) *
    4,2,0    402) *
    4,3,0    403) *
    4,4,0    404) *
    4,5,0    405) *
    4,6,0    406) *
    4,7,0    407) *

---

### Post by corrytonapple on 2010-08-22
Yes, I can understand your English good enough to help you. Um, if this is a DVD issue, how can we drag that dreaded ATI into this? What are your system specs? Laptop or Desktop? I am sorry that this is taking so long but we are getting places.

---

### Post by QLee on 2010-08-22
[cool Cpu]("http://ubuntuforums.org/member.php?u=1134529"),

Have a look at this bug on launchpad, isn't post 9 something like yours.
[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/578180](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/578180)

---

### Post by Iowan on 2010-08-22
Merged threads

---

### Post by cool Cpu on 2010-08-24
> **corrytonapple said:**
> Yes, I can understand your English good enough to help you. Um, if this is a DVD issue, how can we drag that dreaded ATI into this? What are your system specs? Laptop or Desktop? I am sorry that this is taking so long but we are getting places.


MSI gt 725

laptop 
cpu q9000
ddr3 4gb
ati hd4850
sound intel acl 1200 ati hdmi
hdd 800gb
lucid with the latest updates dual boot win7

i was just saying that i have instaled catalyst instead open source driver for ati card just cuz open source didnt work no matter just forget it it is not about ati just about optiarc dvd

---

### Post by corrytonapple on 2010-08-24
Unless there is some DVD software running, the DVD player should not be effecting your CPU. Try what QLee suggests. Give me a screenshot of System Monitor in the Resources tab and in the Processes Tab. Go to the System Monitor by going to **System>Administration>System Monitor.** You can get to the Screenshot tool by going to [B]Applications>Accessories>Take Screenshot.
[/B]Thanks Iowan. Hey cool Cpu, why are you "Day Old Decaf"?

---

