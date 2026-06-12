---
title: "new hdd: how do I make it writable?"
date: 2011-07-31
forum: New to Ubuntu
---

### Post by mccuisinart on 2011-07-31
I just installed a new 500G HDD. It was recognized by the BIOS, and I was able to create a primary fat32 partition and have it mount automatically on startup in /etc/fstab, but the last step of making it writable is stumping me. How do I make it writable?

---

### Post by bigken on 2011-07-31
try gparted

---

### Post by mccuisinart on 2011-07-31
Cool app. I used it to change the partition into an ext3.

I probably should have mentioned this: I'm running ubuntu and its entire file system off of another drive. An 64G SSD. I bought an additional HDD for extra storage and I want to make it writable from my GUI instead of just sudo in the terminal. GParted doesn't seem to do that, (there doesn't seem to be anything in its help manual, anyway).

Thanks

---

### Post by Miljet on 2011-07-31
What options did you use in the fstab entry? 
```
cat /etc/fstab
```
Copy and paste results here please.

---

### Post by mccuisinart on 2011-07-31
was:

```
/dev/sdb1    /media/wdcb500g   vfat    defaults     0        2
```now:

```
/dev/sdb1    /media/wdcb500g   ext3    defaults     0        2
```-EDIT: (whoops sorry didn't understand your question hold on)...

-EDITx2: (modified /etc/fstab back to its original state)

```
xxxx@xxxx:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=df1ed6d1-3bd4-4919-bc19-f67edfcfd37a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d80b4a94-0999-4ea9-ad1e-0800ebff9c34 none            swap    sw              0       0
```There!

---

### Post by ajgreeny on 2011-07-31
First backup the current fstab with terminal command ```
sudo cp /etc/fstab /etc/fstab-backup
``` You then need to carefully edit the fstab file using the terminal command ```
gksudo gedit /etc/fstab
``` which will give you root privileges.  Now depending on the filesystem that the new disk partition has ended up as, add the appropriate line to fstab, having first made the mountpoint folder with ```
sudo mkdir /media/*newdisk*
```but use a better name than *newdisk* if you want.

Automount ext3 partition. Add line to /etc/fstab:-
```
UUID=66E53AEC54455DB2 /media/*newdisk* ext3 defaults, relatime 0 1
```Automount fat32 partition. Add line to /etc/fstab:-
```
UUID=66E53AEC54455DB2 /media/*newdisk* vfat defaults,user,dmask=027,fmask=137 0 0
```You can find the UUID of attached disks with command ```
sudo blkid
```so change my UUID figures for yours.

Having edited the fstab file run command ```
sudo mount -a
```to execute it.  If any errors report back here, if no errors, all should be ready to go.

---

### Post by mccuisinart on 2011-07-31
Here is my new fstab from the command cat /etc/fstab

```
xxxx@xxxx:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=df1ed6d1-3bd4-4919-bc19-f67edfcfd37a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d80b4a94-0999-4ea9-ad1e-0800ebff9c34 none            swap    sw              0       0
UUID=450bed29-58d1-497f-b7fa-d068a8809cb1 /media/wdcb500g ext3 defaults, relatime 0 1
```I got excited at first because the original instructions I followed from another guide littered my terminal with errors after I saved and exited /etc/fstab, but this time the terminal didn't make a fuss.

But! after saving, sudo mount -a returned the line:

[mntent]: line 13 in /etc/fstab is bad

Which had happened the other times I tried altering /etc/fstab. I'm getting the same error when I try mounting the partition from the GUI now.

Did I have to put both the ext3 & vfat UUID lines in?

EDIT - sudo blkid returns:

```
xxxx@xxxx:~$ sudo blkid
/dev/sda1: UUID="df1ed6d1-3bd4-4919-bc19-f67edfcfd37a" TYPE="ext4" 
/dev/sda5: UUID="d80b4a94-0999-4ea9-ad1e-0800ebff9c34" TYPE="swap" 
/dev/sdb1: UUID="450bed29-58d1-497f-b7fa-d068a8809cb1" SEC_TYPE="ext2" TYPE="ext3"
```Pretty sure sdb1 is my new HDD ID

---

### Post by ajgreeny on 2011-07-31
There is a bit of a mixup in the final line of your blkid output where you have both ext2 and ext3 showing.  It is either one or the other, so I think you need to format the partition on your new drive again to ext3.

I have never seen this happen before, so it is a bit baffling as to why this is showing like that this time.  Hopefully a reformat will solve it, though you will need to edit fstab again to get the right UUID, which will have changed.

---

### Post by mccuisinart on 2011-07-31
Ajgreeny! Thanks a lot I figured it out all with your help! Much love.

---

### Post by ajgreeny on 2011-07-31
Just out of interest, what was the problem?  Did a reformat solve it?

---

### Post by Miljet on 2011-07-31
> There is a bit of a mixup in the final line of your blkid output where you have both ext2 and ext3 showing.

That is perfectly normal output for a partition formatted as EXT3. I still have an old EXT3 partition and just checked it.

---

### Post by sisco311 on 2011-07-31
> **Miljet said:**
> That is perfectly normal output for a partition formatted as EXT3. I still have an old EXT3 partition and just checked it.

Indeed it is. ext3 is  compatible to ext2 filesystems. You can look at it as an ext2 filesystem with a journal file.

---

### Post by ajgreeny on 2011-08-01
> **Miljet said:**
> That is perfectly normal output for a partition formatted as EXT3. I still have an old EXT3 partition and just checked it.
Interesting, as I have an external disk formatted to ext3 which does not show that when I run sudo blkid.  See in red below.  That is why I presumed a problem.  Any idea why I don't see it that way on my system?:-
```
/dev/sda1: LABEL="Lucid" UUID="1a3edc2d-4fe7-49e6-8bcc-179e5d5df49f" TYPE="ext4" 
/dev/sda2: LABEL="UbuntuHome" UUID="e2554df2-7e16-4864-97c9-834d8bebecda" TYPE="ext4" 
/dev/sda5: UUID="1bfd912d-b6b6-4a68-9aaf-4139513772ec" TYPE="swap" 
/dev/sdb1: LABEL="Kubuntu" UUID="414fc828-8f60-4f62-9a8e-2b7293b6e964" TYPE="ext4" 
/dev/sdb2: LABEL="Lubuntu" UUID="0a3e01e7-ce77-4397-b72b-4c17c450a872" TYPE="ext4" 
/dev/sdb3: LABEL="Mint11" UUID="09df0b0c-4956-42c1-b939-ed8783ab270c" TYPE="ext4" 
/dev/sdb4: LABEL="Xubuntu" UUID="32fc1cd4-eebe-4931-acd8-96b622c6e316" TYPE="ext4" 
[COLOR=Red]/dev/sdd1: LABEL="Iomega" UUID="f020c7d0-9cef-4142-9269-63d8af2c6b11" TYPE="ext3"[/COLOR]
```

---

### Post by CharlesA on 2011-08-01
> **ajgreeny said:**
> Interesting, as I have an external disk formatted to ext3 which does not show that when I run sudo blkid.  See in red below.  That is why I presumed a problem.  Any idea why I don't see it that way on my system?:-
```
/dev/sda1: LABEL="Lucid" UUID="1a3edc2d-4fe7-49e6-8bcc-179e5d5df49f" TYPE="ext4" 
/dev/sda2: LABEL="UbuntuHome" UUID="e2554df2-7e16-4864-97c9-834d8bebecda" TYPE="ext4" 
/dev/sda5: UUID="1bfd912d-b6b6-4a68-9aaf-4139513772ec" TYPE="swap" 
/dev/sdb1: LABEL="Kubuntu" UUID="414fc828-8f60-4f62-9a8e-2b7293b6e964" TYPE="ext4" 
/dev/sdb2: LABEL="Lubuntu" UUID="0a3e01e7-ce77-4397-b72b-4c17c450a872" TYPE="ext4" 
/dev/sdb3: LABEL="Mint11" UUID="09df0b0c-4956-42c1-b939-ed8783ab270c" TYPE="ext4" 
/dev/sdb4: LABEL="Xubuntu" UUID="32fc1cd4-eebe-4931-acd8-96b622c6e316" TYPE="ext4" 
[COLOR=Red]/dev/sdd1: LABEL="Iomega" UUID="f020c7d0-9cef-4142-9269-63d8af2c6b11" TYPE="ext3"[/COLOR]
```

Different version of Ubuntu, maybe? I haven't used ext3 in a while, but from what I remember, my blkid showed the same as you.

---

### Post by ajgreeny on 2011-08-01
> **CharlesA said:**
> Different version of Ubuntu, maybe? I haven't used ext3 in a while, but from what I remember, my blkid showed the same as you.
I'm on 10.04, as you seem to be.  But, yes, perhaps you're right.  The versions of ubuntu showing these variable outputs may be different.  It is only my external backup disk that is ext3, all the rest are ext4, as you can see.

---

### Post by CharlesA on 2011-08-01
> **ajgreeny said:**
> I'm on 10.04, as you seem to be.  But, yes, perhaps you're right.  The versions of ubuntu showing these variable outputs may be different.  It is only my external backup disk that is ext3, all the rest are ext4, as you can see.

Yep. I moved everything to ext4 a while ago, so I don't have anything to compare it with - that is, unless I want to boot a VM and play around. :p

---

### Post by Miljet on 2011-08-02
I don't think that it has to do with different versions of Ubuntu. I am running 10.04 also. I read something a good while back explaining why EXT3 also shows up as EXT2, but can't remember where I read it. I have done a little searching around but haven't found it yet. I will post it here if, and when, I find it.

---

### Post by Miljet on 2011-08-02
OK, here are a couple of links:
[http://ubuntuforums.org/showthread.php?t=914990](http://ubuntuforums.org/showthread.php?t=914990)
[http://en.wikipedia.org/wiki/Ext3](http://en.wikipedia.org/wiki/Ext3)
I don't believe that either of these are what I originally read, but is the best I can come up with on short notice.

---

### Post by ajgreeny on 2011-08-02
I am sorry to keep this thread going, and I am aware that the OP's problem is now sorted out, but I started this confusion about the ext3/ext2 fstab entry, and yet I still can't see any answer to why some show both ext2 and ext3, and others just show ext3.

There must be a reason, surely, and I am just extremely curious.

Anybody???

---

### Post by Miljet on 2011-08-03
Like you, I am somewhat curious too. Actually we are talking about the output of the "blkid" command, not the fstab file. 

Anyway, I have searched all my Ubuntu books and can not find an explanation. I am beginning to suspect that it depends on the disk type and what information it reports to the system. In other words, an IDE drive vs a SATA drive, or an external vs internal. But I can find absolutely nothing to support that theory.

---

