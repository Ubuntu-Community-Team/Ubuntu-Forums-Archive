---
title: "How to install ubuntu 9.04 dual boot xp installed ? newbie"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by ubfu on 2009-06-01
Sorry , I am new to ubuntu.
I had done a partition earlier last year and the partition is quite confusing too.:(

250GB Hard Disk space

Primary Partition (formated to)
C:Window XP ( currently using) [45GB]
E:Fat32 (Storing Data) [with data 20GB]
F:NTFS (Storing Data) [with data 60GB]

Extended Partition (Logical)
G: Storing Data)[with data 110GB]

I had made 3 primary partition and 1 local partition which I had fully used up all of the partition remaining.
Now I wanted to install ubuntu 9.04.I plan to choose and format to install it on E:Fat32 which is 20GB

I went to the installation of 9.04 but I was confuse using Advance partition ,

-Which one I should choose ? Ext4 , Ext3 ,Ext2 ,ReiserFS , JFS , XFS , Fat16 , Fat32 ?
-What is ext3 and 4 difference ? is ext4 will cause booting problem to my window xp ?
-About the swap partition ,  I choose to install ubuntu 9.04 into E: , there is no other partition left for Swap.Or the swap partition can create another partition inside E: ? (I had 2GB ram , how much I should use ? )
-What is mount Point ? got /boot , /Home  , /tmp , /usr and others. ??

Please Guide me though it [-o< thank you very much.

---

### Post by rossmoore on 2009-06-01
This could be a very long post, the options for partition layout are endless. I'll give a quick answer:

Let's start with your partition layout.
20Gb should be enough for Ubuntu - especially if you'll be having your data (Music, photos, etc) on one of the other partitions.
You should have at least as much space for swap as you have RAM - in theory you should have twice as much (4Gb for you).
People normally choose either ext3 or ext4 for their filesystem. Ext4 is the latest version of Ext3 and is quicker. I use Ext4, but many still use Ext3 - I only switched 2 months ago. The safe, default option is Ext3.

So if I were you, and I've understood your setup correctly, I would:
Move the data on E: to another location.
Then in the installer:
Delete the E partition, and replace it with two partitions:
One 16Gb, Ext3
One 4Gb, swap
Then install Ubuntu into the 16Gb partition, with mount point = "/".

You have other options if you're willing to move or play about with other partitions, but that's probably the quickest and simplest solution.

Final caveat: Can you replace a primary partition with two logicals like that? I _think_ you can.

---

### Post by ubfu on 2009-06-01
> **rossmoore said:**
> This could be a very long post, the options for partition layout are endless. I'll give a quick answer:

Let's start with your partition layout.
20Gb should be enough for Ubuntu - especially if you'll be having your data (Music, photos, etc) on one of the other partitions.
You should have at least as much space for swap as you have RAM - in theory you should have twice as much (4Gb for you).
People normally choose either ext3 or ext4 for their filesystem. Ext4 is the latest version of Ext3 and is quicker. I use Ext4, but many still use Ext3 - I only switched 2 months ago. The safe, default option is Ext3.

So if I were you, and I've understood your setup correctly, I would:
Move the data on E: to another location.
Then in the installer:
Delete the E partition, and replace it with two partitions:
One 16Gb, Ext3
One 4Gb, swap
Then install Ubuntu into the 16Gb partition, with mount point = "/".

You have other options if you're willing to move or play about with other partitions, but that's probably the quickest and simplest solution.

Final caveat: Can you replace a primary partition with two logicals like that? I _think_ you can.

Yep , I'll move and backup all the data at E:
Run ubuntu live cd and delete the E partition

But I am still abit of confuse.The hard disk is limited to maximum of 3 primary partition and 1 extended and also maximum of 4 primary partition without any extended partition.
I had made 3 primary and 1 extended.Installing ubuntu needed 1 primary as it'll be at E: but about the swap file , it needed another partition or it can be done under the same E: partition ?
I don't quite understand 
"Final caveat: Can you replace a primary partition with two logicals like that? I _think_ you can."
What does it mean actually ?

Can I actually doing the quickest and simplest solution 
-Delete the E partition, and replace it with two partitions:
-One 16Gb, Ext3
-One 4Gb, swap

I am very confuse on the swap partition and about the hard disk partition (Primary and local extended )
Hope anyone can guide me out.Thank you very much. :)

---

### Post by Elfy on 2009-06-01
If I read it right you won;t be able to make 2 new partitions if all exisitng are on one hdd - maximum of 4 primaries includinf a single extended (which you already have)

The best thing you could do would be to provide the result of running the following command from a terminal on the livecd - find terminal in Applicatiosn > Accessories

```
sudo fdisk -l
```

As far as how much swap IF you need to hibernate then swap should be the same as RAM or slightly higher otherwise it's likely you could use less. I have 2Gb RAM and 1Gb swap and rearely use the swap.

---

### Post by ubfu on 2009-06-01
Anyone can quick guide me what I should do ?
Please help , thank you again. 

```
> 
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11fb11fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421    7  HPFS/NTFS
/dev/sda2            5738        8287    20482875    b  W95 FAT32
/dev/sda3            8288       15936    61440592+   7  HPFS/NTFS
/dev/sda4           15937       30401   116190112+   f  W95 Ext'd (LBA)
/dev/sda5           15937       19760    30716248+   7  HPFS/NTFS
/dev/sda6           19761       26134    51199123+   7  HPFS/NTFS
/dev/sda7           26135       30401    34274646    7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```

---

