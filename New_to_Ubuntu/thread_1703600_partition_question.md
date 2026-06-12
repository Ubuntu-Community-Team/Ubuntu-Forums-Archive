---
title: "partition question"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by beew on 2011-03-09
Hi,

I have deleted Windows XP from my XP/Ubuntu dual boot and want to use the unallocated space to install another Linux. It is about 40G I figure I can actually install 2 other distros (since Ubuntu is my main OS these don't have to take a lot of space) But here is the problem, if I install 2 OSes with the / + /home configuratiion I would need to credate 4 partitions in this space and they will all be primary partitions (gparted does not allow me to choose logical) and there is already another primary partition,--the Ubuntu one, that will make five and it is one too many. Since I am not able to create a second extended partition either I am pretty stuck.

The layout is kind of awkward because Windows was installed first (like in most dual boots between Win and Linux)

I have attached a screenshot.

Another question: Is it possible to create / and /home in nonadjacient partitions? I have another similar set up but with a lot more free space to the right of the Ubuntu /home partition. In that case I am thinking of turning the Windows partition (about 60G) into 3 primary partitions for the / partitions of 3 Linux distros and then use the free space right to the Ubuntu partition for their /home partitions. Can this be done?

Thanks for any advice.

---

### Post by cariboo on 2011-03-09
When you do your install, choose the manual partitioning option in order to use the unallocated space on you hard drive. as far as / and /home go, they don't even have to be on the same hard drive.

---

### Post by beew on 2011-03-09
Thanks.

Do you have any idea about the problem with too many primary partitions?

---

### Post by oldfred on 2011-03-09
If doing multiple installs, your /home does not have to be separate. The advantage is if you want to reinstall, it is a bit easier. But  if /home is small then you can just back it up and copy into the new install.

You can keep /home very small if you only have the hidden user files & folders. You can keep all your data in a separate /data partition and share that with every install. You do not have a lot of room for a /data and two installs as you are configured.

You can in gparted move sda2 to the beginning of the drive and then expand the extended partition. A partition move has a slightly risk, make sure you have good backups or be prepared to reinstall. A move should  not change partition numbers or UUID, but if they do change you have to reinstall grub to the MBR and edit fstab.

---

### Post by teward on 2011-03-09
Most system technicians and hardware technicians wont ever go past 4 primary partitions.  Typical setups I've seen on server boxes and/or desktop boxes (regardless of operating systems) is 2 primary partitions, a 3rd partition that is an "extended partition", then 2 or more virtual partitions inside the extended partition.


And the number of 4 primary partitions is the typical technician's agreement on the max. number of primary partitions, not just some arbitrary number i threw out there.

---

### Post by beew on 2011-03-09
> **oldfred said:**
> 
You can in gparted move sda2 to the beginning of the drive and then expand the extended partition. A partition move has a slightly risk, make sure you have good backups or be prepared to reinstall. A move should  not change partition numbers or UUID, but if they do change you have to reinstall grub to the MBR and edit fstab.

Hi, is it ok to move the sda2 to the begining? I have expanded the / partition by moving the right end to the right (and not touching the left end )many times but last time I tried to move a  / partition  closer to the begining (moving both the right an left end to the left) and the hard drive was not bootable anymore (get tons of I/O errors) I don't know if that was just a coincidence that the hard drive died or I have screwed up sometihing with gparted(tried reformat it, overwote it with 0's using the dd command and did a fresh install but still wouldn't boot and got I/O errors)

As to share data, I have had this question before, how do I set it up so that I can read/write into it from all the OS's? I think there will be some permission issues. I don't want to use ntfs because there is no reason to use a Windows file system in a purely Linux machine.

---

### Post by beew on 2011-03-09
> **EvilPhoenix said:**
> Most system technicians and hardware technicians wont ever go past 4 primary partitions.  Typical setups I've seen on server boxes and/or desktop boxes (regardless of operating systems) is 2 primary partitions, a 3rd partition that is an "extended partition", then 2 or more virtual partitions inside the extended partition.


And the number of 4 primary partitions is the typical technician's agreement on the max. number of primary partitions, not just some arbitrary number i threw out there.


yeah I know I am asking if there is a way to expanded the extended partition or move things around so that I don't end up with too many primary partitions.

EDITED: I wouldn't have set it up that way if I wasn't dual booting with Windows and with Windows installed first, but back then I didn't know better. :)

---

### Post by srs5694 on 2011-03-09
> **EvilPhoenix said:**
> Most system technicians and hardware technicians wont ever go past 4 primary partitions.  Typical setups I've seen on server boxes and/or desktop boxes (regardless of operating systems) is 2 primary partitions, a 3rd partition that is an "extended partition", then 2 or more virtual partitions inside the extended partition.


And the number of 4 primary partitions is the typical technician's agreement on the max. number of primary partitions, not just some arbitrary number i threw out there.

This isn't simply an "agreement" by "most" technicians who "won't" go beyond four primaries; it's a hard limit imposed by the [Master Boot Record (MBR)](http://en.wikipedia.org/wiki/Master_boot_record) partitioning system. You *can't* have more than four primary partitions on an MBR disk. (Other partitioning systems, such as the GUID Partition Table (GPT), don't have this limit.)

As to the original issue, if the disk is to hold nothing but Linux partitions, my recommendation is to abandon MBR in favor of GPT. My [GPT fdisk (gdisk)](http://www.rodsbooks.com/gdisk/) utility will convert (mostly) non-destructively from MBR to GPT format. The big caveats relate to booting; it's best to create a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) (which can be as small as about 32 KiB in size, although 1 MiB is a common size) and you must re-install GRUB to the disk after converting it. There are several ways to handle this, but the simplest and safest is probably to use GPT fdisk to convert the disk and add a BIOS Boot Partition, then run the installer for your new distribution and use it to install a GRUB that will boot either distribution. Because GPT doesn't distinguish between primary, extended, and logical partitions, switching to GPT will eliminate that complication and remove the need to move /dev/sda2, which is an inherently dangerous operation. GPT's also got some minor advantages over MBR, such as error checking and redundancy that can theoretically improve reliability.

Another option is to use a new utility I'm writing to convert /dev/sda2 into a logical partition. You'll then be able to resize the extended partition and create some or all of your new partitions as logical partitions. I'll send you a PM with some details in case you decide to attempt this approach.

---

