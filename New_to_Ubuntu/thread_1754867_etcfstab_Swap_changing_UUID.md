---
title: "/etc/fstab Swap changing UUID?"
date: 2011-05-10
forum: New to Ubuntu
---

### Post by Chrissd on 2011-05-10
Hi all,

I have recently lost my swap space, as found in 'free' and conky. My swap seems to no longer have the same UUID since I amended /etc/fstab to use it. How do I find out if I have a swap file or a swap partition, and would a swap file appear to have a UUID?

Is there an easy way to fix it?

fdisk -l shows:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1698    13631488   27  Unknown
/dev/sda2            1698        2220     4194304    c  W95 FAT32 (LBA)
/dev/sda3   *        2220        2233      102400    7  HPFS/NTFS
/dev/sda4            2233       30402   226268161    f  W95 Ext'd (LBA)
/dev/sda5            2233        8634    51415040    7  HPFS/NTFS
/dev/sda6            8634       30020   171782144   83  Linux
/dev/sda7           30020       30402     3068928   82  Linux swap / Solaris
```

ls /dev/disk/by-uuid shows:
```
3236670B3666D001                      9d9642f1-2888-4cff-80c5-68c6a3c1c451
7ca8a3dc-3688-4c27-9d0b-f6e58ed781d6  AC9C654A9C65105E
8C6663E56663CF10                      C291-9987
```

/etc/fstab shows:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=7ca8a3dc-3688-4c27-9d0b-f6e58ed781d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
#UUID=506da7e6-61ff-4302-be24-ed6f0e17830a none            swap    sw              0       0
UUID=8d8135f8-ffd2-469f-b0d5-12984145ed9e none swap sw 0 0
```

---

### Post by Elfy on 2011-05-10
Well the uuid for the swap in fstab does not appear in the uuid list.

Do ```
ls -al /dev/disk/by-uuid
```

Find the right UUID - change fstab, save and do ```
sudo swapon -a
```

If there's nothing from the terminal you should have swap, check with ```
free -m
```


Edit - if you hibernate then you'll need to check into [https://help.ubuntu.com/community/UsingUUID#Resuming%20from%20Hibernation](https://help.ubuntu.com/community/UsingUUID#Resuming%20from%20Hibernation)

---

### Post by Chrissd on 2011-05-10
Hi and thanks for the reply.

The first command displays
```

drwxr-xr-x 2 root root 160 2011-05-06 07:52 .
drwxr-xr-x 6 root root 120 2011-05-06 08:51 ..
lrwxrwxrwx 1 root root  10 2011-05-06 07:52 3236670B3666D001 -> ../../sda5
lrwxrwxrwx 1 root root  10 2011-05-06 07:52 7ca8a3dc-3688-4c27-9d0b-f6e58ed781d6 -> ../../sda6
lrwxrwxrwx 1 root root  10 2011-05-06 07:52 8C6663E56663CF10 -> ../../sda1
lrwxrwxrwx 1 root root  10 2011-05-06 07:52 9d9642f1-2888-4cff-80c5-68c6a3c1c451 -> ../../dm-0
lrwxrwxrwx 1 root root  10 2011-05-06 07:52 AC9C654A9C65105E -> ../../sda3
lrwxrwxrwx 1 root root  10 2011-05-06 07:52 C291-9987 -> ../../sda2

