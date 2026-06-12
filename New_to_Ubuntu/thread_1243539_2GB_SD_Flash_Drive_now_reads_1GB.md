---
title: "2GB SD Flash Drive now reads 1GB"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by chris1950 on 2009-08-18
I loaned a 2GB flash drive(Kingston) to a friend and when I got it back it shows 1GB capacity. How can I get it back to 2GB? When I try to reformat, it shows it as being 1GB not 2GB.

---

### Post by stim on 2009-08-18
if 
```
sudo fdisk -l
```
does not display anything that looks like it is near two GB, I would say your 'friend' swapped your 2G card out for a 1G card, and its pulling a fast one on you.  

If you are absolutely sure its the same card (i.e.,  you engraved your name on it, or otherwise marked it as yours). Then I would try a full format with gparted.

---

### Post by MrWES on 2009-08-18
> **chris1950 said:**
> I loaned a 2GB flash drive(Kingston) to a friend and when I got it back it shows 1GB capacity. How can I get it back to 2GB? When I try to reformat, it shows it as being 1GB not 2GB.

Once the drive is loaded/mounted, hit Alt + F2 and type gksu nautilus (root access nautilus). Navigate to the flash drive and hit Ctrl + H to show hidden files and directories. Navigate to the .trash directory and delete the files in it.

Bill

---

### Post by Penguin Guy on 2009-08-18
Make sure your USB drive is plugged in and type [COLOR="Green"]sudo fdisk -l[/COLOR] into the terminal, then post the results back here.

---

### Post by chris1950 on 2009-08-19
As you can see fdisk is showing it as a 1GB not 2GB. Fdisk is showing my virtual drives after the SD.

[sudo] password for chris: 

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9c589c58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1           38124       38913     6345675   82  Linux swap / Solaris
/dev/sda2   *           1        7295    58597056   83  Linux
/dev/sda3            7296       25531   146480670   83  Linux
/dev/sda4           25532       38123   101145240    5  Extended
/dev/sda5           25532       31610    48829536   83  Linux
/dev/sda6           31611       38123    52315641   83  Linux

