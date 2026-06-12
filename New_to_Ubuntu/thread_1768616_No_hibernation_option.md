---
title: "No hibernation option"
date: 2011-05-27
forum: New to Ubuntu
---

### Post by beew on 2011-05-27
Hi,
I am running Ubuntu 10.10. Install the package uswsusp. it complains that I don't have a swap partition for hibernation. But I do have a 4G swap partition. So what is it talking about?  I checked power manager settings I have the shut down and suspend options but no hibernation. Tested that suspend apparently works.

Please advise, thanks.

---

### Post by beew on 2011-05-27
Ok, it seems that the swap partition is disabled (swapoff) on reboot. Any solution to that?

Thanks.

---

### Post by beew on 2011-05-27
Bump!

---

### Post by Prince Valiant on 2011-05-27
Idea:

Install gparted, if you don't have it already.

```
sudo apt-get install gparted
```

Once you've opened that, navigate within it to your HD.  Right-click on the swap partition, and select swap on.

Maybe that'll work.  I assume you've got less than 4GB RAM?

Have fun!
-Val

---

### Post by beew on 2011-05-27
> **Prince Valiant said:**
> Idea:

Install gparted, if you don't have it already.

```
sudo apt-get install gparted
```Once you've opened that, navigate within it to your HD.  Right-click on the swap partition, and select swap on.

Maybe that'll work.  I assume you've got less than 4GB RAM?

Have fun!
-Val

I did that before, but swap is disabled again when I reboot.

---

### Post by dnairb on 2011-05-27
It is not enough to merely turn swap on; you also need to check that your system is configured to actually use the swap partition.

First, check the UUID of the swap partition. In terminal:

```
sudo blkid
```

will give an output similar to this:

```
/dev/sda4: UUID="2b37da11-ad70-4ccb-b090-cec4822b788c" TYPE="swap" 
```

Next, check 2 system files. Again, in terminal:

```
gksudo gedit /etc/fstab /etc/initramfs-tools/conf.d/resume
```

and check that the swap's UUID in each is the same as the output from blkid above.

---

### Post by psusi on 2011-05-27
> **ISHRAT said:**
> Install gparted, if you don't have it already.

Code:
sudo apt-get install gparted

Please read threads before posting in them.  This was already suggested and it wasn't appropriate then either.

---

### Post by dnairb on 2011-05-27
> **ISHRAT said:**
> Install gparted, if you don't have it already.

Code:
sudo apt-get install gparted

Oh, for..... It is answers like this that clog up the forum with so much useless info, and turn people off asking for help.
This was already suggested merely 3 posts above yours, and in any case will not help the OP.

---

### Post by beew on 2011-05-27
Hi dnairb

Here is the output for blkid (what does blkid mean??)


> /dev/sda6: UUID="e876c000-8276-4ce1-b7a2-cb0a973e33c8" TYPE="swap" 
On the other hand /etc/fstab /etc/initramfs-tools/conf.d/resume looks like this

> # swap was on /dev/sda6 during installation
UUID=dd45a5df-44de-4d02-bf16-8e96a4caffe3 none            swap    sw              0       0

I have actually moved the swap partition after installed, maybe that  caused the problem. How should I edit  /etc/fstab  /etc/initramfs-tools/conf.d/resume ?

Thanks.

---

### Post by dnairb on 2011-05-27
You should have 2 files open now in gedit: **/etc/fstab** and **/etc/initramfs-tools/conf.d/resume**

---

### Post by beew on 2011-05-27
> **dnairb said:**
> You should have 2 files open now in gedit: **/etc/fstab** and **/etc/initramfs-tools/conf.d/resume**

Ok, sorry that was fstab above, resume looks like this

> RESUME=UUID=dd45a5df-44de-4d02-bf16-8e96a4caffe3

---

### Post by dnairb on 2011-05-27
OK. 

The output from blkid gave us the actual UUID for the swap partition.
The 2 system files are looking for a partition with a different (non-existing) UUID, and hence swap is not being used.

You need to edit them thus:

change the lines in /etc/fstab to:

```
# swap was on /dev/sda6 during installation
UUID=e876c000-8276-4ce1-b7a2-cb0a973e33c8 none swap sw 0 0

```

and in /etc/initramfs-tools/conf.d/resume:

```
RESUME=UUID=e876c000-8276-4ce1-b7a2-cb0a973e33c8
```

When you have edited and saved these files, reboot and all should be good.

---