### Post by Elfy on 2009-06-01
Somehow you need to get a new partition for your swap - I would resize one of the logical partitions - sda5-sda7 - to get some unallocated space for the swap. Your E: partition can just be formatted to enable the install. 

I am using ext4 but there have been reports of problems - so you could use ext3 which is the default.

If your E: is inside the extended then you can delete it and create 2 new logicals - it depends where it resides now. If you're not sure which drive is which then you can gete a graphical representation of your partitions by running the partition editor from the System Admin menu.

---

### Post by ubfu on 2009-06-01
> **forestpixie said:**
> Somehow you need to get a new partition for your swap - I would resize one of the logical partitions - sda5-sda7 - to get some unallocated space for the swap. Your E: partition can just be formatted to enable the install. 

I am using ext4 but there have been reports of problems - so you could use ext3 which is the default.

If your E: is inside the extended then you can delete it and create 2 new logicals - it depends where it resides now. If you're not sure which drive is which then you can gete a graphical representation of your partitions by running the partition editor from the System Admin menu.

Sorry I think I made a mistake at my first post about extended.Judging from the drive size.

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5737    46082421    7  HPFS/NTFS
/dev/sda2            5738        8287    20482875    b  W95 FAT32
/dev/sda3            8288       15936    61440592+   7  HPFS/NTFS
/dev/sda4           15937       30401   116190112+   f  W95 Ext'd (LBA)
/dev/sda5           15937       19760    30716248+   7  HPFS/NTFS
/dev/sda6           19761       26134    51199123+   7  HPFS/NTFS
/dev/sda7           26135       30401    34274646    7  HPFS/NTFS
ubuntu@ubuntu:~$
```
```

sda1 = C:
sda2 = E: ( which I had formated to fat32)
sda3 = F:
sda4 = extended which I had made sda4=G: ,sda6=H: ,sda7=I: 
```

So , can you kindly suggest me what I should remove or partition ? I wanted to minimize any hassle on deleting file , backup them to a dvd and etc.

---

### Post by Elfy on 2009-06-01
Personally and assuming that you have the free space I would resize sda7 so it is 2Gb smaller. 

Now you can proceed with the install - when it reaches the partition part - choose manual again.

Select the partition which corresponds to E:\ - here is where you will install the OS - while it is selected - Edit partition, you'll get a new window - in the Use As menu choose ext3. Tick the format box. From the Mountpoint box pick /. Close that window.

The partitioner wil refresh - now pick the unallocated space that you got from the earlier resize of sda7 - (don't pick any of the partitions, just the unallocated space) - Edit partition - Use As = choose swap , tick the format box. Close, let the partioner refresh and continue.

IF you are unsure while doing that - screenshot the partition window and paste that here so someone can check - but it should be failry self explanatory once you are doing it - changes don;t get made to the partitions until later so you can bale if you want to ;)

---

### Post by ubfu on 2009-06-01
> **forestpixie said:**
> Personally and assuming that you have the free space I would resize sda7 so it is 2Gb smaller. 

Now you can proceed with the install - when it reaches the partition part - choose manual again.

Select the partition which corresponds to E:\ - here is where you will install the OS - while it is selected - Edit partition, you'll get a new window - in the Use As menu choose ext3. Tick the format box. From the Mountpoint box pick /. Close that window.

The partitioner wil refresh - now pick the unallocated space that you got from the earlier resize of sda7 - (don't pick any of the partitions, just the unallocated space) - Edit partition - Use As = choose swap , tick the format box. Close, let the partioner refresh and continue.

IF you are unsure while doing that - screenshot the partition window and paste that here so someone can check - but it should be failry self explanatory once you are doing it - changes don;t get made to the partitions until later so you can bale if you want to ;)

Resize which you meant taking out 2GB from sda7 30GB which remain 28GB right ?
So how can I do that ? 

I remember only vista have the shrink partition which can shrink the partition volume and arrange/sorting the files to free the space.But , how do I do that ? I am using window XP currently and I can't think of any program for Ubuntu than can do it.

Swap partition can choose on extended logical partition ? I  though it only allow primary partition

So , let say at the "Prepare Partitions " screen step 4 of 7 
While I selecting the partition for Ubuntu and swap files, it wouldn't do any thing until I click forward right ?

Worry it'd do anything wrong.:(

---

### Post by Elfy on 2009-06-01
there's a partition editor on the livecd - System - Admin menu

> So , let say at the "Prepare Partitions " screen step 4 of 7
While I selecting the partition for Ubuntu and swap files, it wouldn't do any thing until I click forward right ?From memory that is correct.

> Resize which you meant taking out 2GB from sda7 30GB which remain 28GB right ?yep

> Swap partition can choose on extended logical partition ?yep - any of the needed linux partitions will work as logicals

---

### Post by rossmoore on 2009-06-02
Hi Ubfu,

I now realise that your first reply is of course correct, you cannot create another logical like that.

forestpixie's advice looks very good - you need to create a bit of space for swap.

Here's a good [guide to partitioning]("https://help.ubuntu.com/community/HowtoPartition") to help you understand what's being suggested, and what the implications might be.

Ross

---

### Post by mevan_snp on 2009-06-02
run under windowes. it's safe

---

### Post by Nixie Pixel on 2009-06-02
My little video tutorial might help you, I hope! It was made for Vista but can help with XP too, though the partition resizing is different in XP (or you can just use GParted, only Vista seems to have problems with partition alignment being messed up by partitioning from outside of Windows):

[My Ubuntu installation video tutorial.]("http://www.youtube.com/watch?v=GhnLk3gviWY")

---

