---
title: "cannot mount volume error 212.5 GB media"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by clay woodruff on 2009-12-25
ok when i go to my computer i have a few things there i don't understand what they are. this is what is showing
 212.5 GB media ?
cd-rw/dvd-rom dr
cd-rw/dvd+rw dr
compactflash drive ?
disk2_vol1
memory stick drive ?
sd/mmc drive ?
SmartMedia drive ?
filesystem

so when i tried to open the 212.5 gb media drive i got an error message that read.
mount: wrong fs type, bad option, bad superblock on /dev/sdb5  missing codepage or helper program or other error  in some cases useful info is found in syslog-try   dmesg | tail or so. 

does anyone have any idea what this is or why it happens. also what are these other drives i'm showing. i do have 2 hard drives disk2 is my slave drive and i'm assuming file system is my master drive. Right? :???:

---

### Post by mgranet on 2009-12-26
What is the output of ```
sudo fdisk -l
```
and
```
cat /etc/fstab
```

---

### Post by clay woodruff on 2009-12-26
fdisk is
Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11661    93666951   83  Linux
/dev/sda2           11662       12161     4016250    5  Extended
/dev/sda5           11662       12161     4016218+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x257f016e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4111    33021576    7  HPFS/NTFS
/dev/sdb2            4112       30515   212090130    5  Extended
/dev/sdb5            4112       29952   207567801   83  Linux
/dev/sdb6           29953       30515     4522266   82  Linux swap / Solaris

fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=73241397-e343-4a6a-8fe3-0e789f867b82 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=aa651e48-a580-459b-8ad5-31cf733c6bdc none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

thanks for taking the time to assist me.
see a few things that i was wondering about although still dont understand, how did i swap something during install? please be patient. i was the kid at school who always tried to fit the round peg in the square hole.

---

### Post by mgranet on 2009-12-26
First, you'll need to check the filesystem for errors on /dev/sdb5 (what appears to be your 212GB partition). To do this:

```
sudo fsck -cfpv /dev/sdb5
```

