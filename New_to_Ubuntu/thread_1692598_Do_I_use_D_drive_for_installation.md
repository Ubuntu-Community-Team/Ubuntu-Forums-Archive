---
title: "Do I use D drive for installation"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by Olivares on 2011-02-21
I am a Windows user with no experience of Linux. I recently bought a new computer and I had the 250 Gb hard drive partitioned into a C-drive (157 Gb) and a D-drive (93 Gb). Windows XP and all applications and files are on the C-drive; the D-drive is blank. I have an installation CD for Ubuntu 8.04 and I thought that I would install Ubuntu on the D-drive and this way have a dual-boot computer. However, when I select the D-drive at step 4 in the installation procedure, and select ‘manual,’ it will only let me create one partition. If I create a root partition, it tells me I need to create a swap partition but there is no apparent way to do this. If I create a swap partition it tells me I need to create a root partition but again doesn’t seem to have an option for this. I am beginning to think that I have wasted my time having a D-drive and that I am supposed to install Ubuntu on the C-drive. Is this correct? If so, do I use the first option in step 4, i.e. “guided - resize SCS13 (0, 0, 0) partition # sda and use freed space”?

I have read some of the threads touching on this topic but I'm still confused and want to be certain about what I'm doing before making changes affecting my hard drive.

---

### Post by wojox on 2011-02-21
First I would download 10.04 and install that. When you get to the manual partition screen delete D and create a new Primary Partition for root ( / ) and one for Swap.

---

### Post by Oathanvil on 2011-02-21
Read my same question resolved post!

