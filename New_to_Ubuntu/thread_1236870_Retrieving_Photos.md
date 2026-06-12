---
title: "Retrieving Photos"
date: 2009-08-10
forum: New to Ubuntu
---

### Post by daniell59 on 2009-08-10
I have a dual boot. Windows/Ubuntu. I have Ubuntu on one hard drive and windows on the other. I have digital photos stored on the same hard drive that I installed Ubuntu on. This is the problem. I stored the photos using windows Vista. For some reason, I can no longer get into windows. Ubuntu is working fine. Is there a way that I can retrieve the photos using Ubuntu? Thanks

---

### Post by LewRockwell on 2009-08-10
would you like to correct your windows problem if possible?

it might be something fairly simple if you care to relate the difficulty

.

---

### Post by daniell59 on 2009-08-10
> **LewRockwell said:**
> would you like to correct your windows problem if possible?

it might be something fairly simple if you care to relate the difficulty

.

I would love to but I was reluctant to discuss windows problems here.

I have a dual boot. Vista/Ubuntu

I just booted into Vista and it is stuck at Configuring Updates.
Stage 3 of 3 0% complete. It eventually shuts down, and it happens again. I tried it in safe mode, but all I got was the arrow.
A related question. I have two hard drives. One drive has Vista, the other has Ubuntu. The photos are on the hard drive that has Ubuntu but I used Vista to store them. Can I access them using Ubuntu? Also, If I reinstall Vista, what will happen to the Ubuntu?

---

### Post by LewRockwell on 2009-08-10
> **daniell59 said:**
> I would love to but I was reluctant to discuss windows problems here.

I have a dual boot. Vista/Ubuntu

I just booted into Vista and it is stuck at Configuring Updates.
Stage 3 of 3 0% complete. It eventually shuts down, and it happens again. I tried it in safe mode, but all I got was the arrow.
A related question. I have two hard drives. One drive has Vista, the other has Ubuntu. The photos are on the hard drive that has Ubuntu but I used Vista to store them. Can I access them using Ubuntu? Also, If I reinstall Vista, what will happen to the Ubuntu?

to clarify:

you reference TWO hard drives and I wanted to make sure there was no confusion regarding "drives" versus "partitions"

thanks

.

---

### Post by daniell59 on 2009-08-10
> **LewRockwell said:**
> to clarify:

you reference TWO hard drives and I wanted to make sure there was no confusion regarding "drives" versus "partitions"

thanks

.

Two separate hard drives

---

### Post by LewRockwell on 2009-08-10
> **daniell59 said:**
> I have a dual boot. Windows/Ubuntu. I have Ubuntu on one hard drive and windows on the other. I have digital photos stored on the same hard drive that I installed Ubuntu on. This is the problem. I stored the photos using windows Vista. For some reason, I can no longer get into windows. Ubuntu is working fine. Is there a way that I can retrieve the photos using Ubuntu? Thanks

ok, two hard drives

Vista on one(assuming "master" or primary)

Ubuntu on the second(assuming "slave" or secondary)

Photos also on second(probably on a separate storage partition)

Given the above is correct...I see no reason why you shouldn't attempt a repair/recovery of your Vista installation utilizing the functions of the installation media provided by Microsoft or your Original Equipment Manufacturer

After the recovery you will probably find that Vista has overwritten the part of Grub that resides in your MBR but that is not hard to fix with Super Grub Disk or similar corrective actions

.

---

### Post by daniell59 on 2009-08-10
> **LewRockwell said:**
> ok, two hard drives

Vista on one(assuming "master" or primary)

Ubuntu on the second(assuming "slave" or secondary)

Photos also on second(probably on a separate storage partition)

Given the above is correct...I see no reason why you shouldn't attempt a repair/recovery of your Vista installation utilizing the functions of the installation media provided by Microsoft or your Original Equipment Manufacturer

After the recovery you will probably find that Vista has overwritten the part of Grub that resides in your MBR but that is not hard to fix with Super Grub Disk or similar corrective actions

.

Thanks, but can you elaborate. I should use the Installation DVD to do the repair. How do I install GRUB afterwards?

---

### Post by daniell59 on 2009-08-10
> **daniell59 said:**
> Thanks, but can you elaborate. I should use the Installation DVD to do the repair. How do I install GRUB afterwards?

Before I do anything, is there a way to retrieve the photos?

---

### Post by oldfred on 2009-08-10
I am surprised that you cannot see the partition with the photos, did you install ntfs-3g to give you access to windows partitions. If installed you should be able to go to places/computer and in the left pane it will show all the mountable partitions. If not installed ( or use system/administration/synaptic package manager)
sudo apt-get install ntfs-3g

Do not attempt to write anything into the Vista partition until you resolve your boot issue there as it may make it worse. Normally writing to ntfs directories are not an issue.

---

### Post by LewRockwell on 2009-08-10
> **daniell59 said:**
> Before I do anything, is there a way to retrieve the photos?

Ubuntu should mount the partition that contains the photos

.

---

### Post by daniell59 on 2009-08-10
> **oldfred said:**
> I am surprised that you cannot see the partition with the photos, did you install ntfs-3g to give you access to windows partitions. If installed you should be able to go to places/computer and in the left pane it will show all the mountable partitions. If not installed ( or use system/administration/synaptic package manager)
sudo apt-get install ntfs-3g

Do not attempt to write anything into the Vista partition until you resolve your boot issue there as it may make it worse. Normally writing to ntfs directories are not an issue.

I was able to access the  photos, but for some reason I cannot figure out how to copy them to my flash drive. Any assistance would be appreciated. It just says copy location, not just copy

---

### Post by LewRockwell on 2009-08-10
> **daniell59 said:**
> Thanks, but can you elaborate. I should use the Installation DVD to do the repair. How do I install GRUB afterwards?

yes

Vista disk should have some provision for "repairing" and/or "recovery"

grub

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

or there's always this way:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

.

---

### Post by LewRockwell on 2009-08-10
> **daniell59 said:**
> I was able to access the  photos, but for some reason I cannot figure out how to copy them to my flash drive. Any assistance would be appreciated. It just says copy location, not just copy

you may open a window for your flash drive and also the window containing the image files/directories that you wish to copy

select all and then drag and drop them into the flash drive window

.

---

### Post by daniell59 on 2009-08-10
> **LewRockwell said:**
> you may open a window for your flash drive and also the window containing the image files/directories that you wish to copy

select all and then drag and drop them into the flash drive window

.

Thanks
I copied the photos that were most important. What do you think that I should do next. I was thinking of reinstalling Vista. I would rather not however.

---

### Post by LewRockwell on 2009-08-10
> **daniell59 said:**
> Thanks
I copied the photos that were most important. What do you think that I should do next. I was thinking of reinstalling Vista. I would rather not however.

It's up to you really

We would like to see you advance your knowledge and skill level by attempting to resolve your Vista issues without the necessity of complete reinstallation

However, regardless of your attempts, in the end that may be required depending on the specific problem that rendered your Vista installation inoperative

keep us posted on how it goes!

inquiring minds yearn for knowledge!

.

---

### Post by daniell59 on 2009-08-11
> **LewRockwell said:**
> It's up to you really

We would like to see you advance your knowledge and skill level by attempting to resolve your Vista issues without the necessity of complete reinstallation

However, regardless of your attempts, in the end that may be required depending on the specific problem that rendered your Vista installation inoperative

keep us posted on how it goes!

inquiring minds yearn for knowledge!

.

Soon I will attempt to Repair or Re-install windows.  I really do not understand how to restore the GRUB. Perhaps I have too many other things that need my attention.

---

