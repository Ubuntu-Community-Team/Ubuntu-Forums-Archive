---
title: "Swap and 9.04. Not sure mine is set up properly"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by kendoori on 2009-06-05
I had started my Ubuntu experiment using Wubi, which have since moved to a real install on a dedicated partition (still have XP on another partition). I had initially installed 8.10, and have since upgrade to 9.04.

I've always been suspicious regarding my swap settings, but don't have the experience to verify whether my system is setup optimally. I have 4GB of RAM on this machine.

I recently tried to hibernate for this first time and came up with the error, "cannot find swap device, try swapon -a"

This made me want to investigate whether I had swap properly set up.

In Gparted, I show that I have a partition called /dev/sda4 with a file system of linux-swap, with a size of 4.79 GiB

I was considering blowing away the swap and recreating, but could use some step by step. 

1-Need to determine whether what I have is set up properly
2-Need to make hibernate work

Here is the copy of my fstab
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc     defaults                    0  0  
# /dev/sda3
UUID=fd4efedd-2c88-458f-9a77-308a3a7b01b6  /            ext3     defaults,errors=remount-ro,relatime  0  1  
# /dev/sda2
UUID=AA60CDB060CD8413                      /media/drv0  ntfs-3g  defaults                    0  0  


# /dev/sda4
UUID=5c858742-e41d-410f-afe0-ca5b978c882f  none         swap     sw                          0  0  

/dev/sda2                                  /media/sda2  ntfs     defaults                    0  0  
/dev/sda1                                  /media/My Documents  ntfs     nls=iso8859-1,umask=000     0  0  
/dev/sda1                                  /media/sda1  ntfs     defaults                    0  0  
/dev/sda3                                  /media/sda3  ext3     defaults,relatime                    0  0  
/dev/sda4                                  /media/sda4  swap     defaults                    0  0  





```

---

### Post by Kareeser on 2009-06-05
Have you tried "swapon -a"? It's right in the error message.

---

### Post by drs305 on 2009-06-05
Try turning on swap as suggested above (sudo swapon -a), then run:
```
free -m
```
Does it return values other than zero?

First, you have an unnecessary line in fstab. Backup fstab and open for editing:
```

sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab

```

Remove this line:
> /dev/sda4                                  /media/sda4  swap     defaults                    0  0

Next, check that the UUIDs match between various system files. 
Your fstab says it is:
**5c858742-e41d-410f-afe0-ca5b978c882f**

Use these two commands to verify the correct settings. *Also confirm the swap partition is sda4.* 
```

cat /etc/initramfs-tools/conf.d/resume  # check swap UUID in 'resume'
sudo blkid -c /dev/null | grep "swap"   # check system UUID for swap

```


If they don't all match, you can run the following commands to make sure swap's UUID is the same as the one contained in fstab:
```

sudo swapoff -a    # turns off all current swap files/partitions
sudo mkswap -U "5c858742-e41d-410f-afe0-ca5b978c882f" /dev/sda4  # sets swap UUID to match fstab entry
sudo update-initramfs -uk all  # Updates 'resume' 
sudo swapon -a    # Restore swap with new fstab settings
free -m   # Check swap

```

---

### Post by kendoori on 2009-06-05
Thanks greatly for the detailed how-to; however, still getting 
```

Cannot find swap device, try swapon -a

```
In case this helps, below find various output messages regarding my current system state. It looks like "resume" doesn't match properly UUID wise, but I did follow your steps in sequence, so not sure how to reconcile this.[B]

Results of free -m after the modifications suggested and reboot
[/B]```

             total       used       free     shared    buffers     cached
Mem:          3015        594       2420          0         22        193
-/+ buffers/cache:        379       2636
Swap:         4902          0       4902


```

**Results of cat /etc/initramfs-tools/conf.d/resume  # check swap UUID in 'resume'**
```

RESUME=UUID=fd4efedd-2c88-458f-9a77-308a3a7b01b6

```

**Results of sudo blkid -c /dev/null | grep "swap"   # check system UUID for swap**
```

/dev/sda4: UUID="5c858742-e41d-410f-afe0-ca5b978c882f" TYPE="swap"