[http://ubuntuforums.org/showthread.php?p=10459148#post10459148](http://ubuntuforums.org/showthread.php?p=10459148#post10459148)

I too am new to Ubuntu but you need to create some partitions for it.

My follow up post has directions from other users and my own resolve with pictures.

---

### Post by Frogs Hair on 2011-02-21
8.04 will loose support soon , it may be best to download 10.04 or 10.10  before installing Ubuntu . 10.04 will be supported longer as it is an LTS release. [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Dutch70 on 2011-02-21
> **wojox said:**
> First I would download 10.04 and install that. When you get to the manual partition screen delete D and create a new Primary Partition for root ( / ) and one for Swap.

+1

 Support for 8.04 runs out in about 2 months. It will no longer be maintained. If you have a flash/thumb drive aka usb stick, it's much easier & faster to install than a cd. 

As far as your question about C: or D:, it makes no difference what windows names the partition. 

Download & directions below...
[*[COLOR="Blue"]http://www.ubuntu.com/desktop/get-ubuntu/download[/COLOR]*]("http://www.ubuntu.com/desktop/get-ubuntu/download")

---

### Post by grahammechanical on 2011-02-21
The live CD runs the Partition Manager program as part of the install process. What are called drives in Windows are called partitions in Linux. You only have one physical drive but it is in two partitions. Agreed? You need to tell the installer to put Ubuntu in the empty space that you have created.

Do not tell the program to format the partition where Windows is installed. Do not agree to let it use the entire disc. These actions will wipe out the Windows installation.

You need to select the empty partition. You might see the windows partition marked as sda1 and the empty partition as sda2. You need to give it a mount point, which should be /  It will need to be formatted so tick the box and select a format. Either Ext3 or Ext4. Now the installation will put Ubuntu there.

You also need a swap partition. So choose to have a swap partition by  selecting a mount point of /swap. The program may suggest a size which  you can accept. This partition will automatically be created. Up until  this point no changes have been made to the disc so you can back out. If  you are nervous.

May I make a suggestion that seems more complicated but is actually easier in the long run? Use Partition manager to create a third partition by shrinking the empty partition to 20GB. This is sufficient for the Ubuntu OS. The new partition should be mounted as /home and formated either to Ext3 or Ext4. Create the swap partition as above.

Why do this? All your data will be on the /home partition. A lot of the settings that make the desktop personal to you will be in the /home partition. If you need to re-install Ubuntu at any time you can tell the program to put the new Ubuntu into the / partition. You can format it if you like. You can assign the already existing /home partition as mount point /home and the already existing /swap partition as mount point /swap. You do not mark these to be formatted. Then you get a clean installation without loosing your data and settings. Otherwise all your data will be in a /home folder on that / partition and it will be wiped by a re-installation.

Regards.   And good luck. You will need it. No, I am joking.

---

### Post by theDaveTheRave on 2011-02-21
+1 for a more up to date version of ubuntu.

During the install the system should recognise the 'windows' parition, and you will get plenty of messages like
> this partition already contains data
asking you to confirm that you want to overwrite this partition (which you obviously don't want to do!).


+1 for grahammechanical's advice, proviso however is that this may seem more complex for a first time user. My solution / advice is that if you need to do a re-install of ubuntu ever (or a clean upgrade) is as follows.

Fist install of Ubuntu (or any other linux OS for that matter). Just follow the 'basic' setup, and put everything on the same partition.

Then you can 'play around' with the system, and get to know linux a bit more, then on your second install you can mess around with extra separated partitions.

Remember that the advice of the /home partition also works for creating backups of your personal files and settings - just copy all drives over to an external HDD (ensure you get all the hidden files and folders also) and then you can copy these over to your new system when you have completed it.

An even easier way of trying out ubuntu is the 'Wubi' method, I used it once and was very impressed with how easily everything went.

David

---

### Post by Olivares on 2011-02-22
Thank you everyone for your interest in my problem. You might be interested in the outcome.

The partition manager in Ubuntu had the following table:
       /dev/sda1    157283 Mb. 
      /dev/sda5       92764 Mb
     free space               8 Mb
I went into DiskPart and it gave me the following information:
List partition:
     Partition 1    Primary  146 Gb
     Partition 2    Extended 86 Gb
     Partition 3    Logical 86 Gb.
I deleted partition 3, went back to Ubuntu installation, and the partition table now looked like this:
     /dev/sda1     157283 Mb
    free space       92772 Mb
Selecting 'free space,' I was now able to partition it into /, /swap and /home and perform a successful installation.

---

### Post by srs5694 on 2011-02-23
I realize that the OP has found a solution; I just want to make a couple of points. First, a small technical correction....

> **grahammechanical said:**
> You also need a swap partition. So choose to have a swap partition by  selecting a mount point of /swap.

Unlike most partitions, swap space is not mounted and has no mount point. It's therefore properly referred to as "swap", not "/swap" -- the leading "/" when we refer to, for instance, /home, is part of the directory specification in the Linux directory tree, but since swap space is not mounted, this character is unnecessary, and even technically incorrect, when referring to swap space. This may seem nit-picky, but the better you (the generic "you") understand partitions and the data structures they contain (filesystems and swap space, mainly), the less likely it is that you'll cause problems for yourself down the road when creating and managing them.

Incidentally, it's possible to give a label to swap space, just as you can give a label to many filesystems. This label is mostly ignored, but it can be used to activate swap space by name. If you mistakenly give your swap space a label of "/swap", no harm will come from this, so don't sweat it if you've done this.

My second point is that, except for a passing reference in Olivares's last post (in reference to the old setup), nobody's mentioned the difference between primary, extended, and logical partitions. The Master Boot Record (MBR) partitioning system used on this disk (and most disks in PCs) supports a total of four *primary* partitions. To work around this limit, one of these partitions may be an *extended* partition, which in turn holds an arbitrary number of *logical* partitions. Thus, a disk can hold a total of either four primary partitions or three primary partitions, an extended partition, and an abritrary number of logical partitions. Windows must boot from a primary partition, but you can use logical partitions as data partitions in Windows. Linux is not so limited; you can boot Linux from a logical partition, or use logical partitions for data (such as /home) or for swap.

It's unclear whether Olivares's solution uses any logical partitions. If not, the disk is maxed out on partitions, which will complicate things if a need arises to add more partitions. If that happens, the easiest solution will probably be to delete the swap partition, move and resize as necessary, create a new extended partition, re-create the swap partition as a logical partition, and create the new partition(s) as logical partition(s). This will in turn require adjusting the swap entry in /etc/fstab. If Olivares's current solution involves extended/logical partitions, adding new partitions is likely to be slightly easier.

---

