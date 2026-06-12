---
title: "How to tell the Windows and Ubuntu partitions apart in GParted"
date: 2011-08-10
forum: New to Ubuntu
---

### Post by R1chbloke on 2011-08-10
Hello,

I use an Acer Extensa 5620G which had Vista Home Premium installed. I added Natty Narwal as a dual partition alongside the now defunct and un-bootable Vista partition. When I open GParted to delete the knackered Vista partition I'm not sure which it is!

I'm running out of HD space and have deleted the Windows partitions I could identify - I've now 71GB of unallocated space.

So I want to:
[LIST=1]
[*] Identify which partition is Vista
[*] Delete the Vista partition
[*] Allocate the free space to the Ubuntu file system
[/LIST]

I've attached a print screen so you'll all have a better idea what the issue is.


Thanks, R

---

### Post by haqking on 2011-08-10
> **R1chbloke said:**
> Hello,

I use an Acer Extensa 5620G which had Vista Home Premium installed. I added Natty Narwal as a dual partition alongside the now defunct and un-bootable Vista partition. When I open GParted to delete the knackered Vista partition I'm not sure which it is!

I'm running out of HD space and have deleted the Windows partitions I could identify - I've now 71GB of unallocated space.

So I want to:
[LIST=1]
[*] Identify which partition is Vista
[*] Delete the Vista partition
[*] Allocate the free space to the Ubuntu file system
[/LIST]

I've attached a print screen so you'll all have a better idea what the issue is.


Thanks, R

The NTFS partition is likely to be Vista. The FAT 32 is a recovery partition

The partitions using ext as the filesystem are linux

Though as a dula boot deleting the Vista will likely screw up your GRUB.

---

### Post by mikewhatever on 2011-08-10
Look at the 'File System' column. Windows partitions will have the NTFS file system, while Ubuntu ones ext4. It looks like /dev/sda2 was your Vista partition.
Now, you Ubuntu partition is /dev/sda5, and to add the unallocated space to it, you first have to expand the extended partition - /dev/sda4.

---

### Post by R1chbloke on 2011-08-10
I'm fresh to Ubuntu - what is the GRUB?

Please educate me :)

---

### Post by Joebewan on 2011-08-10
The FAT32 partition is probably a utility partition containing diags and such for your computer.  As long as you don't need them, delete that one.  You won't gain much space though, so I'd probably leave it just in case you do need the diags.

The NTFS partition is also a Windows partition.  As long as you have the data it contains backed up, you can delete it.

---

### Post by R1chbloke on 2011-08-10
Cool. I've removed the FAT32 and NTFS partitions.[IMG]/home/richard/Desktop/Screenshot--dev-sda - GParted-1.png[/IMG]

---

### Post by Arijit_Kundu on 2011-08-10
yes, looks like sda2 was the windows partition, which is still not deleted. probably you can extend the partition sda4 in the unallocated portion to make some room for the ext4 sda5. But, before extending sda4 or sda5, back up your data and boot from a live usb/cd to extend it.

---

### Post by R1chbloke on 2011-08-10
When  I right-click on /dev/sda4 I can't resize despite unallocated space either side of this partition...

---

### Post by Arijit_Kundu on 2011-08-10
now it is mounted. you have to boot from live cd/usb and then only you should try to extend the root partition

---

### Post by R1chbloke on 2011-08-10
I'm trying to create a bootable usb though can't assign to image to the usb drive...[IMG]/home/richard/Desktop/Startup_USB.png[/IMG]

What next?

---

### Post by Arijit_Kundu on 2011-08-10
after downloading the .iso, you should try to create the disk through the usb-creator program you should find in the menu, or just install unetbootin from synaptic. for more elaborate details, see [this ]("https://help.ubuntu.com/community/Installation/FromUSBStick")

then, while booting change the boot device to be the usb from bios.

---

### Post by R1chbloke on 2011-08-10
Great stuff. I've created the boot usb from the .iso file (glad I made the switch to Linux - I'm coming to understand why more Windows users are switching).

So now I a. keep the usb bootable in the laptop, b. restart...accessing bios...get back to you

---

### Post by R1chbloke on 2011-08-11
All finished. I created the start up USB, backed up my docs to Ubuntu One, then performed a clean re-install.

Cheers everyone.

---