### Post by beew on 2011-05-27
Hi, following your instruction swap is actually activated on reboot.

But hibernation still doesn't work (the option does show up in power manager), when I try to awake the system from hibernation I see the purple splash screen with the ubuntu logo and 5 dots but it got stuck at 4 dots so I have to reboot it.

 I have close to 3 G of ram but I have set swap to 4 G, maybe I should increase it to 6 G and then edit fstab and resume again?

Thanks again.

---

### Post by dnairb on 2011-05-27
OK, just to check, can you check /etc/fstab and /etc/initramfs-tools/conf.d/resume again to ensure that the UUIDs are correct.

---

### Post by beew on 2011-05-27
> **dnairb said:**
> OK, just to check, can you check /etc/fstab and /etc/initramfs-tools/conf.d/resume again to ensure that the UUIDs are correct.

Hi, they all match.

---

### Post by dnairb on 2011-05-27
OK. 

That's as far as I can go with this I'm afraid. The swap is now working OK, but your machine won't wake from hibernate properly - I don't know how to fix this.

---

### Post by beew on 2011-05-27
> **dnairb said:**
> OK. 

That's as far as I can go with this I'm afraid. The swap is now working OK, but your machine won't wake from hibernate properly - I don't know how to fix this.

Ok, this fine. But thanks for restoring the swap and teaching me something new. :)

P.S. Suspension, however, works flawlessly.

---

### Post by dnairb on 2011-05-27
You're welcome.

Suspend and hibernate work in a similar way, except that suspend uses RAM memory and hibernate use the physical hard-disk swap space.

It may be an idea to mark this thread as "Solved" as the initial problem of hibernation/swap is solved.
You could then start a new thread entitled "Unable to wake from hibernate" for example, and give more detail as to hardware, etc. You may then find that other people with more knowledge pick up on this and are able to help.

---

### Post by QLee on 2011-05-27
Try rebuilding your initrd.img with update-initramfs, it's that image that has the hook to your resume and it was written with the wrong swap UUID in the resume file, now that you have corrected, you need to do the update.

---

### Post by beew on 2011-05-27
> **QLee said:**
> Try rebuilding your initrd.img with update-initramfs, it's that image that has the hook to your resume and it was written with the wrong swap UUID in the resume file, now that you have corrected, you need to do the update.

How do you do that? like run sudo update-initramfs?

---

### Post by beew on 2011-05-27
> **dnairb said:**
> You're welcome.

Suspend and hibernate work in a similar way, except that suspend uses RAM memory and hibernate use the physical hard-disk swap space.

It may be an idea to mark this thread as "Solved" as the initial problem of hibernation/swap is solved.
You could then start a new thread entitled "Unable to wake from hibernate" for example, and give more detail as to hardware, etc. You may then find that other people with more knowledge pick up on this and are able to help. 

Hi, I think I am going to wait a bit before starting a new thread as the solution may be very close. But I will keep that in mind.

---

### Post by dnairb on 2011-05-27
> **beew said:**
> Hi, I think I am going to wait a bit before starting a new thread as the solution may be very close. But I will keep that in mind.

That's cool. Actually I think that QLee may be on to something. The command you need is:

```
sudo update-initramfs -u
```

Then reboot.

The "-u" option updates an existing initramfs file.

---

### Post by beew on 2011-05-27
> **dnairb said:**
> That's cool. Actually I think that QLee may be on to something. The command you need is:

```
sudo update-initramfs -u
```Then reboot.

The "-u" option updates an existing initramfs file.


Hi, I ran the command and got a warning
> found more than one resume device candidate:
                     /dev/sda6
                     UUID=e876c000-8276-4ce1-b7a2-cb0a973e33c8


And when I tried to resume I was stuck but this time there is a message on the screen that says
> 
Resuming from /dev/disk/by-uuid/e876c000-8276-4ce1-b7a2-cb0a973e33c8

So there is some progress.

P.S  Thanks to QLee too.

---

### Post by dnairb on 2011-05-27
OK. We need to check those files again.

Please post the **full** output of:

```
gksudo gedit /etc/fstab
```

and 

```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```

and 

```
sudo blkid
```

---

### Post by beew on 2011-05-27
Hi,

Here they are

