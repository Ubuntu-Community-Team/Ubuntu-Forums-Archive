---
title: "Partition Appears Lost / Gone"
date: 2010-11-21
forum: New to Ubuntu
---

### Post by cressrt on 2010-11-21
I cannot boot up into Grub any longer, PC boots to a Grub Rescue Prompt only.  I booted up via Live CD and cannot see my files an longer; using Palmipsest Disk Utility it does not show the partition as containing Ubuntu at all.  It reads 74GM Extended- unrecognised, within this there is 3GB od Swap Space and the remainder 71GB Free Unallocated Space.

It is a dual boot with Vista

The last action was deleting files from the Vista folder, I then restarted planning to go to Vista and since then cannot see anything.

Does this mean I have lost all my data?
HELP!!

---

### Post by Scunnered on 2010-11-21
I would imagine that you will have to use your vista disk to set the mbr. Having done that you should get back into vista.  

If you get back to vista ok then you should be able to do a fresh install of Ubuntu.

Hope this assists

---

### Post by cressrt on 2010-11-21
I have space on the HD to install Ubuntu, but my concern is that I have lost all my files from the current install.  I was planning to erase Vista soon once I had backed up my data, but this happened before I could. I have some fiels left on Vista but had just deleted the duplicate files as I only used Ubuntu,
Not a good day!

---

### Post by coffeecat on 2010-11-21
Let's start by seeing what the partition table says about your partition layout. Boot up with a live CD and post the output of this terminal command:

```
sudo fdisk -lu
```You'll need internet connectivity from the live CD so that you can copy and paste the output into the forum message field. Please also enclose the output in code tags by using the # icon which you can see in the toolbar just above the message field.

When you say you were deleting files from the Vista folder, what exactly do you mean? Were you using Ubuntu at the time?

---

### Post by cressrt on 2010-11-21
I can't access Internet from the PC so have copied the output. I was using Ubuntu to delete the Vista files, the restarted the PC and did not get the Grub back.

Disk /dev/sda: 250.1GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 *512 =512 bytes
Disk identifier: 0x9e81345b

Device        Boot        Start        End        Blocks        Id    System
/dev/sda1            2048        19458047    9728000    27    Unknown
/dev/sda2    *        19458048    22530047    1536000    7    HPFS/NFTS
/dev/sda3            22530048    306675652    142072802+    7    HPFS/NFTS
/dev/sda4            343887451    488392064    72252307    5    Extended
/dev/sda5            482480208    488392064    2955928+    82    Linux swap / Solaris

---

### Post by cressrt on 2010-11-21
```
   	 	 	 	p { margin-bottom: 0.21cm; }a:link {  }  Disk /dev/sda: 250.1GB, 250059350016 bytes
 255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
 Units = sectors of 1 *512 =512 bytes
 Disk identifier: 0x9e81345b
 

 Device		Boot		Start		End		Blocks		Id	System
 /dev/sda1			2048		19458047	9728000	27	Unknown
 /dev/sda2	*		19458048	22530047	1536000	7	HPFS/NFTS
 /dev/sda3			22530048	306675652	142072802+	7	HPFS/NFTS
 /dev/sda4			343887451	488392064	72252307	5	Extended
 /dev/sda5			482480208	488392064	2955928+	82	Linux swap / Solaris

```

---

### Post by coffeecat on 2010-11-21
OK. Your partitions as described by the partition table are as follows:

sda1 - 10GB. An unknown ID probably means that this is a restore partition for Windows.

sda2 - 1.6 GB with the boot flag set. I can only assume this is a separate Vista boot partition. This is common with Windows 7 but unusual with Vista.

sda3 - 145 GB NTFS. Most probably your main Vista partition.

sda4 - an extended partition of 74 GB, but it only contains one logical partition:

sda5 - 3GB, your swap partition.

Apart from the "missing" 71GB in the extended partition, there must also be about 16GB unallocated because there is an unused chunk between the end of sda3 and the beginning of sda4.

I would guess therefore that your missing Ubuntu root partition is the 71GB in sda4. The data will still be there, it's just that the filesystem seems to have gone awol as well as the entry in the partition table.

Your best bet is testdisk. I would normally recommend using the live CD, installing testdisk to the live CD and continuing from there. But since you can't get internet access from the live CD, you'll need to download a live CD that includes testdisk. List here:

[http://www.cgsecurity.org/wiki/TestDisk_Livecd](http://www.cgsecurity.org/wiki/TestDisk_Livecd)

Your need testdisk itself in the first instance. This is to recover missing partitions. Don't use photorec (which comes with testdisk) just yet. That is for recovering files from missing partitions. That is a last resort. Try testdisk first. You may be able to recover your Ubuntu partition. If you can and even if Ubuntu remains unbootable, you will at least be able to rescue files from it using the live CD.

---

### Post by cressrt on 2010-11-21
Have manage to log onto the Internet with a dongle, can you say how to add the relevant file. The CD being used to boot with is not writeable.
Thnaks

---

### Post by coffeecat on 2010-11-21
> **cressrt said:**
> Have manage to log onto the Internet with a dongle, can you say how to add the relevant file. The CD being used to boot with is not writeable.
Thnaks

Don't worry about the CD not being writeable. You can install apps in the live session. They are held in RAM so long as you are in the live session but are lost when you power down. The app testdisk is only a few tens of kilobytes iirc, so not much is lost.

Once you're in the live CD, go to System > Administration > Synaptic and search for the app 'testdisk' and install it. You might have to click on the reload button to download the package metadata before testdisk appears in the list. You can use Software Centre instead if you wish.

Once it's installed, open a terminal, and:

```
sudo testdisk
```It can create a log so it might be advisable to have a USB drive available to copy this to before you finish the live session. One you've created the log file, make sure the problem HD is highlighted and select proceed. It's all fairly intuituve from that point on but you might want to acquaint yourself with its features in the wiki here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

And the specific function you need here:

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Good luck!

---

### Post by cressrt on 2010-11-21
That was quite a simple process and it worked OK. I have booted back with the the Live CD and all the file are now showing. Now just to save everything then I'm going to do a clean install and say goodbye to Windows!
This has re-enforced my faith in Ubuntu and Linux .

Thanks for all your help

---

### Post by cressrt on 2010-11-21
Just one more thing, a lot of the files cannot be moved as I do not appear to have the right privilege, I know I have changed this in the past but cannot remember which setting to change.

---

### Post by coffeecat on 2010-11-21
Good news. I'm glad to hear it.

It would be of theoretical interest only since you intend to do a reinstall anyway, but once you've rescued your files with the live CD you might want to see if the resuscitated Ubuntu partition is bootable.

Whatever, enjoy blowing away Vista. :wink:

---

### Post by cressrt on 2010-11-21
The Grub screen doesn't appear so do I need to do something else to see that it can boot?

---

### Post by theozzlives on 2010-11-21
I've never been a fan of Dual Boot myself. I got Windows 7 free for going to a conference and I use it for a few things on it's own box. The rest of my machines run Ubuntu.

---

### Post by coffeecat on 2010-11-21
> **cressrt said:**
> The Grub screen doesn't appear so do I need to do something else to see that it can boot?

OK it sounds as though some random event may have corrupted the part of the mbr where grub stage 1 resides in addition to what we've been dealing with. If you're interested you could try repairing grub with this:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

But only if you want to. As I said, it's all pretty theoretical if you're planning to do a fresh install.

---

### Post by cressrt on 2010-11-21
Sorry you may have missed this above.
Just one more thing, a lot of the files cannot be moved as I do not  appear to have the right privilege, I know I have changed this in the  past but cannot remember which setting to change.

---

### Post by coffeecat on 2010-11-21
> **cressrt said:**
> Sorry you may have missed this above.
Just one more thing, a lot of the files cannot be moved as I do not  appear to have the right privilege, I know I have changed this in the  past but cannot remember which setting to change.

Ah yes, this is to do with ownership and UID in the live CD session. Your UID in your hard drive account will be 1000 if yours is the first created account. But the live CD 'ubuntu' account has a UID of 99 or 999 or 501 or something. Certainly it's different from your own UID which is why you can't access your files to copy. The easiest way in the live CD is simply to open a root nautilus with:

```
gksudo nautilus
```If you're copying to a FAT32 or NTFS drive that will be fine because Linux ownership and permissions will be lost on a Microsoft filesystem. Which actually makes things easier. But if you are copying to a Linux filesystem you may find that all the copies are owned by root. Or possibly not - I can't remember what the default behaviour is with Nautilus. That is easily fixed though.

As an alternative, if copying to a Linux filesystem, you can copy from the terminal with:

```
sudo cp -a
```The -a option is handy. It preserves ownership and permissions and does a recursive copy all in one go.

---

### Post by cressrt on 2010-11-21
I opened the drive with this command and can see and open documents but cannot copy them?

---

### Post by coffeecat on 2010-11-21
Where are you trying to copy them to?

---

### Post by cressrt on 2010-11-21
To a flash drive, but I just realised that I did not have it open from the nautilus but from the menu. Now it is OK..
Thanks again and I'll try the Grub restore and post result once I've copied everything.

---