```

sda7 was showing as the swap earlier, but it's not listed there? ](*,)

---

### Post by wilee-nilee on 2011-05-10
try this, you will see why with mine.
sudo blkid

```
$ sudo blkid
[sudo] password for some name: 
/dev/sda1: LABEL="Windows 7" UUID="6A187E5E62FFEAF6" TYPE="ntfs" 
/dev/sda5: LABEL="Maverick" UUID="833abb84-d08c-4870-9928-8b0c596d0708" TYPE="ext4" 
/dev/sda6: LABEL="Oneiric" UUID="35a5ba64-be6c-4a7a-987c-fc36a3eeddfb" TYPE="ext4" 
/dev/sda7: UUID="635e6c71-750d-46dd-9cc5-73181f751181" TYPE="ext4" 
/dev/sda8: UUID="e837960a-ef85-4c12-a24a-50cbdcf9a3c0" TYPE=**"swap"**
```

---

### Post by Elfy on 2011-05-10
I've had similar happen a while ago. To be honest I just booted a livecd - used gparted to delete what was 'there but not' and recreated it in the same space. 

Got the new uuid and edited fstab. Took about 10 minutes in all.

You could though use a swapfile instead of a swap partition - depends on the need for hibernate/suspend. [https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?](https://help.ubuntu.com/community/SwapFaq#How%20do%20I%20add%20more%20swap?)


Edit - if you actually look at your original uudi information in post#1 there is only 6 uuid's there too.

---

### Post by Chrissd on 2011-05-10
Hi, sudo blkid displayed:

```
/dev/sda1: LABEL="PQSERVICE" UUID="8C6663E56663CF10" TYPE="ntfs" 
/dev/sda2: UUID="C291-9987" TYPE="vfat" 
/dev/sda3: LABEL="SYSTEM RESERVED" UUID="AC9C654A9C65105E" TYPE="ntfs" 
/dev/sda5: LABEL="Acer" UUID="3236670B3666D001" TYPE="ntfs" 
/dev/sda6: UUID="7ca8a3dc-3688-4c27-9d0b-f6e58ed781d6" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="9d9642f1-2888-4cff-80c5-68c6a3c1c451" TYPE="swap"
```

Now I'm really confused. fdisk shows it as sda7, but that now shows it as /dev/mapper/cryptswap1

Is that why the UUID changed? In fstab should I change the UUID=bit to /dev/mapper/cryptswap1 ?

---

### Post by Chrissd on 2011-05-10
I currently use suspend successfully even with no swap working, for what it's worth.

I have changed the UUID in fstab and all is working now, but I'm really baffled as to **how** and **why** the UUID changed. If I understand those factors, I can prevent it happening again.

---

### Post by wilee-nilee on 2011-05-10
You have encrypted your set up it look like.

As far as a regular swap I have done the same as forestpiskie.;)

I saw another user with the same problem, the swap showed unallocated in gparted take a look. They did the wipe and re make a few times and got it back, but I wondered if it was really working within the encryption.

---

### Post by Elfy on 2011-05-10
> **Chrissd said:**
> I have changed the UUID in fstab and all is working now, but I'm really baffled as to **how** and **why** the UUID changed. If I understand those factors, I can prevent it happening again.

To answer that it would depend on what you've done recently.

Glad you got it working at least.

---

### Post by geazzy on 2011-05-10
> **wilee-nilee said:**
> try this, you will see why with mine.
sudo blkid

```
$ sudo blkid
[sudo] password for some name: 
/dev/sda1: LABEL="Windows 7" UUID="6A187E5E62FFEAF6" TYPE="ntfs" 
/dev/sda5: LABEL="Maverick" UUID="833abb84-d08c-4870-9928-8b0c596d0708" TYPE="ext4" 
/dev/sda6: LABEL="Oneiric" UUID="35a5ba64-be6c-4a7a-987c-fc36a3eeddfb" TYPE="ext4" 
/dev/sda7: UUID="635e6c71-750d-46dd-9cc5-73181f751181" TYPE="ext4" 
/dev/sda8: UUID="e837960a-ef85-4c12-a24a-50cbdcf9a3c0" TYPE=**"swap"**
```

thanks for useful command...
I usually see the UUID with gparted :D

---

### Post by Chrissd on 2011-05-11
Hi,

Booted computer this morning and the UUID has changed again. What options do I have to use something other than the UUID?

Thanks

---

### Post by Elfy on 2011-05-11
You could try with /dev/blah

either 

/dev/sda8 or 
/dev/mapper/cryptswap1

Found this yesterday that might help a bit - [http://ubuntuforums.org/showthread.php?t=1120614](http://ubuntuforums.org/showthread.php?t=1120614) - you can see there that the OP of that thread is using /dev/mapper/cryptblah in their fstab.


Edit - wondering if there's something else going on as I've just seen another thread along similar lines - [http://ubuntuforums.org/showthread.php?t=1755248](http://ubuntuforums.org/showthread.php?t=1755248)

---

### Post by Chrissd on 2011-05-11
I've changed my fstab again. I now have for

cat /proc/swaps
```
Filename				Type		Size	Used	Priority
```

So does that mean my swap isn't working? Apparently I should get something like
> and you should get something like this outputted in the first column.
Quote:
Filename
/dev/mapper/cswap 

I'm sorry to be so confused here.

---

### Post by Elfy on 2011-05-11
swap's not working I'd say.

Please  run these and post the results
```
cat /etc/fstab
sudo blkid
cat /var/log/messages |grep swap
cat /var/log/dmesg |grep swap
```

---

### Post by Chrissd on 2011-05-11
Fstab
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=7ca8a3dc-3688-4c27-9d0b-f6e58ed781d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
#UUID=506da7e6-61ff-4302-be24-ed6f0e17830a none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

blkid
```
/dev/sda1: LABEL="PQSERVICE" UUID="8C6663E56663CF10" TYPE="ntfs" 
/dev/sda2: UUID="C291-9987" TYPE="vfat" 
/dev/sda3: LABEL="SYSTEM RESERVED" UUID="AC9C654A9C65105E" TYPE="ntfs" 
/dev/sda5: LABEL="Acer" UUID="3236670B3666D001" TYPE="ntfs" 
/dev/sda6: UUID="7ca8a3dc-3688-4c27-9d0b-f6e58ed781d6" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="6d6024cf-a231-484a-9fb0-2413e14b518e" TYPE="swap"
```

---

### Post by Elfy on 2011-05-11
That looks ok I think - never bothered encrypting anything to be honest so this is new one to me.

I assume that the 2 other commands didn't give a result.

What does this return?

```
cryptsetup status cswap
```

Copied that command from the thread I referred to earlier - so it might need cryptswap1 instead of cswap

---

### Post by Chrissd on 2011-05-11
Ah ha! Using cswap produced nothing, so as you suggested swapped it for cryptswap1

```
/dev/mapper/cryptswap1 is active:
  cipher:  aes-cbc-essiv:sha256
  keysize: 256 bits
  device:  /dev/sda7
  offset:  0 sectors
  size:    6137856 sectors
  mode:    read/write