Partition table entries are not in disk order
[COLOR=Red]
:(Disk /dev/sdd: 1022 MB, 1022624256 bytes
32 heads, 61 sectors/track, 1023 cylinders
Units = cylinders of 1952 * 512 = 999424 bytes
Disk identifier: 0x6f20736b
[/COLOR]
This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   ?      398636      983425   570754815+  72  Unknown
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(357, 116, 40) logical=(398635, 6, 23)
Partition 1 has different physical/logical endings:
     phys=(357, 32, 45) logical=(983424, 30, 61)
Partition 1 does not end on cylinder boundary.
/dev/sdd2   ?       86419     1078237   968014120   65  Novell Netware 386
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(288, 115, 43) logical=(86418, 26, 1)
Partition 2 has different physical/logical endings:
     phys=(367, 114, 50) logical=(1078236, 17, 53)
Partition 2 does not end on cylinder boundary.
/dev/sdd3   ?      957932     1949749   968014096   79  Unknown
Partition 3 has different physical/logical beginnings (non-Linux?):
     phys=(366, 32, 33) logical=(957931, 2, 32)
Partition 3 has different physical/logical endings:
     phys=(357, 32, 43) logical=(1949748, 25, 36)
Partition 3 does not end on cylinder boundary.
/dev/sdd4   ?           1     1863334  1818613248    d  Unknown
Partition 4 has different physical/logical beginnings (non-Linux?):
     phys=(372, 97, 50) logical=(0, 0, 1)
Partition 4 has different physical/logical endings:
     phys=(0, 10, 0) logical=(1863333, 7, 53)
Partition 4 does not end on cylinder boundary.

Partition table entries are not in disk order
chris@Compaq-Laptop:~$

---

### Post by mess110 on 2009-08-19
Try this:

Step 1: ```
sudo apt-get install gparted
```
this will install gparted GUI program that will help you format you disk

Step 2: ```
sudo gparted
```
this will start gparted with root privileges

Step 3: make sure your flash drive isn't mounted

Step 4: in the top right corner of gparted you will see a button that has sth written like: ```
/dev/sda
``` or something like that

Step 5: select your card and click in the menu: Partition > Format to > FAT16 or FAT32 or NTFS (you could try each)


I hope I helped. Sorry if I didn't. I can just say this helped me detect around 300MB on my flash pen. (it was supposed to be 1gb but it detected only 700MB)

---

### Post by chris1950 on 2009-08-19
> **mess110 said:**
> Try this:

Step 1: ```
sudo apt-get install gparted
```this will install gparted GUI program that will help you format you disk

Step 2: ```
sudo gparted
```this will start gparted with root privileges

Step 3: make sure your flash drive isn't mounted

Step 4: in the top right corner of gparted you will see a button that has sth written like: ```
/dev/sda
``` or something like that

Step 5: select your card and click in the menu: Partition > Format to > FAT16 or FAT32 or NTFS (you could try each)


I hope I helped. Sorry if I didn't. I can just say this helped me detect around 300MB on my flash pen. (it was supposed to be 1gb but it detected only 700MB)

I can add,delete and open files but Gparted does not see it. However I was able to reformat a 8GB pen flash that crashed in windows and now works fine. I guess I will have to use as a 1GB drive unless there is another work around to getting it reset back to 2GB.:(

---

### Post by rednano12 on 2009-08-19
> **stim said:**
> I would say your 'friend' swapped your 2G card out for a 1G card, and its pulling a fast one on you.

Judging from what I've seen, this seems to be most likely.

---

### Post by mess110 on 2009-08-20
> **chris1950 said:**
> I can add,delete and open files but Gparted does not see it. However I was able to reformat a 8GB pen flash that crashed in windows and now works fine. I guess I will have to use as a 1GB drive unless there is another work around to getting it reset back to 2GB.:(

You could try formating it on a different computer. Or on windows (but I think you already tried that)

There just might be a problem with your USB port. GParted does not find one of my flash pens in one of my USB ports. But it DOES work in that port. Similar story with my built in laptop card reader.

In my opinion you might have a last shot at 2gb if you try to format it on a different computer.

Cheers!

---

### Post by The Cog on 2009-08-20
> **chris1950 said:**
> I can add,delete and open files but Gparted does not see it. However I was able to reformat a 8GB pen flash that crashed in windows and now works fine. I guess I will have to use as a 1GB drive unless there is another work around to getting it reset back to 2GB.:(

So you can see files on the drive after you plugged it in? In that case, it must be mounted. My guess is that it has been formatted like a partition and mounted as /dev/sdb as opposed to being formatted like a hard disk and mounted as /dev/sdb1. You should be able to confirm this by using the command **df -h** . If this is the case, you should still be able to use gparted to create a new partition table on it (erasing all the current contents) but I don't think you will be able to make it 2G if it's only a 1G drive. 

Are you sure it didn't accidentally get swapped with a different drive, or that it really was 2G to start with?

---

### Post by credobyte on 2009-08-20
```
sudo lshw

```Can you post the part of the output where your Flash drive is described ( example below ) ?
```
*-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 969MiB (1017MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=801fda4f
           *-volume
                description: Windows FAT volume
                vendor: PARAGON#
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/FLASH
                version: FAT32
                serial: 00b3-00b4
[B]                size: 969MiB
                capacity: 969MiB[/B]
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=FLASH mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
```

---

### Post by chris1950 on 2009-08-20
> **The Cog said:**
> So you can see files on the drive after you plugged it in? In that case, it must be mounted. My guess is that it has been formatted like a partition and mounted as /dev/sdb as opposed to being formatted like a hard disk and mounted as /dev/sdb1. You should be able to confirm this by using the command **df -h** . If this is the case, you should still be able to use gparted to create a new partition table on it (erasing all the current contents) but I don't think you will be able to make it 2G if it's only a 1G drive. 

Are you sure it  didn't accidentally get swapped with a different drive, or that it really was 2G to start with?

Yes I am sure, and it was 2GB to start with as I put 2GB of music on it and played it in my car MP3 player. see command df -h below

chris@Compaq-Laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda2              56G  5.1G   48G  10% /
tmpfs                 1.9G     0  1.9G   0% /lib/init/rw
varrun                1.9G  320K  1.9G   1% /var/run
varlock               1.9G     0  1.9G   0% /var/lock
udev                  1.9G  160K  1.9G   1% /dev
tmpfs                 1.9G  116K  1.9G   1% /dev/shm
lrm                   1.9G  2.5M  1.9G   1% /lib/modules/2.6.28-14-generic/volatile
/dev/sda5              46G  1.5G   43G   4% /Data
/dev/sda6              50G  180M   47G   1% /Storage
/dev/sda3             138G  188M  131G   1% /Virtual
[COLOR=Purple]/dev/mmcblk0          975M  202M  774M  21% /media/KINGSTON[/COLOR]
chris@Compaq-Laptop:~$ 

As you can see it is in the built-in card slot but Gparted still does not read it.

---

### Post by LewRockwell on 2009-08-20
perhaps we're arriving at the point where portions of these flash drives/cards are reaching their respective failure points

this is not the first thread to relate these issues

in some discussions the trouble-call has related that the drive itself has became very hot in a few seconds(doubtful that that is "normal")

either way, flash drives are inexpensive and not worth the time to goof around with

.

---

### Post by chris1950 on 2009-08-20
> **credobyte said:**
> ```
sudo lshw

```Can you post the part of the output where your Flash drive is described ( example below ) ?
```
*-scsi
          physical id: 1
          bus info: usb@1:2
          logical name: scsi4
          capabilities: emulated scsi-host
          configuration: driver=usb-storage
        *-disk
             description: SCSI Disk
             physical id: 0.0.0
             bus info: scsi@4:0.0.0
             logical name: /dev/sdb
             size: 969MiB (1017MB)
             capabilities: partitioned partitioned:dos
             configuration: signature=801fda4f
           *-volume
                description: Windows FAT volume
                vendor: PARAGON#
                physical id: 1
                bus info: scsi@4:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/FLASH
                version: FAT32
                serial: 00b3-00b4
[B]                size: 969MiB
                capacity: 969MiB[/B]
                capabilities: primary fat initialized
                configuration: FATs=2 filesystem=fat label=FLASH mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted
```


As requested see below, same results mounted & unmounted: does not show.

  *-pci:2
          description: PCI bridge
          product: MCP51 PCI Bridge
          vendor: nVidia Corporation
          physical id: 10
          bus info: pci@0000:00:10.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci ht bus_master cap_list
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C832 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: 9
             bus info: pci@0000:05:09.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
        *-system:0
             description: SD Host controller
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 9.1
             bus info: pci@0000:05:09.1
             version: 19
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=sdhci-pci latency=64 module=sdhci_pci
        *-system:1 UNCLAIMED
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 9.2
             bus info: pci@0000:05:09.2
             version: 0a
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
        *-system:2 UNCLAIMED
             description: System peripheral
             product: xD-Picture Card Controller
             vendor: Ricoh Co Ltd
             physical id: 9.3
             bus info: pci@0000:05:09.3
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
     *-multimedia
          description: Audio device
          product: MCP51 High Definition Audio
          vendor: nVidia Corp

---

### Post by niteshifter on 2009-08-20
Hi,

The info you gave in posts #5 and #12 show the device as an unpartitioned unit (as The Cog stated in his post).

/dev/mmcblk0 - the device name given to **m**ulti-**m**edia **c**ards. In this case, the 0th (first device seen). A partitioned card would show as /dev/mmcblk0p1 (first partition). Second parition (if it exists) would be /dev/mmcblk0p2 and so forth.

The card has had a file system placed directly upon the device /dev/mmcblk0. That's the limit you may be seeing. Not all devices "play well with others" this way.

If there's any thing on that card you wish to keep, copy it off before doing the below steps.

1. Insert the card in the computer's card reader slot.

2. Unmount it:
```
sudo umount /media/KINGSTON
```

3. Erase the card completely:
```
sudo dd if=/dev/zero of=/dev/mmcblk0 bs=512
```

4. When the erase completes remove the card.

5. Reinsert the card into the reader slot. Don't skip this step - it acts like a reset to the card.

6. Partition the card with whatever tool you favor (fdisk, cfdisk, sfdisk or GParted) to have just one partition. Whatever method you use it should report the size of the "drive" now as 2GB.

7. Make the file system of your choosing on the just created parition. (VFAT recommended if you're sharing with other systems)

If clearing the card doesn't bring it back to 2GB then there are just three possibilities:
A) The controller on the card itself (not your reader's) has decided that 1GB worth of space has become unusable. I think this unlikely that an entire GB would go out at once, normally flash memory wear-leveling mechanisms either just kill the whole device for writes or mark pages (kilo-bytes in size) as unusable - the apparent size of the device decreases in increments over time.

B) The card is failing to address that "upper" 1GB, the card is faulted.

C) Your friend swapped labels. They do peel off easily.

---

### Post by chris1950 on 2009-08-21
> **niteshifter said:**
> Hi,

The info you gave in posts #5 and #12 show the device as an unpartitioned unit (as The Cog stated in his post).

/dev/mmcblk0 - the device name given to **m**ulti-**m**edia **c**ards. In this case, the 0th (first device seen). A partitioned card would show as /dev/mmcblk0p1 (first partition). Second parition (if it exists) would be /dev/mmcblk0p2 and so forth.

The card has had a file system placed directly upon the device /dev/mmcblk0. That's the limit you may be seeing. Not all devices "play well with others" this way.

If there's any thing on that card you wish to keep, copy it off before doing the below steps.

1. Insert the card in the computer's card reader slot.

2. Unmount it:
```
sudo umount /media/KINGSTON
```3. Erase the card completely:
```
sudo dd if=/dev/zero of=/dev/mmcblk0 bs=512
```4. When the erase completes remove the card.

5. Reinsert the card into the reader slot. Don't skip this step - it acts like a reset to the card.

6. Partition the card with whatever tool you favor (fdisk, cfdisk, sfdisk or GParted) to have just one partition. Whatever method you use it should report the size of the "drive" now as 2GB.

7. Make the file system of your choosing on the just created parition. (VFAT recommended if you're sharing with other systems)

If clearing the card doesn't bring it back to 2GB then there are just three possibilities:
A) The controller on the card itself (not your reader's) has decided that 1GB worth of space has become unusable. I think this unlikely that an entire GB would go out at once, normally flash memory wear-leveling mechanisms either just kill the whole device for writes or mark pages (kilo-bytes in size) as unusable - the apparent size of the device decreases in increments over time.

B) The card is failing to address that "upper" 1GB, the card is faulted.

C) Your friend swapped labels. They do peel off easily.


Thanks, your right. I just installed DiskInternals Linux Reader on my Vista machine and it shows Unallocated space  975.25 Mb at end. So will follow your instructions to try and get it back. (I kept telling everyone that it WAS a 2GB and this proves it.)

---

### Post by hussein chechen on 2009-12-17
[SIZE=5]Hello everyone[/SIZE]
[SIZE=5]Different size Memory Card After connecting to my computer my memorey card size is 2GB after connecting to my computer becomes 1.90 MB why
please help me[/SIZE]

---