And I'm assuming you wish the disk to automount (be ready to use) at every boot?
If so, you'll need to modify the /etc/fstab file. First, you'll need to create what is called a mountpoint. ```
sudo mkdir /media/sdb5
```
Now, you'll need to attach the drive to the mountpoint. ```
sudo mount /dev/sdb5 /media/sdb5
```
Now to change the permissions (replace *user* with your username):```
sudo chown *user:user* /media/sdb5
```
Next, you can make the mount persistent across boots:
```
sudo gedit /etc/fstab
```
*I'm **assuming** you are using ext3 for your drives, based on what I see in the existing fstab. If you did a fresh install of 9.10, your drives will be in ext4, and you may need to edit the line I give you to read as such.*

Add the following line to the end of your /etc/fstab, then save and reboot.
```
/dev/sdb5 /media/sdb5 ext3 user,defaults 0 0
```

---

### Post by clay woodruff on 2009-12-26
ok great. before i do this, would it be better to install 9.10 first and implement the change in the code. or is it something your saying i would need to change after/if i upgraded. also maybe this has some barring....or none what so ever on this, what i did was after a friend turned me on to ubuntu i downloaded the 9.10 version burned it to a disc, but DID NOT check for errors. it had a few. so when i began to install it had gotten 35% complete and stopped. completely dumping windows and whatever else. at that point i was done, i had no computer to fix it on. so my friend had a good disk he gave me, only it was 9.4. is that why it said there was a swap at install? or it didn't really matter and the 9.4 install wipped out whatever was there anyway. just a thought trying to grasp how things work. really new to all this terminal comand stuff. and thanks again for your help.


ok well there is a problem i ran fsck and got this

fsck 1.41.4 (27-Jan-2009)
/dev/sdb5: Superblock has an invalid journal (inode 8 )
CLEARED.
*** ext3 journal has been deleted - filesystem is now ext2 only ***

Error reading block 99329 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  

/dev/sdb5: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
    (i.e., without -a or -p options)

how do i run fsck manually
isnt a bitmap a format for an image file? like jpeg?

---

### Post by mgranet on 2009-12-26
Ok, I see now what happened. Let's start from the top.
You had a bad burn, so the install failed halfway through (i.e., after partitioning was complete). The issue here is that 9.10 uses ext4 by default to create the partitions. So you got a good 9.04 disk, and attempt to reinstall, but 9.04 uses ext3 as a default. 

I'm guessing by what you told me, and what your current /etc/fstab says, you did not delete the old ext4 partition you created in 9.10; on the next install the guided partitioner created *another* partition set, this time in ext3. This explains why you have two swapfiles on two seperate disks. From what I can see, your Windows partition is still intact; you just can't access it because you have overwritten the Windows bootloader.

You have two options at this point. You can either get a good 9.10 disc, or use your 9.04 and upgrade once the install is complete. The choice is up to you, I will explain how to fix the problem using either one.

First, begin the installation sequence using the good 9.04 or a new 9.10 disk. When you come to the partitioning screen, select **Specify Partitions Manually (advanced)**. Here you will see your two physical disks, and they will be divided up into partitions. One of these partitions will be your Windows one, and it will be the NTFS patition. Delete every other parition but this one. From what I can see, this will leave you with a blank 100GB (sda)drive, and a Windows partition and free space on your 250GB (sdb)drive. 

The problem here is I can't tell you how you want your partitions setup; I can only tell you what I would do in your case. I would use the 100GB (sda) drive for Linux, keep your Windows partition as it is, and create a new NTFS partition that fills the rest of your 250GB drive (sdb). This will allow you to use that space in both Windows and Linux, as Linux can read/write to NTFS. Here's how to do it:

First, if you haven't already, delete all partitions that are NOT NTFS. Once the 100GB (sda) is empty, click on **Free Space** under the **/dev/sda** device list. 

For 9.04: Under the **Use As** dropdown, select **EXT4 journalling filesystem**. In the **Mountpoint** dropdown, select **/**

For 9.10: In the **Mountpoint** dropdown, select **/**

In the box that says **New Partition Size** there will be a number. You will need to subtract from this amount the amount of space you wish to assign to swap. Rule of thumb is 1.5 times the amount of ram you have. For example: If I have 1GB of ram, I would subtract 1500 from the number in the **New Partition Size** box. Enter this new figure (the result, not the 1500) into the **New Partition Size** box. Click OK.

Now you need to create swap space. To do this, again click on the Free Space label under sda. In the **Use As** dropdown, select **swap area**. Click OK.

Under sdb, there should be two labels; one should be your NTFS parition, and the other should be free space. You will leave this as free space, and can partition it in Windows as NTFS. For later reference: You can mount this NTFS partition in linux with the directions I showed you in my second post. The line to add to your fstab will read: 
/dev/sdb2 /media/sdb2 ntfs-3g user,defaults 0 0

Now click Forward to continue with the installation of Kubuntu. When you complete it, you should now be able to select from Linux or Windows from the grub menu that appears at boot.

Good Luck!

---

### Post by clay woodruff on 2009-12-26
holly cow!!! ok here goes trying to fit the round peg in the square hole again....<laughin> i think this time with enough velocity at impact.... it will fit. i guess i will download a good 9.10 disk and run with that, at least this way i have good 9.4 and 9.10 disk. ok so if you dont see a solved tag along with my post. you can assume i blew it and i just threw the square peg out the window. once again a thousand thanks for your time and knowledge.

ohh hey one more thing, i guess once all is complete i will have to reinstall my drivers for my graphics card as well as the changes i made to my xorg file so that  my resolution would be correct. right? pretty much i'd be at point A again, correct?

---

### Post by mgranet on 2009-12-26
Correct. Your partitions were pretty messed up, in this case, I think the best solution was to start over. That way, you've got ext4 and GRUB 2.

---

### Post by clay woodruff on 2009-12-27
@mgrants well this is the new outputs what do you think did it work out right? how come all of a sudden i get a error message that the 251 GB disk is failing. i got that before when i was on 9.10 from the cd. i clicked on details and it said has bad sectors?


Disk /dev/sda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11979    96221286   83  Linux
/dev/sda2           11980       12161     1461915    5  Extended
/dev/sda5           11980       12161     1461883+  82  Linux swap / Solaris

Disk /dev/sdb: 251.0 GB, 251000193024 bytes
255 heads, 63 sectors/track, 30515 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x257f016e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4111    33021576    7  HPFS/NTFS


/etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=ddafce1d-52b8-453e-9d6a-e84325c85c33 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=96eec1a7-a56a-4273-9e8a-093d0c47accb none            swap    sw              0       0
/dev/scd1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