```

Guess it is working then?

---

### Post by Elfy on 2011-05-11
I'd have to assume so. 

Does free -m show it?

---

### Post by Chrissd on 2011-05-12
Aye it does, guess regardless how many times the UUID of my swap changes, it won't happen again as I've referred to it by name this time?

```
             total       used       free     shared    buffers     cached
Mem:           987        863        124          0         40        359
-/+ buffers/cache:        464        523
Swap:            0          0          0

```

---

### Post by Elfy on 2011-05-12
I'm lost then - need to look into all this encrypted stuff I think.

As far as free is concerned you've no swap - whether that's because it's encrypted is something I'm not at all sure of.

---

### Post by Chrissd on 2011-05-12
Is there a recommended guide to follow where I can create new encrypted swap?

Thanks

---

### Post by Elfy on 2011-05-12
> **Chrissd said:**
> Is there a recommended guide to follow where I can create new encrypted swap?

Thanks

Not sure - looking into to it  - slowly ...

---

### Post by Elfy on 2011-05-12
One last thing - try

```
sudo swapon -a
free -m
```

Is it there now?

---

### Post by Chrissd on 2011-05-12
Hi,

sudo swapon -a
```
swapon: /dev/mapper/cryptswap1: swapon failed: Device or resource busy
```

free -m
```
             total       used       free     shared    buffers     cached
Mem:           987        960         27          0         14        514
-/+ buffers/cache:        431        556
Swap:         2996         36       2960
```

Strange but worked! Will literally reboot now to ensure that it works after reboot. Fingers crossed by the time you read this, there'll be a happy post from me below.

---

### Post by Chrissd on 2011-05-12
Looks like I can gladly mark this thread as solved!

I'm very grateful for the help you have provided, truly it's people like you that make Ubuntu Linux a success!

I'm so very grateful, thank you so much!

Chrissd

---

### Post by Elfy on 2011-05-12
> **Chrissd said:**
> Looks like I can gladly mark this thread as solved!

I'm very grateful for the help you have provided, truly it's people like you that make Ubuntu Linux a success!

I'm so very grateful, thank you so much!

Chrissd

Glad it's sorted at least :)

> truly it's people like you that make Ubuntu Linux a success!I'd not say that - I floundered somewhat with the encrypted bits :p

---

### Post by Chrissd on 2011-05-12
[QUOTE=forestpiskie]
I'd not say that - I floundered somewhat with the encrypted bits :p[/QUOTE]

At least you didn't resort to the last piece of Windows advice I had: Format and reinstall. 

That was a few years ago now and haven't used it since. :lol:

---

### Post by skypuppy on 2011-05-12
Why in the pooh are the developers writing the UUID info in the basic code in the first place?  That locks one into specific hard drives.  That's crazy unless you are using an OS that is "locked" which Linux cannot be.

---

### Post by egalvan on 2011-05-15
> **skypuppy said:**
> Why in the pooh are the developers writing the UUID info in the basic code in the first place?

Don't know what "basic code" you refer to.


>   That locks one into specific hard drives.  That's crazy unless you are using an OS that is "locked" which Linux cannot be.

Using UUID no more "locks" you into anything any more than any other form of ID, such as a disk name...

**UUID** stands for **U**niversally **U**nique **ID**.
the theory is that it gives each partition a unique, never-to-be-repeated-again-in-the-life-of-this-universe-or-changed, name, or ID.
Kinda like DNA or fingerprints.
This UUID never changes, no matter what OS reads it, or what order its found/mounted.
The **hdx/sdx** paradigm was variable, depending on the order the drives were found, how many, what type, etc.
**sdb** may not be **sdb** if the USB pen drive is not installed when the drives are scanned and mounted.

Since each partition has a unique, never-changing name, your (or the software) will never mistake **one** partition for another one,
The theory is softened somewhat by the fact that you can read **and write** the UUID to your heart's content.

Don't like the UUID your partition has? Write a new one.
Call it Bob.
just don't be surprised if a second Bob shows up at the party.
Or if the Bob wants to be introduced as Robert.  :)

---