> ~$ sudo blkid
/dev/sda1: UUID="F8ACBC29ACBBE074" TYPE="ntfs" 
/dev/sda2: UUID="af9073f4-f16c-4285-8acc-01373932dbcc" TYPE="ext4" 
/dev/sda5: UUID="7e5b410b-27e1-43c6-98c7-2df2cbe8dbd5" TYPE="ext4" 
/dev/sda6: UUID="e876c000-8276-4ce1-b7a2-cb0a973e33c8" TYPE="swap" 



fstab

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda2 during installation
UUID=af9073f4-f16c-4285-8acc-01373932dbcc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda5 during installation
UUID=7e5b410b-27e1-43c6-98c7-2df2cbe8dbd5 /home           ext4    defaults        0       2
# swap was on /dev/sda6 during installation
UUID=e876c000-8276-4ce1-b7a2-cb0a973e33c8 none            swap    sw              0       0


resme

> RESUME=UUID=e876c000-8276-4ce1-b7a2-cb0a973e33c8

---

### Post by dnairb on 2011-05-28
OK. Those files are all OK; there is **another** file to check it seems.

Can you check 

```
gksudo gedit /etc/uswsusp.conf
```

which was created when you installed uswsusp

---

### Post by beew on 2011-05-28
Hi,

Here it is 
> # /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/sda6
compress = y
early writeout = y
image size = 1456011018
RSA key file = /etc/uswsusp.key
shutdown method = platform


---

### Post by dnairb on 2011-05-28
Thank you.

The resume file is telling the system to resume from UUID=e876c000-8276-4ce1-b7a2-cb0a973e33c8  and the uswsusp.conf file says to use /dev/sda6. These are the same partitions, but the system reads as them as different.

Did hibernate work before you changed the swap file, I wonder? It may be that you don't actually need uswsusp.

---

### Post by beew on 2011-05-28
> **dnairb said:**
> Thank you.

The resume file is telling the system to resume from UUID=e876c000-8276-4ce1-b7a2-cb0a973e33c8  and the uswsusp.conf file says to use /dev/sda6. These are the same partitions, but the system reads as them as different.

Did hibernate work before you changed the swap file, I wonder? It may be that you don't actually need uswsusp.

I haven't really used hibernation before changing the swap partition (actually I was expanding my /home partition and had to change swap by moving it to the end). When I noticed that hibernation was missing in the power manager (I use suspend sometimes but not often).Then I installed the package "hibernation" and uswsusd was installed along with it, during install (still in Synaptic) it said I didn't have a swap partition. I found that pretty strange, which was what started this thread.

So is there a way to fix it? Thanks again for the patience.

---

### Post by dnairb on 2011-05-28
OK.

We have 2 options available.

You can keep uswsusp installed, but change the **/etc/uswsusp.conf** file to use a disk identified by its UUID:

Change 

```
resume device = /dev/sda6
```

to

```
resume device = /dev/disk/by-uuid/e876c000-8276-4ce1-b7a2-cb0a973e33c8
```


Another option is to remove hibernate and uswsusp. The easiest way is using terminal:

```
sudo apt-get purge hibernate uswsusp
```

The purge option should remove configuration files as well.

After this, check if the /etc/uswsusp.conf file has been removed.
If not, again in terminal

```
sudo rm /etc/uswsusp.conf
```



Whichever method you choose, rerun update-initramfs:

```
sudo update-initramfs -u
```

reboot, and cross your fingers!

---

### Post by beew on 2011-05-28
Hi,

I removed uswsusp and hibernate and it worked! I just woke up from a hibernation. I tried this while on battery and on AC (initramfs was updated automatically when the packages were purged)

It is strange that I don't need the hibernate package for hibernation.

Many thanks for the walk through! I will mark this thread as solved.

---

### Post by dnairb on 2011-05-28
Brilliant! You're welcome. Big thanks to QLee also for pointing out that the initramfs needed to be updated.

I believe that the hibernate and uswsusp applications are mainly for older systems. Hibernate and suspend on more modern systems should work out-of-the-box.

---

### Post by QLee on 2011-05-28
[QUOTE=dnairb]... Big thanks to QLee also for pointing out that the initramfs needed to be updated.
...[/QUOTE]

That little hint was all you needed to get you moving again, beew is not a n00b and you clearly understand this stuff. Now you and all the lurkers may remember the issue for future troubleshooting. 

One of the worst things about this issue is that if there was a kernel upgrade and a new initrd.img was generated by the configuration scripts then the problem would have disappeared as if by magic. It's much better that you figured it out.
[Edit] At least that would have happened if other hibernation software hadn't been installed before the problem of not hibernating was tracked down.

---

