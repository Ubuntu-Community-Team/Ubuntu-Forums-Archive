---
title: "Automatically force mount?"
date: 2009-04-12
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-12
Is there a way I can make Ubuntu automatically force mount a USB drive if it can't mount it normally? as it's kind of embarrassing faffing around trying to mount a USB pendrive when your showing off you new Ubuntu install:mad:

also is there any reason not to force mount?

---

### Post by drowner on 2009-04-12
> **kamitsukai said:**
> Is there a way I can make Ubuntu automatically force mount a USB drive if it can't mount it normally? as it's kind of embarrassing faffing around trying to mount a USB pendrive when your showing off you new Ubuntu install:mad:

also is there any reason not to force mount?


We should work out why it won't mount normally first.

It probably wouldn't be a good idea to automatically force a mount - linux is pretty good at working out when something shouldn't be mounted. I had a corrupted hard drive, windows would 'mount' it no worries, linux continually refused to. 

Is it a recurring problem? Is it only one drive? Why won't it mount?

---

### Post by 3rdalbum on 2009-04-12
I don't know how to actually do it, but I believe you could set a udev rule - when udev detects the device ID is attached to the computer, it runs your mount command.

From what I understand it would be a bit of messing about... maybe submit a bug report if your drive isn't automatically mounting?

---

### Post by xir_ on 2009-04-12
what is the particular problem with the mounting. 

There are ways to force mount, but it's not recommended. 

Normally the problem with pen drives i get is that they have not been unmounted properly from a windows system.

i assume your usb is in fat32 but in case you have it in ntfs

[http://ubuntuforums.org/showthread.php?t=673909](http://ubuntuforums.org/showthread.php?t=673909)

---

### Post by kamitsukai on 2009-04-12
it wouldn't mount because it was just pulled out of the pc and not properly removed in windows...

---

### Post by Paqman on 2009-04-12
> **kamitsukai said:**
> it wouldn't mount because it was just pulled out of the pc and not properly removed in windows...

The obvious solution would be to remove the device properly, instead of trying to hack your Ubuntu.

---

### Post by kamitsukai on 2009-04-12
> **Paqman said:**
> The obvious solution would be to remove the device properly, instead of trying to hack your Ubuntu.

well that would be the obvious solution but with no window PC's in the house it is not one available to me;)

what I want is just to mount the damn things, why does it matter if they haven't been removed properly from windows?

---

### Post by drowner on 2009-04-12
> **kamitsukai said:**
> well that would be the obvious solution but with no window PC's in the house it is not one available to me;)

what I want is just to mount the damn things, why does it matter if they haven't been removed properly from windows?

I don't really understand, not being a windows user, but I think windows leaves the drive 'locked' as it were, as though it were still in use.

Its NTFS, yeah?

---

### Post by xir_ on 2009-04-12
I think its to stop two operating systems simultaneously altering the same bits of data on the same drive. 

The drive is saying that its still mounted to windows.

check the link I sent you in my last reply, it might work

---

### Post by kamitsukai on 2009-04-12
> **drowner said:**
> I don't really understand, not being a windows user, but I think windows leaves the drive 'locked' as it were, as though it were still in use.

Its NTFS, yeah?

No it was FAT32

---

### Post by Paqman on 2009-04-12
> **kamitsukai said:**
> 
what I want is just to mount the damn things, why does it matter if they haven't been removed properly from windows?

Because if they haven't been unmounted properly then the data on them might be corrupted. The system is trying to protect you.

---

### Post by kamitsukai on 2009-04-12
> **Paqman said:**
> Because if they haven't been unmounted properly then the data on them might be corrupted. The system is trying to protect you.

so how would the corrupted data harm my pc? surely if the data is already corrupted then there's no problem?

---

### Post by drowner on 2009-04-12
> **kamitsukai said:**
> so how would the corrupted data harm my pc? surely if the data is already corrupted then there's no problem?

No, that's not the point. Reading or writing to a drive with corrupt data can corrupt more data, or cause other problems.

---

### Post by kamitsukai on 2009-04-12
OK so were scrap the idea of auto force mounting but there has to be some kind of app which can solve this? Ubuntu's magical there's always a non windows solution to everything:lolflag:

---

### Post by drowner on 2009-04-12
> **kamitsukai said:**
> OK so were scrap the idea of auto force mounting but there has to be some kind of app which can solve this? Ubuntu's magical there's always a non windows solution to everything:lolflag:

Solve what? I'm not sure what the problem is.

In this case, where you have a USB drive that has been incorrectly unmounted that you want to force mount, you can force mount it as a one-off.

But I don't think that force mounting EVERYTHING is a solution? THe problem is that it wasn't correctly unmounted, not that linux won't mount it, surely?

---

### Post by SuperSonic4 on 2009-04-12
You can force mount at your own risk. First use ```
sudo fdisk -l
``` to find out what your USB pen is recognised as and then use ```
sudo mount -t vfat /dev/sdXX /media/disk -o force
``` but it could lead to data loss

---

### Post by kamitsukai on 2009-04-12
> **drowner said:**
> Solve what? I'm not sure what the problem is.

In this case, where you have a USB drive that has been incorrectly unmounted that you want to force mount, you can force mount it as a one-off.

But I don't think that force mounting EVERYTHING is a solution? THe problem is that it wasn't correctly unmounted, not that linux won't mount it, surely?



I mean an application that could look at the drive assess whether or not any of the data has been corrupted by an incorrect unmounting and if not mount it as usual

---

### Post by xir_ on 2009-04-12
to look at the data it would need to mount the system. Chicken and egg

---

### Post by Paqman on 2009-04-12
You could just force mount it manually, copy the data off, format the drive, then copy your data back. Since it's only a USB stick it should only take a few minutes.

---

### Post by kamitsukai on 2009-04-12
Right...Ok thanks everyone =]

---