```


**Edited Fstab (after reboot)**
```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc     defaults                    0  0  
# /dev/sda3
UUID=fd4efedd-2c88-458f-9a77-308a3a7b01b6  /            ext3     defaults,errors=remount-ro,relatime  0  1  
# /dev/sda2
UUID=AA60CDB060CD8413                      /media/drv0  ntfs-3g  defaults                    0  0  


# /dev/sda4
UUID=5c858742-e41d-410f-afe0-ca5b978c882f  none         swap     sw                          0  0  

/dev/sda2                                  /media/sda2  ntfs     defaults                    0  0  
/dev/sda1                                  /media/My Documents  ntfs     nls=iso8859-1,umask=000     0  0  
/dev/sda1                                  /media/sda1  ntfs     defaults                    0  0  
/dev/sda3                                  /media/sda3  ext3     defaults,relatime                    0  0 

```

---

### Post by drs305 on 2009-06-05
Ok, we can just update the resume UUID manually.
Open the following and change the UUID:
```

sudo swapoff -a
gksudo gedit /etc/initramfs-tools/conf.d/resume

```

Once you have saved the file, update the initramfs:
```

sudo update-initramfs -uk all
sudo swapon -a

```

Note that the middle value of the "free -m" command can be 0 and not be an error. If the swap partition/file exists but is not currently needed/in use this value could very well be 0.

---

### Post by kendoori on 2009-06-05
Much thanks, this worked... and of course, I learned something along the way.

---

### Post by killabee44 on 2009-06-06
Guys, I was gonna start a new thread, but this one is on the same subject...

I installed kubuntu on a machine for a friend and everything was working fine. The kubuntu install worked great and really fast.

It is a dual boot machine with xp. While in XP I was resizing some partitions and realized that I made the swap partition too large, so I resized it down to 2 gb. I did this with Acronis Director while in windows.

Now the pc is SUPER SLOW. Htop shows that the swap is 92/92 so im sure that is the culprit.

When I resized the swap partition something must have got messed up (I won't be doing that again! lol..).

Anyhow, here is more info:

This PC only has 512mb of ram.

Free -m:

```

             total       used       free     shared    buffers     cached
Mem:           371        365          5          0          1         45
-/+ buffers/cache:        318         52
Swap:           92         92          0

```

fstab:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=5d6b2402-09d9-4472-afe1-e2539440d43d /               ext3    relatime,errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=da420759-3f45-46fd-a1d7-45de8be9bdf2 /home           ext3    relatime        0       2
# swap was on /dev/sda5 during installation
UUID=f25300dc-6e79-449a-8287-527a99cb952c none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

cat /etc/initramfs-tools/conf.d/resume  # check swap UUID in 'resume':
```
RESUME=UUID=f25300dc-6e79-449a-8287-527a99cb952c
```


sudo blkid -c /dev/null | grep "swap"   # check system UUID for swap:
```
/dev/sda6: TYPE="swap" 
/dev/ramzswap0: TYPE="swap"

```

Thanks for any help given!

---

### Post by drs305 on 2009-06-06
The fstab and resume swap UUIDs match, so that is good. Now you can't trust the comments in fstab since they are static and won't change when UUIDs might, but the fstab comment indicates that, at least at one time, swap was sda5. 

The grep command now says it is sda6. So check your partitions and size. What is the size of sda6?

Please post the results of:
```

sudo fdisk -l  # lower case L
sudo blkid     # since we may be changing UUIDs

```

---

### Post by killabee44 on 2009-06-06
sudo fdisk -l  # lower case L:
```


Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/sda2   *         833       10650    74224080    7  HPFS/NTFS
/dev/sda3           10651       13233    19527480   83  Linux
/dev/sda4           13234       20673    56246399+   5  Extended
/dev/sda5           13234       20155    52330257   83  Linux
/dev/sda6           20397       20673     2094088+  82  Linux swap / Solaris
```


sudo blkid:

```
/dev/sda1: LABEL="PRESARIO_RP" UUID="4289-681C" TYPE="vfat" 
/dev/sda5: UUID="da420759-3f45-46fd-a1d7-45de8be9bdf2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 
/dev/sda2: UUID="D610AFDD10AFC33B" LABEL="PRESARIO" TYPE="ntfs" 
/dev/sda3: UUID="5d6b2402-09d9-4472-afe1-e2539440d43d" TYPE="ext3" 

```

---

### Post by drs305 on 2009-06-06
For some reason, your swap partition does not appear to have a UUID. It does seem to be approximately 2GB, as you planned. Perhaps the reported swap is the ramzswap, which I am not familiar with.

So let's give sda6 a UUID:
```

sudo swapoff -a
sudo mkswap -U "f25300dc-6e79-449a-8287-527a99cb952c" /dev/sda6
sudo blkid -c /dev/null | grep "swap"

```
The UUID of this command, fstab and resume should now all be the same.

Turn on swap, and check the results:
```

sudo swapon -a
free -m

```

---

### Post by killabee44 on 2009-06-06
sudo swapoff -a: gave me an error. Should I continue with the rest of the commands?


```
swapoff: /dev/ramzswap0: Cannot allocate memory
```

---

### Post by drs305 on 2009-06-06
> **killabee44 said:**
> sudo swapoff -a: gave me an error. Should I continue with the rest of the commands?


```
swapoff: /dev/ramzswap0: Cannot allocate memory
```

Try running this to turn off sda6:
```

sudo swapoff /dev/sda6

```

I suspect your sda6 is not working/mounted. You can open also run gparted and right click on sda6. You can see whether the "swapoff" option is available. If it is, select it.

Run the remainder of the commands after checking the above. If the sda6 swap was working properly you would be able to turn it off.

---

### Post by killabee44 on 2009-06-06
sudo swapoff /dev/sda6: Now I get: 

```
swapoff: /dev/sda6: Invalid argument
```

---

### Post by drs305 on 2009-06-06
> **killabee44 said:**
> sudo swapoff /dev/sda6: Now I get: 

```
swapoff: /dev/sda6: Invalid argument
```

That is ok. In this case it just means sda6 is not being used as swap. You can check in gparted but go ahead and run the 'mkswap' and following commands.

---

### Post by killabee44 on 2009-06-07
[I]sudo mkswap -U "f25300dc-6e79-449a-8287-527a99cb952c" /dev/sda6
[/I]
gave me:

```
Setting up swapspace version 1, size = 2094084 KiB
no label, UUID=f25300dc-6e79-449a-8287-527a99cb952c
```


*sudo blkid -c /dev/null | grep "swap"*

gave me:

```
/dev/sda6: UUID="f25300dc-6e79-449a-8287-527a99cb952c" TYPE="swap" 
/dev/ramzswap0: TYPE="swap" 

```

*free -m*  gave me:
```

 total       used       free     shared    buffers     cached
Mem:           371        338         33          0          3         75
-/+ buffers/cache:        258        112
Swap:         2137         92       2045

```

*sudo fdisk -l*    now gives me:

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
240 heads, 63 sectors/track, 20673 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         832     6289888+   c  W95 FAT32 (LBA)
/dev/sda2   *         833       10650    74224080    7  HPFS/NTFS
/dev/sda3           10651       13233    19527480   83  Linux
/dev/sda4           13234       20673    56246399+   5  Extended
/dev/sda5           13234       20155    52330257   83  Linux
/dev/sda6           20397       20673     2094088+  82  Linux swap / Solaris

```

and *sudo blkid*  gives me:

```
/dev/sda1: LABEL="PRESARIO_RP" UUID="4289-681C" TYPE="vfat" 
/dev/sda5: UUID="da420759-3f45-46fd-a1d7-45de8be9bdf2" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="f25300dc-6e79-449a-8287-527a99cb952c" 
/dev/ramzswap0: TYPE="swap" 
/dev/sda2: UUID="D610AFDD10AFC33B" LABEL="PRESARIO" TYPE="ntfs" 
/dev/sda3: UUID="5d6b2402-09d9-4472-afe1-e2539440d43d" TYPE="ext3"
```

How does that look?

Seems to be ok now. Feels fast as before and Htop shows Swp 92/2137

Thanks a lot!

---

### Post by drs305 on 2009-06-07
> **killabee44 said:**
> [I]
How does that look?
Seems to be ok now. Feels fast as before and Htop shows Swp 92/2137
Thanks a lot!

Yes, it looks good as far as your normal swap goes. 

I am unfamiliar with the ramzswap0 and if it is necessary/desired. I'd be curious to know what app created it and how it got into fstab, but those are probably questions I can search the Internet for answers. Don't take this post to mean you should continue to pursue the ramzswap0 issue ...

Glad the instructions worked for you.

---

